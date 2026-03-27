:original_name: en-us_topic_0115820205.html

.. _en-us_topic_0115820205:

How Can I Test the Network Performance of Linux ECSs?
=====================================================

Use netperf and iperf3 to test network performance between ECSs. The test operations include preparations, TCP bandwidth test, UDP PPS test, and latency test.

Background
----------

-  Tested ECS: an ECS that is tested for network performance. Such an ECS functions as the client (TX end) or server (RX end) in netperf tests.

-  Auxiliary ECSs: an ECS that is used to exchange test data with the tested ECS. The auxiliary ECS functions as the client (TX end) or server (RX end) in netperf tests.

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

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                           |
      +===================================+=======================================================================================================================================================+
      | -p                                | Port number                                                                                                                                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | -c                                | IP address of the RX end                                                                                                                              |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | -u                                | UDP packets                                                                                                                                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | -b                                | TX bandwidth                                                                                                                                          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | -t                                | Test duration                                                                                                                                         |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | -l                                | Data packet size, which is suggested to be **16** in PPS tests                                                                                        |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | -A                                | ID of the vCPU used by iperf3                                                                                                                         |
      |                                   |                                                                                                                                                       |
      |                                   | In this section, the maximum number of 16 vCPUs is used as an example for each ECS. If an ECS has eight vCPUs, the **-A** value range is from 0 to 7. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

Test Preparations
-----------------

#. Prepare ECSs.

   Ensure that both type and specifications of the tested ECS and auxiliary ECSs are the same. In addition, ensure that these ECSs are deployed in the same ECS group with anti-affinity enabled.

   .. table:: **Table 3** Preparations

      +---------------+----------+---------------------------------+------------------+-------------------------------+
      | Category      | Quantity | Image                           | Specifications   | IP Address                    |
      +===============+==========+=================================+==================+===============================+
      | Tested ECS    | 1        | CentOS 7.4 64-bit (recommended) | N/A              | 192.168.2.10                  |
      +---------------+----------+---------------------------------+------------------+-------------------------------+
      | Auxiliary ECS | 2        | CentOS 7.4 64-bit (recommended) | At least 8 vCPUs | 192.168.2.11 and 192.168.2.12 |
      +---------------+----------+---------------------------------+------------------+-------------------------------+

#. Install the netperf, iperf3, and sar test tools on both the tested ECS and auxiliary ECSs.

   :ref:`Table 4 <en-us_topic_0115820205__table231811914413>` lists the procedures for installing these tools.

   .. _en-us_topic_0115820205__table231811914413:

   .. table:: **Table 4** Installing test tools

      +-----------------------------------+----------------------------------------------------------------------------------------------------+
      | Tool                              | Procedure                                                                                          |
      +===================================+====================================================================================================+
      | netperf                           | a. Run the following command to install gcc:                                                       |
      |                                   |                                                                                                    |
      |                                   |    .. code-block::                                                                                 |
      |                                   |                                                                                                    |
      |                                   |       yum -y install unzip gcc gcc-c++                                                             |
      |                                   |                                                                                                    |
      |                                   | b. Run the following command to download the netperf installation package:                         |
      |                                   |                                                                                                    |
      |                                   |    .. code-block::                                                                                 |
      |                                   |                                                                                                    |
      |                                   |       wget https://github.com/HewlettPackard/netperf/archive/refs/tags/netperf-2.7.0.zip           |
      |                                   |                                                                                                    |
      |                                   | c. Run the following commands to decompress the installation package and install netperf:          |
      |                                   |                                                                                                    |
      |                                   |    .. code-block::                                                                                 |
      |                                   |                                                                                                    |
      |                                   |       unzip netperf-2.7.0.zip                                                                      |
      |                                   |       cd netperf-netperf-2.7.0/                                                                    |
      |                                   |       ./configure && make && make install                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------+
      | iperf3                            | a. Run the following command to download the iperf3 installation package:                          |
      |                                   |                                                                                                    |
      |                                   |    .. code-block::                                                                                 |
      |                                   |                                                                                                    |
      |                                   |       wget --no-check-certificate https://codeload.github.com/esnet/iperf/zip/master -O iperf3.zip |
      |                                   |                                                                                                    |
      |                                   | b. Run the following commands to decompress the installation package and install iperf3:           |
      |                                   |                                                                                                    |
      |                                   |    .. code-block::                                                                                 |
      |                                   |                                                                                                    |
      |                                   |       unzip iperf3.zip                                                                             |
      |                                   |       cd iperf-master/                                                                             |
      |                                   |       ./configure && make && make install                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------+
      | sar                               | Run the following command to install sar:                                                          |
      |                                   |                                                                                                    |
      |                                   | .. code-block::                                                                                    |
      |                                   |                                                                                                    |
      |                                   |    yum -y install sysstat                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------+

