:original_name: en-us_topic_0000001143214829.html

.. _en-us_topic_0000001143214829:

How Do I Configure atop and kdump on Linux ECSs for Performance Analysis?
=========================================================================

Scenarios
---------

This section describes how you can configure atop and kdump on Linux ECSs for performance analysis.

The method for configuring atop varies with the OS version.

atop

-  :ref:`Introduction to atop <en-us_topic_0000001143214829__en-us_topic_0178319250_section0959133015350>`
-  :ref:`Preparing for atop Installation <en-us_topic_0000001143214829__en-us_topic_0178319250_section1829163315414>`
-  :ref:`Configuring atop for CentOS 6 <en-us_topic_0000001143214829__en-us_topic_0178319250_section1972319582310>`
-  :ref:`Configuring atop for CentOS 7/8, AlmaLinux, and Rocky Linux <en-us_topic_0000001143214829__en-us_topic_0178319250_section18897192721320>`
-  :ref:`Configuring atop for Ubuntu 16 and Debian 8 <en-us_topic_0000001143214829__en-us_topic_0178319250_section1919095512712>`
-  :ref:`Configuring atop for Ubuntu 18 and Debian 9 <en-us_topic_0000001143214829__en-us_topic_0178319250_section76781058158>`
-  :ref:`Configuring atop for Ubuntu 20 and Debian 10 <en-us_topic_0000001143214829__en-us_topic_0178319250_section773995710317>`
-  :ref:`Configuring atop for Ubuntu 22 and Ubuntu 24 <en-us_topic_0000001143214829__en-us_topic_0178319250_section203481850122217>`
-  :ref:`Configuring atop for Debian 11 and Debian 12 <en-us_topic_0000001143214829__en-us_topic_0178319250_section59661927152613>`
-  :ref:`Configuring atop for SUSE 12 or SUSE 15 <en-us_topic_0000001143214829__en-us_topic_0178319250_section3205824181917>`
-  :ref:`Installing atop by Compiling the Source Code (for CentOS Stream 8/9, openEuler, or EulerOS) <en-us_topic_0000001143214829__en-us_topic_0178319250_section012793312620>`
-  :ref:`Analyzing atop Logs <en-us_topic_0000001143214829__en-us_topic_0178319250_section478115314146>`

kdump

-  :ref:`Precautions for Configuring kdump <en-us_topic_0000001143214829__en-us_topic_0178319250_section1410131164120>`
-  :ref:`Introduction to kdump <en-us_topic_0000001143214829__en-us_topic_0178319250_section18450171174120>`
-  :ref:`Configuring kdump <en-us_topic_0000001143214829__en-us_topic_0178319250_section134381494320>`
-  :ref:`Checking Whether kdump Configurations Have Taken Effect <en-us_topic_0000001143214829__en-us_topic_0178319250_section1296112934412>`

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section0959133015350:

Introduction to atop
--------------------

atop is a monitor for Linux that can report the activity of all processes and resource consumption by all processes at regular intervals. It shows system-level activity related to the CPU, memory, disks, and network layers for every process. It also logs system and process activities daily and saves the logs in disks for long-term analysis.

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section1829163315414:

Preparing for atop Installation
-------------------------------

An EIP is required and can access YUM.

Constraints
-----------

The atop tool used for node resource monitoring consumes a small number of CPU cores and memory to collect system resources and uses some disk space to record logs. The log path is **/var/log/atop**.

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section1972319582310:

Configuring atop for CentOS 6
-----------------------------

#. Run the following command to install atop:

   **yum install -y atop**

#. Run the following command to modify the configuration file of atop:

   **vi /etc/sysconfig/atop**

   Modify the following parameters, save the modification, and exit:

   Change the value of **LOGINTERVAL** to, for example, **15**. The default value of **LOGINTERVAL** is **600**, in seconds.

   .. code-block::

      LOGINTERVAL=15

   **vi /etc/logrotate.d/atop**

   Modify the following parameters, save the modification, and exit:

   You can change the value of **-mtime** to, for example, **3**. The default retention period of atop logs is **40** days.

   .. code-block::

         postrotate
            /usr/bin/find /var/log/atop/ -maxdepth 1 -mount -name atop_\[0-9\]\[0-9\]\[0-9\]\[0-9\]\[0-9\]\[0-9\]\[0-9\]\[0-9\]\* -mtime +3 -exec /bin/rm {} \;
          endscript

