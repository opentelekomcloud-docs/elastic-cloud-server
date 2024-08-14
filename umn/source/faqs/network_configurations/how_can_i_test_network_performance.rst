:original_name: en-us_topic_0115820205.html

.. _en-us_topic_0115820205:

How Can I Test Network Performance?
===================================

Use netperf and iperf3 to test network performance between ECSs. The test operations include preparations, TCP bandwidth test, UDP PPS test, and latency test.

Background
----------

-  Tested ECS: an ECS that is tested for network performance. Such an ECS functions as the client (TX end) or server (RX end) in netperf tests.

-  Auxiliary ECS: an ECS that is used to exchange test data with the tested ECS. The auxiliary ECS functions as the client (TX end) or server (RX end) in netperf tests.

-  :ref:`Table 1 <en-us_topic_0115820205__table15359114885218>` and :ref:`Table 2 <en-us_topic_0115820205__table8470126153613>` list the common netperf and iperf3 parameters.

   .. _en-us_topic_0115820205__table15359114885218:

   .. table:: **Table 1** Common netperf parameters

      +-----------+-----------------------------------------------------------------------------------------------+
      | Parameter | Description                                                                                   |
      +===========+===============================================================================================+
      | -p        | Port number                                                                                   |
      +-----------+-----------------------------------------------------------------------------------------------+
      | -H        | IP address of the RX end                                                                      |
      +-----------+-----------------------------------------------------------------------------------------------+
      | -t        | Protocol used in packet transmitting, the value of which is **TCP_STREAM** in bandwidth tests |
      +-----------+-----------------------------------------------------------------------------------------------+
      | -l        | Test duration                                                                                 |
      +-----------+-----------------------------------------------------------------------------------------------+
      | -m        | Data packet size, which is suggested to be **1440** in bandwidth tests                        |
      +-----------+-----------------------------------------------------------------------------------------------+

   .. _en-us_topic_0115820205__table8470126153613:

   .. table:: **Table 2** Common iperf3 parameters

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                     |
      +===================================+=================================================================================================================================================+
      | -p                                | Port number                                                                                                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | -c                                | IP address of the RX end                                                                                                                        |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | -u                                | UDP packets                                                                                                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | -b                                | TX bandwidth                                                                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | -t                                | Test duration                                                                                                                                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | -l                                | Data packet size, which is suggested to be **16** in PPS tests                                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | -A                                | ID of the vCPU used by iperf3                                                                                                                   |
      |                                   |                                                                                                                                                 |
      |                                   | In this section, the maximum number of 16 vCPUs is used as an example for each ECS. If an ECS has 8 vCPUs, the **-A** value ranges from 0 to 7. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

Test Preparations
-----------------

#. Prepare ECSs.

   Ensure that both type and specifications of the tested ECS and auxiliary ECSs are the same. In addition, ensure that these ECSs are deployed in the same ECS group with anti-affinity enabled.

   .. table:: **Table 3** Preparations

      +---------------+----------+--------------------------------+----------------------+---------------------------+
      | Category      | Quantity | Image                          | Specifications       | IP Address                |
      +===============+==========+================================+======================+===========================+
      | Tested ECS    | 1        | CentOS 7.4 64bit (recommended) | At least eight vCPUs | 192.168.2.10              |
      +---------------+----------+--------------------------------+----------------------+---------------------------+
      | Auxiliary ECS | 8        | CentOS 7.4 64bit (recommended) | At least 8 vCPUs     | 192.168.2.11-192.168.2.18 |
      +---------------+----------+--------------------------------+----------------------+---------------------------+