TCP Bandwidth Test (Using netperf)
----------------------------------

Perform the test on multiple flows. In the following example, 64 flows are evenly distributed to two auxiliary ECSs.

.. note::

   The TCP bandwidth test uses the multi-flow model.

   -  When testing the TCP transmission (TX) bandwidth, use the one-to-many model to ensure that the capability of the receiver is sufficient.
   -  When testing the TCP receiver (RX) bandwidth, use the many-to-one model to ensure that the capability of the sender is sufficient.

#. Test the TCP TX bandwidth.

   a. Run the following commands on all auxiliary ECSs to start the netserver process:

      .. code-block::

         #!/bin/bash
         for port in {1..32}; do
             netserver -p $((12000 + port)) > /dev/null 2>&1 &
         done

   b. Start the netperf process on the tested ECS and specify a netserver port for each auxiliary ECS. For details about common netperf parameters, see :ref:`Table 1 <en-us_topic_0115820205__table15359114885218>`.

      .. code-block::

         ##The IP address is for the first auxiliary ECS.
         #!/bin/bash
         server_ip=192.168.2.11 #Private IP address of the test server
         for port in {1..32}; do
             netperf -H ${server_ip} -p $((12000 + port))  -t TCP_STREAM  -l 300 -- -m 1440 > netperf_${server_ip}_$((12000 + port)).log 2>&1 &
         done

         ##The IP address is for the second auxiliary ECS.
         #!/bin/bash
         server_ip2=192.168.2.12 #Private IP address of the test server
         for port in {1..32}; do
             netperf -H ${server_ip2} -p $((12000 + port))  -t TCP_STREAM  -l 300 -- -m 1440 > netperf_${server_ip2}_$((12000 + port)).log 2>&1 &
         done

#. Test the TCP RX bandwidth.

   a. Start the netserver process on the tested ECS.

      .. code-block::

         #!/bin/bash
         for port in {1..64}; do
             netserver -p $((12000 + port)) > /dev/null 2>&1 &
         done

   b. Start the netperf process on each auxiliary ECS.

      .. code-block::

         ##Log in to the first auxiliary ECS.
         #!/bin/bash
         server_ip=192.168.2.10 #Private IP address of the test server
         for port in {1..32}; do
             netperf -H ${server_ip} -p $((12000 + port))  -t TCP_STREAM  -l 300 -- -m 1440  > netperf_${server_ip}_$((12000 + port)).log  2>&1 &
         done
         ##Log in to the second auxiliary ECS.
         #!/bin/bash
         server_ip=192.168.2.10 #Private IP address of the test server
         for port in {33..64}; do
             netperf -H ${server_ip} -p $((12000 + port))  -t TCP_STREAM  -l 300 -- -m 1440  > netperf_${server_ip}_$((12000 + port)).log  2>&1 &
         done