#. Run the following command to start atop:

   **service atop start**

#. Run the following command to check the status of atop. **is running** indicates that atop is running properly.

   **service atop status**

   .. code-block::

      atop (pid 3170) is running

#. Run the following command to stop atop after troubleshooting to release the system and disk resources occupied by atop:

   **service atop stop**

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section18897192721320:

Configuring atop for CentOS 7/8, AlmaLinux, and Rocky Linux
-----------------------------------------------------------

#. Run the following command to install atop:

   **yum install -y atop**

#. Run the following command to modify the configuration file of atop:

   **vi /etc/sysconfig/atop**

   Modify the following parameters, save the modification, and exit:

   -  Change the value of **LOGINTERVAL** to, for example, **15**. The default value of **LOGINTERVAL** is **600**, in seconds.
   -  Change the value of **LOGGENERATIONS** to, for example, **3**. The default retention period of atop logs is **28** days.

   .. code-block::

      LOGINTERVAL=15
      LOGGENERATIONS=3

3. Run the following command to start atop:

   **systemctl enable --now atop atopacct atop-rotate.timer**

4. Check whether atop is started. If **atop atopacct** is **active (running)**, or **atop-rotate.timer** is **active (waiting)**, the service is running properly.

   **systemctl status atop atopacct atop-rotate.timer**

   .. code-block::

      atop.service - Atop advanced performance monitor
      Loaded: loaded (/usr/lib/systemd/system/atop.service; enabled; vendor preset: enabled)
      Active: active (running)

      atopacct.service - Atop process accounting daemon
      Loaded: loaded (/usr/lib/systemd/system/atopacct.service; enabled; vendor preset: enabled)
      Active: active (running)

      atop-rotate.timer - Daily atop restart
      Loaded: loaded (/usr/lib/systemd/system/atop-rotate.timer; enabled; vendor preset: enabled)
      Active: active (waiting)

5. Run the following command to stop atop after troubleshooting to release the system and disk resources occupied by atop:

   **systemctl disable atop atopacct atop-rotate.timer**

   **systemctl stop atop atopacct atop-rotate.timer**

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section1919095512712:

Configuring atop for Ubuntu 16 and Debian 8
-------------------------------------------

#. Run the following command to install atop:

   **apt-get install -y atop**

#. Run the following command to modify the configuration file of atop:

   **vi /etc/default/atop**

   Modify the following parameters, save the modification, and exit:

   -  Change the value of **LOGINTERVAL** to, for example, **15**. The default value of **LOGINTERVAL** is **600**, in seconds.
   -  The default retention period of atop logs is **28** days and cannot be modified.

   .. code-block::

      LOGINTERVAL=15

3. Run the following command to start atop:

   **systemctl start atop**

4. Run the following command to check the status of atop. **active (running)** indicates that atop is running properly.

   **systemctl status atop**

   .. code-block::

      atop.service - Atop advanced performance monitor
      Loaded: loaded (/etc/init.d/atop; bad; vendor preset: disabled)
      Active: active (running)

5. Run the following command to stop atop after troubleshooting to release the system and disk resources occupied by atop:

   **systemctl stop atop**

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section76781058158:

Configuring atop for Ubuntu 18 and Debian 9
-------------------------------------------

#. Run the following command to install atop:

   **apt-get install -y atop**

#. Run the following command to modify the configuration file of atop:

   **vi /usr/share/atop/atop.daily**

   Modify the following parameters, save the modification, and exit:

   -  Change the value of **LOGINTERVAL** to, for example, **15**. The default value of **LOGINTERVAL** is **600**, in seconds.
   -  You can change the value of **-mtime** to, for example, **3**. The default retention period of atop logs is **28** days.

   .. code-block::

      LOGINTERVAL=15
      ……
      ( (sleep 3; find $LOGPATH -name 'atop_*' -mtime +3 -exec rm {} \;)& )