#. Install the netperf, iperf3, and sar test tools on both the tested ECS and auxiliary ECSs.

   :ref:`Table 4 <en-us_topic_0115820205__table231811914413>` lists the procedures for installing these tools.

   .. _en-us_topic_0115820205__table231811914413:

   .. table:: **Table 4** Installing test tools

      +-----------------------------------+-----------------------------------------------------------------------------------------------------+
      | Tool                              | Procedure                                                                                           |
      +===================================+=====================================================================================================+
      | netperf                           | a. Run the following command to install gcc:                                                        |
      |                                   |                                                                                                     |
      |                                   |    **yum -y install unzip gcc gcc-c++**                                                             |
      |                                   |                                                                                                     |
      |                                   | b. Run the following command to download the netperf installation package:                          |
      |                                   |                                                                                                     |
      |                                   |    **wget** **https://github.com/HewlettPackard/netperf/archive/refs/tags/netperf-2.7.0.zip**       |
      |                                   |                                                                                                     |
      |                                   | c. Run the following commands to decompress the installation package and install netperf:           |
      |                                   |                                                                                                     |
      |                                   |    **unzip netperf-2.7.0.zip**                                                                      |
      |                                   |                                                                                                     |
      |                                   |    **cd netperf-netperf-2.7.0/**                                                                    |
      |                                   |                                                                                                     |
      |                                   |    **./configure && make && make install**                                                          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------+
      | iperf3                            | a. Run the following command to download the iperf3 installation package:                           |
      |                                   |                                                                                                     |
      |                                   |    **wget --no-check-certificate https://codeload.github.com/esnet/iperf/zip/master -O iperf3.zip** |
      |                                   |                                                                                                     |
      |                                   | b. Run the following commands to decompress the installation package and install iperf3:            |
      |                                   |                                                                                                     |
      |                                   |    **unzip iperf3.zip**                                                                             |
      |                                   |                                                                                                     |
      |                                   |    **cd iperf-master/**                                                                             |
      |                                   |                                                                                                     |
      |                                   |    **./configure && make && make install**                                                          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------+
      | sar                               | Run the following command to install sar:                                                           |
      |                                   |                                                                                                     |
      |                                   | **yum -y install sysstat**                                                                          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------+

#. Enable NIC multi-queue.

   Perform the following operations on both tested ECS and auxiliary ECSs.

   a. .. _en-us_topic_0115820205__li162918018139:

      Run the following command to check the number of queues supported by the ECSs:

      **ethtool -l eth0 \| grep -i Pre -A 5 \| grep Combined**

   b. Run the following command to enable NIC multi-queue:

      **ethtool -L eth0 combined** *X*

      In the preceding command, *X* is the number of queues obtained in :ref:`3.a <en-us_topic_0115820205__li162918018139>`.

TCP Bandwidth Test (Using netperf)
----------------------------------

Perform the test on multiple flows. This section considers 16 flows that are evenly distributed to eight ECSs, as an example.

.. note::

   The TCP bandwidth test uses the multi-flow model.

   -  When testing the TCP transmission (TX) bandwidth, use the one-to-many model to ensure that the capability of the receiver is sufficient.
   -  When testing the TCP receiver (RX) bandwidth, use the many-to-one model to ensure that the capability of the sender is sufficient.

#. Test the TCP TX bandwidth.

   a. Run the following commands on all auxiliary ECSs to start the netserver process:

      **netserver -p** *12001*

      **netserver -p** *12002*

      In the preceding commands, **-p** specifies the listening port.

   b. Start the netperf process on the tested ECS and specify a netserver port for each auxiliary ECS. For details about common netperf parameters, see :ref:`Table 1 <en-us_topic_0115820205__table15359114885218>`.

      ##The IP address is for the first auxiliary ECS.

      **netperf -H** **192.168.2.11** **-p** **12001 -t TCP_STREAM -l** **300 -- -m** **1440 &**

      **netperf -H** **192.168.2.11** **-p** **12002 -t TCP_STREAM -l** **300 -- -m** **1440 &**

      ##The IP address is for the second auxiliary ECS.

      **netperf -H** **192.168.2.12** **-p** **12001 -t TCP_STREAM -l** **300 -- -m** **1440 &**

      **netperf -H** **192.168.2.12** **-p** **12002 -t TCP_STREAM -l** **300 -- -m** **1440 &**

      ##The IP address is for the third auxiliary ECS.

      **netperf -H** **192.168.2.13 -p** **12001 -t TCP_STREAM -l** **300 -- -m** **1440 &**

      **netperf -H** **192.168.2.13 -p** **12002 -t TCP_STREAM -l** **300 -- -m** **1440 &**

      ##The IP address is for the fourth auxiliary ECS.

      **netperf -H** **192.168.2.14 -p** **12001 -t TCP_STREAM -l** **300 -- -m** **1440 &**

      **netperf -H** **192.168.2.14 -p** **12002 -t TCP_STREAM -l** **300 -- -m** **1440 &**

      ##The IP address is for the fifth auxiliary ECS.

      **netperf -H** **192.168.2.15 -p** **12001 -t TCP_STREAM -l** **300 -- -m** **1440 &**

      **netperf -H** **192.168.2.15 -p** **12002 -t TCP_STREAM -l** **300 -- -m** **1440 &**

      ##The IP address is for the sixth auxiliary ECS.

      **netperf -H** **192.168.2.16 -p** **12001 -t TCP_STREAM -l 300 -- -m** **1440 &**

      **netperf -H** **192.168.2.16 -p** **12002 -t TCP_STREAM -l 300 -- -m** **1440 &**

      ##The IP address is for the seventh auxiliary ECS.

      **netperf -H** **192.168.2.17 -p** **12001 -t TCP_STREAM -l** **300 -- -m** **1440 &**

      **netperf -H** **192.168.2.17 -p** **12002 -t TCP_STREAM -l** **300 -- -m** **1440 &**

      ##The IP address is for the eighth auxiliary ECS.

      **netperf -H** **192.168.2.18 -p** **12001 -t TCP_STREAM -l** **300 -- -m** **1440 &**

      **netperf -H** **192.168.2.18 -p** **12002 -t TCP_STREAM -l** **300 -- -m** **1440 &**

#. Test the TCP RX bandwidth.

   a. Start the netserver process on the tested ECS.

      ##The port number is for the first auxiliary ECS.

      **netserver -p** **12001**

      **netserver -p** **12002**

      ##The port number is for the second auxiliary ECS.

      **netserver -p** **12003**

      **netserver -p** **12004**

      ##The port number is for the third auxiliary ECS.

      **netserver -p** **12005**

      **netserver -p** **12006**

      ##The port number is for the fourth auxiliary ECS.

      **netserver -p** **12007**

      **netserver -p** **12008**

      ##The port number is for the fifth auxiliary ECS.

      **netserver -p 12009**

      **netserver -p 12010**

      ##The port number is for the sixth auxiliary ECS.

      **netserver -p** **12011**

      **netserver -p** **12012**

      ##The port number is for the seventh auxiliary ECS.

      **netserver -p** **12013**

      **netserver -p** **12014**

      ##The port number is for the eighth auxiliary ECS.

      **netserver -p** **12015**

      **netserver -p** **12016**

   b. Start the netperf process on all auxiliary ECSs.

      Log in to auxiliary ECS 1.

      **netperf -H 192.168.2.10 -p 12001 -t TCP_STREAM -l 300 -- -m 1440 &**

      **netperf -H 192.168.2.10 -p 12002 -t TCP_STREAM -l 300 -- -m 1440 &**

      Log in to auxiliary ECS 2.

      **netperf -H 192.168.2.10 -p 12003 -t TCP_STREAM -l 300 -- -m 1440 &**

      **netperf -H 192.168.2.10 -p 12004 -t TCP_STREAM -l 300 -- -m 1440 &**

      Log in to auxiliary ECS 3.

      **netperf -H 192.168.2.10 -p 12005 -t TCP_STREAM -l 300 -- -m 1440 &**

      **netperf -H 192.168.2.10 -p 12006 -t TCP_STREAM -l 300 -- -m 1440 &**

      Log in to auxiliary ECS 4.

      **netperf -H 192.168.2.10 -p 12007 -t TCP_STREAM -l 300 -- -m 1440 &**

      **netperf -H 192.168.2.10 -p 12008 -t TCP_STREAM -l 300 -- -m 1440 &**

      Log in to auxiliary ECS 5.

      **netperf -H 192.168.2.10 -p 12009 -t TCP_STREAM -l 300 -- -m 1440 &**

      **netperf -H 192.168.2.10 -p 12010 -t TCP_STREAM -l 300 -- -m 1440 &**

      Log in to auxiliary ECS 6.

      **netperf -H 192.168.2.10 -p 12011 -t TCP_STREAM -l 300 -- -m 1440 &**

      **netperf -H 192.168.2.10 -p 12012 -t TCP_STREAM -l 300 -- -m 1440 &**

      Log in to auxiliary ECS 7.

      **netperf -H 192.168.2.10 -p 12013 -t TCP_STREAM -l 300 -- -m 1440 &**

      **netperf -H 192.168.2.10 -p 12014 -t TCP_STREAM -l 300 -- -m 1440 &**

      Log in to auxiliary ECS 8.

      **netperf -H 192.168.2.10 -p 12015 -t TCP_STREAM -l 300 -- -m 1440 &**

      **netperf -H 192.168.2.10 -p 12016 -t TCP_STREAM -l 300 -- -m 1440 &**

#. Analyze the test result.

   After the test is complete, the output of the netperf process on one TX end is shown in :ref:`Figure 1 <en-us_topic_0115820205__fig333414318238>`. The final result is the sum of the test results of the netperf processes on all TX ends.

   .. _en-us_topic_0115820205__fig333414318238:

   .. figure:: /_static/images/en-us_image_0115873247.png
      :alt: **Figure 1** Output of the netperf process on one TX end

      **Figure 1** Output of the netperf process on one TX end

   .. note::

      There are a large number of netperf processes. To facilitate statistics collection, it is a good practice to run the following command to view test data on the tested ECS using sar:

      **sar -n DEV 1 60**

UDP PPS Test (Using iperf3)
---------------------------

#. Test the UDP TX PPS.

   a. Log in to an auxiliary ECS.

   b. Run the following commands on all auxiliary ECSs to start the server process:

      **iperf3 -s -p 12001 &**

      **iperf3 -s -p 12002 &**

      In the preceding commands, **-p** specifies the listening port.

   c. Start the client process on the tested ECS. For details about common iperf3 parameters, see :ref:`Table 2 <en-us_topic_0115820205__table8470126153613>`.

      ##Auxiliary ECS 1

      **iperf3 -c 192.168.2.11 -p 12001 -u -b 100M -t 300 -l 16 -A 0 &**

      **iperf3 -c 192.168.2.11 -p 12002 -u -b 100M -t 300 -l 16 -A 1 &**

      ##Auxiliary ECS 2

      **iperf3 -c 192.168.2.12 -p 12001 -u -b 100M -t 300 -l 16 -A 2 &**

      **iperf3 -c 192.168.2.12 -p 12002 -u -b 100M -t 300 -l 16 -A 3 &**

      ##Auxiliary ECS 3

      **iperf3 -c 192.168.2.13 -p 12001 -u -b 100M -t 300 -l 16 -A 4 &**

      **iperf3 -c 192.168.2.13 -p 12002 -u -b 100M -t 300 -l 16 -A 5 &**

      ##Auxiliary ECS 4

      **iperf3 -c 192.168.2.14 -p 12001 -u -b 100M -t 300 -l 16 -A 6 &**

      **iperf3 -c 192.168.2.14 -p 12002 -u -b 100M -t 300 -l 16 -A 7 &**

      ##Auxiliary ECS 5

      **iperf3 -c 192.168.2.15 -p 12001 -u -b 100M -t 300 -l 16 -A 8 &**

      **iperf3 -c 192.168.2.15 -p 12002 -u -b 100M -t 300 -l 16 -A 9 &**

      ##Auxiliary ECS 6

      **iperf3 -c 192.168.2.16 -p 12001 -u -b 100M -t 300 -l 16 -A 10 &**

      **iperf3 -c 192.168.2.16 -p 12002 -u -b 100M -t 300 -l 16 -A 11 &**

      ##Auxiliary ECS 7

      **iperf3 -c 192.168.2.17 -p 12001 -u -b 100M -t 300 -l 16 -A 12 &**

      **iperf3 -c 192.168.2.17 -p 12002 -u -b 100M -t 300 -l 16 -A 13 &**

      ##Auxiliary ECS 8

      **iperf3 -c 192.168.2.18 -p 12001 -u -b 100M -t 300 -l 16 -A 14 &**

      **iperf3 -c 192.168.2.18 -p 12002 -u -b 100M -t 300 -l 16 -A 15 &**

#. Test the UDP RX PPS.

   a. Start the server process on the tested ECS. For details about common iperf3 parameters, see :ref:`Table 2 <en-us_topic_0115820205__table8470126153613>`.

      ##The port number is for the first auxiliary ECS.

      **iperf3 -s -p 12001 -A 0 -i 60 &**

      **iperf3 -s -p 12002 -A 1 -i 60 &**

      ##The port number is for the second auxiliary ECS.

      **iperf3 -s -p 12003 -A 2 -i 60 &**

      **iperf3 -s -p 12004 -A 3 -i 60 &**

      ##The port number is for the third auxiliary ECS.

      **iperf3 -s -p 12005 -A 4 -i 60 &**

      **iperf3 -s -p 12006 -A 5 -i 60 &**

      ##The port number is for the fourth auxiliary ECS.

      **iperf3 -s -p 12007 -A 6 -i 60 &**

      **iperf3 -s -p 12008 -A 7 -i 60 &**

      ##The port number is for the fifth auxiliary ECS.

      **iperf3 -s -p 12009 -A 8 -i 60 &**

      **iperf3 -s -p 12010 -A 9 -i 60 &**

      ##The port number is for the sixth auxiliary ECS.

      **iperf3 -s -p 12011 -A 10 -i 60 &**

      **iperf3 -s -p 12012 -A 11 -i 60 &**

      ##The port number is for the seventh auxiliary ECS.

      **iperf3 -s -p 12013 -A 12 -i 60 &**

      **iperf3 -s -p 12014 -A 13 -i 60 &**

      ##The port number is for the eighth auxiliary ECS.

      **iperf3 -s -p 12015 -A 14 -i 60 &**

      **iperf3 -s -p 12016 -A 15 -i 60 &**

   b. Start the client process on all auxiliary ECSs. For details about common iperf3 parameters, see :ref:`Table 2 <en-us_topic_0115820205__table8470126153613>`.

      Log in to auxiliary ECS 1.

      **iperf3 -c 192.168.2.10 -p 12001 -u -b 100M -t 300 -l 16 -A 0 &**

      **iperf3 -c 192.168.2.10 -p 12002 -u -b 100M -t 300 -l 16 -A 1 &**

      Log in to auxiliary ECS 2.

      **iperf3 -c 192.168.2.10 -p 12003 -u -b 100M -t 300 -l 16 -A 0 &**

      **iperf3 -c 192.168.2.10 -p 12004 -u -b 100M -t 300 -l 16 -A 1 &**

      Log in to auxiliary ECS 3.

      **iperf3 -c 192.168.2.10 -p 12005 -u -b 100M -t 300 -l 16 -A 0 &**

      **iperf3 -c 192.168.2.10 -p 12006 -u -b 100M -t 300 -l 16 -A 1 &**

      Log in to auxiliary ECS 4.

      **iperf3 -c 192.168.2.10 -p 12007 -u -b 100M -t 300 -l 16 -A 0 &**

      **iperf3 -c 192.168.2.10 -p 12008 -u -b 100M -t 300 -l 16 -A 1 &**

      Log in to auxiliary ECS 5.

      **iperf3 -c 192.168.2.10 -p 12009 -u -b 100M -t 300 -l 16 -A 0 &**

      **iperf3 -c 192.168.2.10 -p 12010 -u -b 100M -t 300 -l 16 -A 1 &**

      Log in to auxiliary ECS 6.

      **iperf3 -c 192.168.2.10 -p 12011 -u -b 100M -t 300 -l 16 -A 0 &**

      **iperf3 -c 192.168.2.10 -p 12012 -u -b 100M -t 300 -l 16 -A 1 &**

      Log in to auxiliary ECS 7.

      **iperf3 -c 192.168.2.10 -p 12013 -u -b 100M -t 300 -l 16 -A 0 &**

      **iperf3 -c 192.168.2.10 -p 12014 -u -b 100M -t 300 -l 16 -A 1 &**

      Log in to auxiliary ECS 8.

      **iperf3 -c 192.168.2.10 -p 12015 -u -b 100M -t 300 -l 16 -A 0 &**

      **iperf3 -c 192.168.2.10 -p 12016 -u -b 100M -t 300 -l 16 -A 1 &**

#. Analyze the test result.

   :ref:`Figure 2 <en-us_topic_0115820205__fig166644134610>` shows an example of the UDP PPS test result.

   .. _en-us_topic_0115820205__fig166644134610:

   .. figure:: /_static/images/en-us_image_0115874559.png
      :alt: **Figure 2** UDP PPS test result

      **Figure 2** UDP PPS test result

   .. note::

      There are a large number of iperf3 processes. To facilitate statistics collection, it is a good practice to run the following command to view test data on the tested ECS using sar:

      **sar -n DEV 1 60**

Latency Test
------------

#. Run the following command to start the qperf process on the tested ECS:

   **qperf &**

#. Log in to auxiliary ECS 1 and run the following command to perform a latency test:

   **qperf 192.168.2.10 -m 64 -t 60 -vu udp_lat**

   After the test is complete, the **lat** value in the command output is the latency between ECSs.