#. Analyze the test result.

   After the test is complete, the output of the netperf process on one TX end is shown in :ref:`Figure 1 <en-us_topic_0115820205__fig333414318238>`. The final result is the sum of the test results of the netperf processes on all TX ends.

   .. _en-us_topic_0115820205__fig333414318238:

   .. figure:: /_static/images/en-us_image_0115873247.png
      :alt: **Figure 1** Output of the netperf process on one TX end

      **Figure 1** Output of the netperf process on one TX end

   .. note::

      There are a large number of netperf processes. To facilitate statistics collection, it is a good practice to run the following command to view test data on the tested ECS using sar:

      .. code-block::

         sar -n DEV 1 60

UDP PPS Test (Using iperf3)
---------------------------

#. Test the UDP TX PPS.

   a. Log in to an auxiliary ECS.

   b. Run the following commands on all auxiliary ECSs to start the server process:

      .. code-block::

         #!/bin/bash
         for port in {1..32}; do
             iperf3 -s -p $((12000 + port)) > /dev/null 2>&1  &
         done

   c. Start the client process on the tested ECS. For details about common iperf3 parameters, see :ref:`Table 2 <en-us_topic_0115820205__table8470126153613>`.

      .. code-block::

         ##The first auxiliary ECS
         #!/bin/bash
         for port in {1..32}; do
         server_ip=192.168.2.11 #Private IP address of the test server
         iperf3 -c ${server_ip} -p $((12000 + port)) -u -b 0M -t 300 -l 64 -i 30 --logfile iperf_${server_ip}_$((12000 + port)).log > /dev/null 2>&1 &
         done

         ##The secondary auxiliary ECS
         #!/bin/bash
         for port in {1..32}; do
         server_ip2=192.168.2.12 #Private IP address of the test server
         iperf3 -c ${server_ip2} -p $((12000 + port)) -u -b 0M -t 300 -l 64 -i 30 --logfile iperf_${server_ip2}_$((12000 + port)).log > /dev/null 2>&1 &
          done

#. Test the UDP RX PPS.

   a. Start the server process on the tested ECS. For details about common iperf3 parameters, see :ref:`Table 2 <en-us_topic_0115820205__table8470126153613>`.

      .. code-block::

         #!/bin/bash
         for port in {1..64}; do
             iperf3 -s -p $((12000 + port))  > /dev/null 2>&1 &
         done

   b. Start the client process on all auxiliary ECSs. For details about common iperf3 parameters, see :ref:`Table 2 <en-us_topic_0115820205__table8470126153613>`.

      .. code-block::

         ##Log in to the first auxiliary ECS.
         #!/bin/bash
         for port in {1..32}; do
         server_ip=192.168.2.10 #Private IP address of the test server
         iperf3 -c ${server_ip} -p $((12000 + port)) -u -b 0M -t 300 -l 64 -i 30 --logfile iperf_${server_ip}_$((12000 + port)).log > /dev/null 2>&1 &
         done

         ##Log in to the second auxiliary ECS.
         #!/bin/bash
         for port in {33..64}; do
         server_ip=192.168.2.10 #Private IP address of the test server
         iperf3 -c ${server_ip} -p $((12000 + port)) -u -b 0M -t 300 -l 64 -i 30 --logfile iperf_${server_ip}_$((12000 + port)).log > /dev/null 2>&1 &
         done

#. Analyze the test result.

   :ref:`Figure 2 <en-us_topic_0115820205__fig166644134610>` shows an example of the UDP PPS test result.

   .. _en-us_topic_0115820205__fig166644134610:

   .. figure:: /_static/images/en-us_image_0115874559.png
      :alt: **Figure 2** UDP PPS test result

      **Figure 2** UDP PPS test result

   .. note::

      There are a large number of iperf3 processes. To facilitate statistics collection, it is a good practice to run the following command to view test data on the tested ECS using sar:

      .. code-block::

         sar -n DEV 1 60

Latency Test
------------

#. Run the following command to start the qperf process on the tested ECS:

   .. code-block::

      qperf &

#. Log in to auxiliary ECS 1 and run the following command to perform a latency test:

   .. code-block::

      qperf 192.168.2.10 -m 64 -t 60 -vu udp_lat

   After the test is complete, the **lat** value in the command output is the latency between ECSs.