3. Restart the atop service (started by default) to apply the configuration:

   **systemctl restart atop atopacct**

4. Run the following command to check the status of atop. **active (running)** indicates that atop is running properly.

   **systemctl status atop atopacct**

   .. code-block::

      atop.service - Atop advanced performance monitor
      Loaded: loaded (/etc/init.d/atop; enable; vendor preset: enabled)
      Active: active (running)

      atopacct.service - Atop process accounting daemon
      Loaded: loaded (/usr/lib/systemd/system/atopacct.service; enabled; vendor preset: enabled)
      Active: active (running)

5. Run the following command to stop atop after troubleshooting to release the system and disk resources occupied by atop:

   **systemctl disable atop atopacct**

   **systemctl stop atop atopacct**

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section773995710317:

Configuring atop for Ubuntu 20 and Debian 10
--------------------------------------------

#. Run the following command to install atop:

   **apt-get install -y atop**

#. Run the following command to modify the configuration file of atop:

   **vi /etc/default/atop**

   Modify the following parameters, save the modification, and exit:

   -  Change the value of **LOGINTERVAL** to, for example, **15**. The default value of **LOGINTERVAL** is **600**, in seconds.
   -  Change the value of **LOGGENERATIONS** to, for example, **3**. The default retention period of atop logs is **28** days.

   .. code-block::

      LOGINTERVAL=15
      LOGGENERATIONS=3

3. Restart the atop service (started by default) to apply the configuration:

   **systemctl restart atop atopacct**

4. Run the following command to check the status of atop. **active (running)** indicates that atop is running properly.

   **systemctl status atop atopacct**

   .. code-block::

      atop.service - Atop advanced performance monitor
      Loaded: loaded (/etc/init.d/atop; enable; vendor preset: enabled)
      Active: active (running)

      atopacct.service - Atop process accounting daemon
      Loaded: loaded (/usr/lib/systemd/system/atopacct.service; enabled; vendor preset: enabled)
      Active: active (running)

5. Run the following command to stop atop after troubleshooting to release the system and disk resources occupied by atop:

   **systemctl disable atop atopacct**

   **systemctl stop atop atopacct**

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section203481850122217:

Configuring atop for Ubuntu 22 and Ubuntu 24
--------------------------------------------

#. Run the following command to install atop:

   **apt-get install -y atop**

#. Run the following command to modify the configuration file of atop:

   **vi /etc/default/atop**

   Modify the following parameters, save the modification, and exit:

   -  Change the value of **LOGINTERVAL** to, for example, **15**. The default value of **LOGINTERVAL** is **600**, in seconds.
   -  Change the value of **LOGGENERATIONS** to, for example, **3**. The default retention period of atop logs is **28** days.

   .. code-block::

      LOGINTERVAL=15
      LOGGENERATIONS=3

#. Restart the atop service (started by default) to apply the configuration:

   **systemctl restart atop atopacct atop-rotate.timer**

#. Check whether atop is started. If **atop atopacct** is **active (running)**, or **atop-rotate.timer** is **active (waiting)**, the service is running properly.

   **systemctl status atop atopacct atop-rotate.timer**

   .. code-block::

      atop.service - Atop advanced performance monitor
      Loaded: loaded (/usr/lib/systemd/system/atop.service; enabled; vendor preset: enabled)
      Active: active (running)

      atopacct.service - Atop process accounting daemon
      Loaded: loaded (/usr/lib/systemd/system/atopacct.service; enabled; vendor preset: enabled)
      Active: active (running)

      atop-rotate.timer - Daily atop restart
      Loaded: loaded (/usr/lib/systemd/system/atop-rotate.timer; enabled; vendor preset: enabled)
      Active: active (waiting)

#. Run the following command to stop atop after troubleshooting to release the system and disk resources occupied by atop:

   **systemctl disable atop atopacct atop-rotate.timer**

   **systemctl stop atop atopacct atop-rotate.timer**

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section59661927152613:

Configuring atop for Debian 11 and Debian 12
--------------------------------------------

#. Run the following command to install atop:

   **apt-get install -y atop**

#. Run the following command to modify the configuration file of atop:

   **vi /etc/default/atop**

   Modify the following parameters, save the modification, and exit:

   -  Change the value of **LOGINTERVAL** to, for example, **15**. The default value of **LOGINTERVAL** is **600**, in seconds.
   -  Change the value of **LOGGENERATIONS** to, for example, **3**. The default retention period of atop logs is **28** days.

   .. code-block::

      LOGINTERVAL=15
      LOGGENERATIONS=3

#. Restart the atop service (started by default) to apply the configuration:

   **systemctl restart atop atopacct atop-rotate.timer**

#. Check whether atop is started. If **atop atopacct** is **active (running)**, or **atop-rotate.timer** is **active (waiting)**, the service is running properly.

   **systemctl status atop atopacct atop-rotate.timer**

   .. code-block::

      atop.service - Atop advanced performance monitor
      Loaded: loaded (/usr/lib/systemd/system/atop.service; enabled; vendor preset: enabled)
      Active: active (running)

      atopacct.service - Atop process accounting daemon
      Loaded: loaded (/usr/lib/systemd/system/atopacct.service; enabled; vendor preset: enabled)
      Active: active (running)

      atop-rotate.timer - Daily atop restart
      Loaded: loaded (/usr/lib/systemd/system/atop-rotate.timer; enabled; vendor preset: enabled)
      Active: active (waiting)

#. Run the following command to stop atop after troubleshooting to release the system and disk resources occupied by atop:

   **systemctl disable atop atopacct atop-rotate.timer**

   **systemctl stop atop atopacct atop-rotate.timer**

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section3205824181917:

Configuring atop for SUSE 12 or SUSE 15
---------------------------------------

#. Run the following command to download the atop source package:

   **wget https://www.atoptool.nl/download/atop-2.6.0-1.src.rpm**

#. Run the following command to install the atop source package:

   **rpm -ivh atop-2.6.0-1.src.rpm**

#. Run the following command to install atop dependencies.

   **zypper -n install rpm-build ncurses-devel zlib-devel**

#. Run the following commands to compile atop:

   **cd /usr/src/packages/SPECS**

   **rpmbuild -bb atop-2.6.0.spec**

#. Run the following commands to install atop:

   **cd /usr/src/packages/RPMS/x86_64**

   **rpm -ivh atop-2.6.0-1.x86_64.rpm**

#. Run the following command to modify the configuration file of atop:

   **vi /etc/default/atop**

   Modify the following parameters, save the modification, and exit:

   -  Change the value of **LOGINTERVAL** to, for example, **15**. The default value of **LOGINTERVAL** is **600**, in seconds.
   -  Change the value of **LOGGENERATIONS** to, for example, **3**. The default retention period of atop logs is **28** days.

   .. code-block::

      LOGINTERVAL=15
      LOGGENERATIONS=3

7. Restart the atop service (started by default) to apply the configuration:

   **systemctl restart atop atopacct atop-rotate.timer**

8. Check whether atop is started. If **atop atopacct** is **active (running)**, or **atop-rotate.timer** is **active (waiting)**, the service is running properly.

   **systemctl status atop atopacct atop-rotate.timer**

   .. code-block::

      atop.service - Atop advanced performance monitor
      Loaded: loaded (/usr/lib/systemd/system/atop.service; enabled; vendor preset: enabled)
      Active: active (running)

      atopacct.service - Atop process accounting daemon
      Loaded: loaded (/usr/lib/systemd/system/atopacct.service; enabled; vendor preset: enabled)
      Active: active (running)

      atop-rotate.timer - Daily atop restart
      Loaded: loaded (/usr/lib/systemd/system/atop-rotate.timer; enabled; vendor preset: enabled)
      Active: active (waiting)

