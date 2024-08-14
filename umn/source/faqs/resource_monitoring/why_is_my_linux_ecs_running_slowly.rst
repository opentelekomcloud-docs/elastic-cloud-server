:original_name: en-us_topic_0167429329.html

.. _en-us_topic_0167429329:

Why Is My Linux ECS Running Slowly?
===================================

If your ECS runs slowly or is inaccessible unexpectedly, the bandwidth or vCPU usage of the ECS may be excessively high. If you have created an alarm rule using Cloud Eye, the system automatically sends an alarm to you when the bandwidth or CPU usage reaches the threshold specified in the rule.

To handle this issue, perform the following operations:

#. Fault locating

   Identify the processes leading to high bandwidth or CPU usage.

2. Check whether the processes are normal and handle the issue accordingly.

   -  If the processes are normal, optimize them or modify ECS specifications.
   -  If the processes are malicious, use a third-party tool to automatically stop the processes or manually stop them.

Common Commands
---------------

The following uses the CentOS 7.2 64bit OS as an example to describe common commands. The commands may vary depending on Linux OS editions. For details, see the official documentation for the specific OS edition.

The common commands for checking Linux ECS performance metrics, such as the CPU usage, are as follows:

-  **ps -aux**
-  **ps -ef**
-  **top**

Locating High CPU Usage
-----------------------

#. Log in to the ECS using VNC.

#. Run the following command to check the OS running status:

   **top**

   Information similar to the following is displayed.

   |image1|

#. View the command output.

   -  The first line in the command output is "20:56:02 up 37 days, 1 user, load average: 0.00, 0.01, 0.05", indicating that:

      The current system time is 20:56:02; the ECS has been running for 37 days; there is one login user; the last three values indicate the average CPU load in the last 1 minute, 5 minutes, and 15 minutes, respectively.

   -  The third line in the command output shows the overall CPU usage.

   -  The fourth line in the command output shows the overall memory usage.

   -  The lower part of the command output shows the resource usage of each process.

      .. note::

         a. On the **top** page, enter **q** or press **Ctrl+C** to exit.

         b. Alternatively, click **Input Command** in the upper right corner of the VNC login page, paste or enter commands in the displayed dialog box, and click **Send**.

         c. Common parameters in top commands are as follows:

            **s**: Change the image update frequency.

            **l**: Show or hide the first line for the top information.

            **t**: Show or hide the second line for tasks and the third line for CPUs.

            **m**: Show or hide the fourth line for Mem and the fifth line for Swap.

            **N**: Sort processes by PID in ascending or descending order.

            **P**: Sort processes by CPU usage in ascending or descending order.

            **M**: Sort processes by memory usage in ascending or descending order.

            **h**: Show help for commands.

            **n**: Set the number of processes displayed in the process list.

#. Run the **ll /proc/**\ *PID*\ **/exe** command to obtain the program file specified by a PID.

   |image2|

Troubleshooting High CPU Usage
------------------------------

If the processes leading to high CPU usage are malicious, run the top command to stop them. If the **kswapd0** process leads to high CPU usage, optimize the program for the process or upgrade the ECS specifications for a larger memory capacity.

**kswapd0** is a virtual memory management process. When the physical memory becomes insufficient, **kswapd0** runs to allocate disk swap capacity for caching. This uses a large number of CPU resources.

-  For the detected malicious processes

   Quickly stop such processes on the top page. To do so, perform the following operations:

   #. Press the **k** key during the execution of the top command.

   #. Enter the PID of the process to be stopped.

      The PID of the process is the value in the first column of the top command output. For example, to stop the process with PID 52, enter **52** and press **Enter**.

      |image3|

   #. After the operation is successful, information similar to the following is displayed. Press **Enter**.

      |image4|

-  For the **kswapd0** process

   To check the memory usage of a process, perform the following operations:

   #. Run the top command to check the resource usage of the **kswapd0** process.

   #. If the process remains in non-sleeping state for a long period of time, you can preliminarily determine that the system is consistently paging. In such a case, the high CPU usage is caused by insufficient memory.

      |image5|

   #. Run the **vmstat** command to check the virtual memory usage of the system.

      If the **si** and **so** values are large, the system is frequently paging and the physical memory of the system is insufficient.

      -  **si**: Volume of data written from the swap partition to the memory per second, which is transferred from the disk to the memory.
      -  **so**: Volume of data written from the memory to the swap partition per second, which is transferred from the memory to the disk.

   #. Further identify the causes of high memory usage. Run commands, such as **free** and **ps** to check the memory usage of the system and processes in the system.

   #. Restart the application or release the memory when traffic is light.

      To handle this issue, expand the ECS memory. If memory expansion is not allowed, optimize the application and enable hugepage memory.

Handling High Bandwidth Usage
-----------------------------

If the high bandwidth usage is caused by normal service access of non-malicious processes, enlarge the bandwidth to handle this issue. If the high bandwidth usage is caused by abnormal service access, for example, malicious access from certain IP addresses, CC attacks on the ECS, or malicious processes, use the traffic monitoring tool **nethogs** to monitor the bandwidth usage of each process in real time and identify faulty processes.

-  Using **nethogs** for troubleshooting

   #. Run the following command to install **nethogs**:

      **yum install nethogs -y**

      After the installation, run the **netgos** command to check bandwidth usage.

      Parameters in the **nethogs** command are as follows:

      -  **-d**: Set the update interval in the unit of second. The default value is **1**.
      -  **-t**: Enable tracing.
      -  **-c**: Set the number of updates.
      -  **device**: Set the NIC to be monitored. The default value is **eth0**.

      The following parameters are involved in command execution:

      -  **q**: Exit **nethogs**.
      -  **s**: Sort processes in the process list by TX traffic in ascending or descending order.
      -  **r**: Sort processes in the process list by RX traffic in ascending or descending order.
      -  **m**: Switch the display unit in the sequence of KB/s, KB, B, and MB.

   #. Run the following command to check the bandwidth usage of each process on the specified NIC:

      **nethogs** **eth1**

      |image6|

      The parameters in the command output are as follows:

      -  **PID**: ID of the process.
      -  **USER**: user who runs the process.
      -  **PROGRAM**: IP addresses and port numbers of the process and connection, respectively. The former is for the server and the latter is for the client.
      -  **DEV**: Network port to which the traffic is destined.
      -  **SENT**: Volume of data sent by the process per second.
      -  **RECEIVED**: Volume of data received by the process per second.

   #. Stop malicious programs or blacklist malicious IP addresses.

      To stop a malicious process, run the **kill** *PID* command.

      To blacklist a malicious IP address or limit its rate, use iptables.

.. |image1| image:: /_static/images/en-us_image_0166736726.png
.. |image2| image:: /_static/images/en-us_image_0166945975.png
.. |image3| image:: /_static/images/en-us_image_0166947771.png
.. |image4| image:: /_static/images/en-us_image_0166947775.png
.. |image5| image:: /_static/images/en-us_image_0167110971.png
.. |image6| image:: /_static/images/en-us_image_0167295759.png