9. Run the following command to stop atop after troubleshooting to release the system and disk resources occupied by atop:

   **systemctl disable atop atopacct atop-rotate.timer**

   **systemctl stop atop atopacct atop-rotate.timer**

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section012793312620:

Installing atop by Compiling the Source Code (for CentOS Stream 8/9, openEuler, or EulerOS)
-------------------------------------------------------------------------------------------

#. Download the atop source package.

   **wget https://www.atoptool.nl/download/atop-2.6.0.tar.gz**

2. Decompress the atop source package.

   **tar -zxvf atop-2.6.0.tar.gz**

3. Query the systemctl version.

   **systemctl --version**

   If the version is 220 or later, go to the next step.

   Otherwise, delete parameter **--now** from the Makefile of atop.

   **vi atop-2.6.0/Makefile**

   Delete parameter **--now** following the **systemctl** command.

   .. code-block::

                      then   /bin/systemctl disable  atop     2> /dev/null; \
                              /bin/systemctl disable  atopacct 2> /dev/null; \
                              /bin/systemctl daemon-reload;                   \
                              /bin/systemctl enable   atopacct;          \
                              /bin/systemctl enable   atop;              \
                              /bin/systemctl enable   atop-rotate.timer; \

4. Install atop dependencies.

   -  Installing command for SUSE 12 or SUSE 15

      **zypper -n install make gcc zlib-devel ncurses-devel**

   -  Installing command for EulerOS or Fedora

      **yum install make gcc zlib-devel ncurses-devel -y**

   -  Installing command for Debian 9, Debian 10, or Ubuntu

      **apt install make gcc zlib1g-dev libncurses5-dev libncursesw5-dev -y**

5. Compile and install atop.

   **cd atop-2.6.0**

   **make systemdinstall**

6. Run the following command to modify the configuration file of atop:

   **vi /etc/default/atop**

   Modify the following parameters, save the modification, and exit:

   -  Change the value of **LOGINTERVAL** to, for example, **15**. The default value of **LOGINTERVAL** is **600**, in seconds.
   -  Change the value of **LOGGENERATIONS** to, for example, **3**. The default retention period of atop logs is **28** days.

   .. code-block::

      LOGOPTS=""
      LOGINTERVAL=15
      LOGGENERATIONS=3
      LOGPATH=/var/log/atop

7. Restart the atop service (started by default) to apply the configuration:

   **systemctl restart atop atopacct atop-rotate.timer**

8. Check whether atop is started. If **atop atopacct** is **active (running)**, or **atop-rotate.timer** is **active (waiting)**, the service is running properly.

   **systemctl status atop atopacct atop-rotate.timer**

   .. code-block::

      atop.service - Atop advanced performance monitor
      Loaded: loaded (/usr/lib/systemd/system/atop.service; enabled; vendor preset: enabled)
      Active: active (running)

      atopacct.service - Atop process accounting daemon
      Loaded: loaded (/usr/lib/systemd/system/atopacct.service; enabled; vendor preset: enabled)
      Active: active (running)

      atop-rotate.timer - Daily atop restart
      Loaded: loaded (/usr/lib/systemd/system/atop-rotate.timer; enabled; vendor preset: enabled)
      Active: active (waiting)

9. Run the following command to stop atop after troubleshooting to release the system and disk resources occupied by atop:

   **systemctl disable atop atopacct atop-rotate.timer**

   **systemctl stop atop atopacct atop-rotate.timer**

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section478115314146:

Analyzing atop Logs
-------------------

After startup, atop stores collection records in **/var/log/atop**.

Run the following command to check the log file:

**atop -r /var/log/atop/atop_2024XXXX**

-  **Common atop commands**

   After opening the log file, you can use the following commands to sort data:

   -  **c**: used to sort processes by CPU usage in descending order.
   -  **m**: used to sort processes by memory usage in descending order.
   -  **d**: used to sort processes by disk usage in descending order.
   -  **a**: used to sort processes by the overall resource usage in descending order.
   -  **n**: used to sort processes by network usage in descending order.
   -  **t**: used to go to the next monitoring collection point.
   -  **T**: used to go to the previous monitoring collection point.
   -  **b**: used to specify a time point in the format of YYYYMMDDhhmm.

-  **System resource monitoring fields**

   The following figure shows some monitoring fields and values. The values vary according to the sampling period and atop version. The figure is for reference only.


   .. figure:: /_static/images/en-us_image_0000001914323145.png
      :alt: **Figure 1** System resource monitoring fields

      **Figure 1** System resource monitoring fields

   Description of major fields is as follows:

   -  **ATOP** row: Specifies the host name and information sampling date and time.
   -  **PRC** row: Specifies the running status of a process.
   -  **#sys** and **user**: Specifies how long the CPU is occupied when the system is running in kernel mode and user mode.
   -  **#proc**: Specifies the total number of processes.
   -  **#zombie**: Specifies the number of zombie processes.
   -  **#exit**: Specifies the number of processes that exited during the sampling period.
   -  **CPU** row: Specifies the overall CPU usage (multi-core CPU as a whole CPU). The sum of the values in the CPU row is N x 100%. **N** indicates the number of vCPUs.
   -  **#sys** and **user**: Specifies the percentage of how long the CPU is occupied when the system is running in kernel mode and user mode.
   -  **#irq**: Specifies the percentage of time when CPU is servicing interrupts.
   -  **#idle**: Specifies the percentage of time when CPU is idle.
   -  **#wait**: Specifies the percentage of time when CPU is idle due to I/O wait.
   -  **CPL** row: Specifies CPU load.
   -  **#avg1**, **avg5** and **avg15**: Specifies the average number of running processes in the past 1, 5, and 15 minutes, respectively.
   -  **#csw**: Specifies the number of context exchanges.
   -  **#intr**: Specifies the number of interruptions.
   -  **MEM** row: Specifies the memory usage.
   -  **#tot**: Specifies the physical memory size.
   -  **#free**: Specifies the size of available physical memory.
   -  **#cache**: Specifies the memory size used for page cache.
   -  **#buff**: Specifies the memory size used for file cache.
   -  **#slab**: Specifies the memory size occupied by the system kernel.
   -  **SWP** row: Specifies the usage of swap space.
   -  **#tot**: Specifies the total swap space.
   -  **#free**: Specifies the size of available swap space.
   -  **DSK** row: Specifies the disk usage. Each disk device corresponds to a column. If there is an **sdb** device, a **DSK** row should be added.
   -  **#sda**: Specifies the disk device identifier.
   -  **#busy**: Specifies the percentage of time when the disk is busy.
   -  **#read** and **write**: Specifies the number of read and write requests.
   -  **NET** row: Displays the network status, covering the transport layer (TCP and UDP), IP layer, and active network ports.
   -  **#xxxxxi**: Specifies the number of packets received by each layer or active network port.
   -  **#xxxxxo**: Specifies the number of packets sent by each layer or active network port.

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section1410131164120:

Precautions for Configuring kdump
---------------------------------

The method for configuring kdump described in this section applies to KVM ECSs running EulerOS or CentOS 7.\ *x*. For details, see `Documentation for kdump <https://www.kernel.org/doc/Documentation/kdump/kdump.txt>`__.

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section18450171174120:

Introduction to kdump
---------------------

Kdump is a tool used to dump runtime memory when the system crashes. Once the system crashes, the kernel can no longer function properly. At this point, Kdump boots another kernel to capture and save a memory dump. This kernel collects all runtime states and data and stores them in a dump core file for troubleshooting and debugging.

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section134381494320:

Configuring kdump
-----------------

#. Run the following command to check whether kexec-tools is installed:

   **rpm -q kexec-tools**

   If it is not installed, run the following command to install it:

   **yum install -y kexec-tools**

#. Run the following command to enable kdump to run at system startup:

   **systemctl enable kdump**

#. Configure the **crashkernel** parameter to reserve the memory for the capture kernel.

   Run the following command to check whether the parameter has been configured:

   **grep crashkernel /proc/cmdline**

   If the command output is displayed, this parameter has been configured. If no command output is displayed, you need to configure **crashkernel**.

   Edit the **/etc/default/grub** file to configure **crashkernel** as follows:

   .. code-block::

      GRUB_TIMEOUT=5
      GRUB_DEFAULT=saved
      GRUB_DISABLE_SUBMENU=true
      GRUB_TERMINAL_OUTPUT="console"
      GRUB_CMDLINE_LINUX="crashkernel=auto rd.lvm.lv=rhel00/root rd.lvm.lv=rhel00/swap
      rhgb quiet"
      GRUB_DISABLE_RECOVERY="true"

   Locate parameter **GRUB_CMDLINE_LINUX** and add **crashkernel=auto** after it.

#. Run the following command for the configuration to take effect:

   **grub2-mkconfig -o /boot/grub2/grub.cfg**

#. Open the **/etc/kdump.conf** file, locate parameter **path**, and add **/var/crash** after it.

   .. code-block::

      path  /var/crash

   By default, the file is saved in the **/var/crash** directory.

   You can save the file to another directory, for example, **/home/kdump**. Then add **/home/kdump** after parameter **path**:

   .. code-block::

      path  /home/kdump

   .. note::

      There must be enough space in the specified path for storing the vmcore file. It is recommended that the available space be greater than or equal to the RAM size. You can also store the vmcore file on a shared device such as SAN or NFS.

#. Set the vmcore dump level.

   Add the following content to file **/etc/kdump.conf**. If the content already exists, skip this step.

   .. code-block::

      core_collector makedumpfile -d 31 -c

   In the preceding command:

   **-c** indicates compressing the vmcore file.

   **-d** indicates leaving out irrelevant data. Generally, the value following **-d** is **31**, which is calculated based on the following values. You can adjust the value if needed.

   .. code-block::

      zero pages   = 1
      cache pages   = 2
      cache private = 4
      user  pages   = 8
      free  pages   = 16

#. Run the following command to restart the system for the configurations to take effect:

   **reboot**

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section1296112934412:

Checking Whether kdump Configurations Have Taken Effect
-------------------------------------------------------

#. Run the following command and check whether **crashkernel=auto** is displayed:

   **cat /proc/cmdline \|grep crashkernel**

   .. code-block::

      BOOT_IMAGE=/boot/vmlinuz-3.10.0-514.44.5.10.h142.x86_64 root=UUID=6407d6ac-c761-43cc-a9dd-1383de3fc995 ro crash_kexec_post_notifiers softlockup_panic=1 panic=3 reserve_kbox_mem=16M nmi_watchdog=1 rd.shell=0 fsck.mode=auto fsck.repair=yes net.ifnames=0 spectre_v2=off nopti noibrs noibpb crashkernel=auto LANG=en_US.UTF-8

#. Run the following command and check whether the information in the output is correct:

   **grep core_collector /etc/kdump.conf \|grep -v ^"#"**

   .. code-block::

      core_collector makedumpfile -l --message-level 1 -d 31

#. Run the following command and check whether the information in the output is correct:

   **grep path /etc/kdump.conf \|grep -v ^"#"**

   .. code-block::

      path /var/crash

#. Run the following command and check whether the value of **Active** in the output is **active (exited)**:

   **systemctl status kdump**

   .. code-block::

      ● kdump.service - Crash recovery kernel arming
      Loaded: loaded (/usr/lib/systemd/system/kdump.service; enabled; vendor preset: enabled)
      Active: active (exited) since Tue 2019-04-09 19:30:24 CST; 8min ago
      Process: 495 ExecStart=/usr/bin/kdumpctl start (code=exited, status=0/SUCCESS)
      Main PID: 495 (code=exited, status=0/SUCCESS)
      CGroup: /system.slice/system-hostos.slice/kdump.service

#. Run the following test command:

   **echo c > /proc/sysrq-trigger**

   This command will trigger kdump. When triggered, kdump will boot another kernel and store the generated **vmcore** file to the location specified by **path**.

#. Run the following command to check whether the **vmcore** file has been generated in the specified path, for example, **/var/crash/**:

   **ll /var/crash/**
