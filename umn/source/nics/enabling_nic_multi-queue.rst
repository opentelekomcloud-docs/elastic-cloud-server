:original_name: en-us_topic_0058758453.html

.. _en-us_topic_0058758453:

Enabling NIC Multi-Queue
========================

Scenarios
---------

Single-core CPU performance cannot meet the requirement of processing NIC interruptions incurred with the increase of network I/O bandwidth. NIC multi-queue enables multiple CPUs to process ECS NIC interruptions, thereby improving PPS and I/O performance.

The ECS described in this section is assumed to comply with the requirements on specifications and virtualization type.

-  If the ECS was created using a public image listed in :ref:`Support of NIC Multi-Queue <en-us_topic_0058758453__section892862210138>`, NIC multi-queue has been enabled on the ECS by default. Therefore, you do not need to perform the operations described in this section.
-  If the ECS was created using a private image and the OS of the external image file is listed in :ref:`Support of NIC Multi-Queue <en-us_topic_0058758453__section892862210138>`, perform the following operations to enable NIC multi-queue:

   #. :ref:`Importing the External Image File to the IMS Console <en-us_topic_0058758453__section1659682611504>`
   #. :ref:`Setting NIC Multi-Queue for the Image <en-us_topic_0058758453__section1949113217282>`
   #. :ref:`Creating an ECS Using a Private Image <en-us_topic_0058758453__section1841681225617>`
   #. :ref:`Enabling NIC Multi-Queue <en-us_topic_0058758453__section214227201118>`

.. _en-us_topic_0058758453__section892862210138:

Support of NIC Multi-Queue
--------------------------

NIC multi-queue can be enabled on an ECS only when the ECS specifications, virtualization type, and image OS meet the requirements described in this section.

-  For details about the ECS specifications that support NIC multi-queue, see :ref:`ECS Specifications and Types <en-us_topic_0132345719>`.

   .. note::

      If the number of NIC queues is greater than 1, NIC multi-queue is supported.

-  The virtualization type must be KVM.
-  The Linux public images listed in :ref:`Table 2 <en-us_topic_0058758453__table1572993710538>` support NIC multi-queue.

   .. note::

      -  Windows public images have not supported NIC multi-queue. If you enable NIC multi-queue in a Windows public image, starting an ECS created using such an image may be slow.

      -  It is a good practice to upgrade the kernel version of the Linux ECS to 2.6.35 or later. Otherwise, NIC multi-queue is not supported.

         Run the **uname -r** command to obtain the kernel version. If the kernel version is earlier than 2.6.35, contact customer service to upgrade the kernel.

.. table:: **Table 1** Support of NIC multi-queue for Linux ECSs

   +----------------------------------------------------+----------------------------+------------------------------------+
   | Image                                              | Support of NIC Multi-Queue | NIC Multi-Queue Enabled by Default |
   +====================================================+============================+====================================+
   | Ubuntu 14.04/16.04/18.04/20.04 server 64bit        | Yes                        | Yes                                |
   +----------------------------------------------------+----------------------------+------------------------------------+
   | OpenSUSE 42.2/15.\* 64bit                          | Yes                        | Yes                                |
   +----------------------------------------------------+----------------------------+------------------------------------+
   | SUSE Enterprise 12 SP1/SP2 64bit                   | Yes                        | Yes                                |
   +----------------------------------------------------+----------------------------+------------------------------------+
   | CentOS 6.8/6.9/7.*/8.\* 64bit                      | Yes                        | Yes                                |
   +----------------------------------------------------+----------------------------+------------------------------------+
   | Debian 8.0.0/8.8.0/8.9.0/9.0.0/10.0.0/10.2.0 64bit | Yes                        | Yes                                |
   +----------------------------------------------------+----------------------------+------------------------------------+
   | Fedora 24/25/30 64bit                              | Yes                        | Yes                                |
   +----------------------------------------------------+----------------------------+------------------------------------+
   | EulerOS 2.2/2.3/2.5 64bit                          | Yes                        | Yes                                |
   +----------------------------------------------------+----------------------------+------------------------------------+

.. _en-us_topic_0058758453__table1572993710538:

.. table:: **Table 2** Support of NIC multi-queue for KVM ECSs

   +---------+-------------------------------------------------------------+--------------------------------+
   | OS      | Image                                                       | Status                         |
   +=========+=============================================================+================================+
   | Windows | Windows Server 2008 Web R2 64-bit                           | Supported using private images |
   +---------+-------------------------------------------------------------+--------------------------------+
   |         | Windows Server 2008 R2 Standard/DataCenter/Enterprise 64bit | Supported using private images |
   +---------+-------------------------------------------------------------+--------------------------------+
   |         | Windows Server 2012 R2 Standard/DataCenter 64bit            | Supported using private images |
   +---------+-------------------------------------------------------------+--------------------------------+
   |         | Windows Server 2016 Standard/DataCenter 64bit               | Supported using private images |
   +---------+-------------------------------------------------------------+--------------------------------+
   | Linux   | Ubuntu 14.04/16.04 server 64bit                             | Supported                      |
   +---------+-------------------------------------------------------------+--------------------------------+
   |         | OpenSUSE 42.2 64bit                                         | Supported                      |
   +---------+-------------------------------------------------------------+--------------------------------+
   |         | SUSE Enterprise 12 SP1/SP2 64bit                            | Supported                      |
   +---------+-------------------------------------------------------------+--------------------------------+
   |         | CentOS 6.8/6.9/7.0/7.1/7.2/7.3/7.4/7.5/7.6 64bit            | Supported                      |
   +---------+-------------------------------------------------------------+--------------------------------+
   |         | Debian 8.0.0/8.8.0/8.9.0/9.0.0 64bit                        | Supported                      |
   +---------+-------------------------------------------------------------+--------------------------------+
   |         | Fedora 24/25 64bit                                          | Supported                      |
   +---------+-------------------------------------------------------------+--------------------------------+
   |         | EulerOS 2.2 64bit                                           | Supported                      |
   +---------+-------------------------------------------------------------+--------------------------------+

.. _en-us_topic_0058758453__section1659682611504:

Importing the External Image File to the IMS Console
----------------------------------------------------

For details, see "Registering an Image File as a Private Image" in *Image Management Service User Guide*.

.. _en-us_topic_0058758453__section1949113217282:

Setting NIC Multi-Queue for the Image
-------------------------------------

Windows OSs have not commercially supported NIC multi-queue. If you enable NIC multi-queue in a Windows image, starting an ECS created using such an image may be slow.

Use one of the following methods to set the NIC multi-queue attribute:

**Method 1:**

#. Log in to the management console.
#. Under **Computing**, click **Image Management Service**.
#. Click the **Private Images** tab, locate the row containing the target image, click **Modify** in the **Operation** column.
#. Set the NIC multi-queue attribute of the image.

**Method 2:**

#. Log in to the management console.
#. Under **Computing**, click **Image Management Service**.
#. Click the **Private Images** tab. In the image list, click the name of the target image to switch to the page providing details about the image.
#. Click **Modify** in the upper right corner. In the displayed **Modify Image** dialog box, set the NIC multi-queue attribute.

**Method 3:** Add **hw_vif_multiqueue_enabled** to an image through the API.

#. .. _en-us_topic_0058758453__en-us_topic_0085214115_li13762086162643:

   For instructions about how to obtain the token, see `Token Authentication <https://docs.otc.t-systems.com/en-us/api/apiug/apig-en-api-180328003.html>`__.

#. For instructions about how to call an API to update image information, see "Updating Image Information (Native OpenStack API)" in *Image Management Service API Reference*.

#. Add **X-Auth-Token** to the request header.

   The value of **X-Auth-Token** is the token obtained in step :ref:`1 <en-us_topic_0058758453__en-us_topic_0085214115_li13762086162643>`.

#. Add **Content-Type** to the request header.

   The value of **Content-Type** is **application/openstack-images-v2.1-json-patch**.

   The request URI is in the following format:

   PATCH /v2/images/{image_id}

   The request body is as follows:

   .. code-block::

      [
               {
                "op":"add",
                "path":"/hw_vif_multiqueue_enabled",
                "value": "true"
               }
       ]

   :ref:`Figure 1 <en-us_topic_0058758453__en-us_topic_0085214115_fig3215821216479>` shows an example request body for modifying the NIC multi-queue attribute.

   .. _en-us_topic_0058758453__en-us_topic_0085214115_fig3215821216479:

   .. figure:: /_static/images/en-us_image_0193026956.png
      :alt: **Figure 1** Example request body

      **Figure 1** Example request body

.. _en-us_topic_0058758453__section1841681225617:

Creating an ECS Using a Private Image
-------------------------------------

Create an ECS using a registered private image. For details, see :ref:`Creating an ECS <en-us_topic_0021831611>`. Note the following when setting the parameters:

-  **Region**: Select the region where the private image is located.
-  **Image**: Select **Private image** and then the desired image from the drop-down list.

.. _en-us_topic_0058758453__section214227201118:


Enabling NIC Multi-Queue
------------------------

KVM Windows ECSs use private images to support NIC multi-queue. For details, see "How Do I Set NIC Multi-queue Feature of an Image?" in *Image Management Service User Guide*.

This section uses a Linux ECS running CentOS 7.4 as an example to describe how to enable NIC multi-queue.

#. Enable NIC multi-queue.

   a. Log in to the ECS.

   b. Run the following command to obtain the number of queues supported by the NIC and the number of queues with NIC multi-queue enabled:

      **ethtool -l** *NIC*

   c. Run the following command to configure the number of queues used by the NIC:

      **ethtool -L** *NIC* **combined** *Number of queues*

   An example is provided as follows:

   .. code-block:: console

      [root@localhost ~]# ethtool -l eth0  #View the number of queues used by NIC eth0.
      Channel parameters for eth0:
      Pre-set maximums:
      RX:               0
      TX:               0
      Other:                  0
      Combined: 4  #Indicates that a maximum of four queues can be enabled for the NIC.
      Current hardware settings:
      RX:               0
      TX:               0
      Other:                  0
      Combined: 1 #Indicates that one queue has been enabled.

      [root@localhost ~]# ethtool -L eth0 combined 4 #Enable four queues on NIC eth0.

#. (Optional) Enable irqbalance so that the system automatically allocates NIC interrupts on multiple vCPUs.

   a. Run the following command to enable irqbalance:

      **service irqbalance start**

   b. Run the following command to view the irqbalance status:

      **service irqbalance status**

      If the **Active** value in the command output contains **active (running)**, irqbalance has been enabled.


      .. figure:: /_static/images/en-us_image_0126402833.png
         :alt: **Figure 2** Enabled irqbalance

         **Figure 2** Enabled irqbalance

#. (Optional) Enable interrupt binding.

   Enabling irqbalance allows the system to automatically allocate NIC interrupts, improving network performance. If the improved network performance still fails to meet your requirements, manually configure interrupt affinity on the ECS.

   To do so, perform the following operations:

   Configure the following script so that one ECS vCPU serves the interrupt requests initialized by one queue. One queue corresponds to one interrupt, and one interrupt binds to one vCPU.

   .. code-block::

      #!/bin/bash
      service irqbalance stop

      eth_dirs=$(ls -d /sys/class/net/eth*)
      if [ $? -ne 0 ];then
          echo "Failed to find eth*  , sleep 30" >> $ecs_network_log
          sleep 30
          eth_dirs=$(ls -d /sys/class/net/eth*)
      fi

      for eth in $eth_dirs
      do
          cur_eth=$(basename $eth)
          cpu_count=`cat /proc/cpuinfo| grep "processor"| wc -l`
          virtio_name=$(ls -l /sys/class/net/"$cur_eth"/device/driver/ | grep pci |awk {'print $9'})

          affinity_cpu=0
          virtio_input="$virtio_name""-input"
          irqs_in=$(grep "$virtio_input" /proc/interrupts | awk -F ":" '{print $1}')
          for irq in ${irqs_in[*]}
          do
              echo $((affinity_cpu%cpu_count)) > /proc/irq/"$irq"/smp_affinity_list
              affinity_cpu=$[affinity_cpu+2]
          done

          affinity_cpu=1
          virtio_output="$virtio_name""-output"
          irqs_out=$(grep "$virtio_output" /proc/interrupts | awk -F ":" '{print $1}')
          for irq in ${irqs_out[*]}
          do
              echo $((affinity_cpu%cpu_count)) > /proc/irq/"$irq"/smp_affinity_list
              affinity_cpu=$[affinity_cpu+2]
          done
      done

#. (Optional) Enable XPS and RPS.

   XPS allows the system with NIC multi-queue enabled to select a queue by vCPU when sending a data packet.

   .. code-block::

      #!/bin/bash
      # enable XPS feature
      cpu_count=$(grep -c processor /proc/cpuinfo)
      dec2hex(){
        echo $(printf "%x" $1)
      }
      eth_dirs=$(ls -d /sys/class/net/eth*)
      if [ $? -ne 0 ];then
          echo "Failed to find eth* , sleep 30" >> $ecs_network_log
          sleep 30
          eth_dirs=$(ls -d /sys/class/net/eth*)
      fi
      for eth in $eth_dirs
      do
          cpu_id=1
          cur_eth=$(basename $eth)
          cur_q_num=$(ethtool -l $cur_eth | grep -iA5 current | grep -i combined | awk {'print $2'})
          for((i=0;i<cur_q_num;i++))
          do
              if [ $i -eq $cpu_count ];then
                  cpu_id=1
              fi
              xps_file="/sys/class/net/${cur_eth}/queues/tx-$i/xps_cpus"
              rps_file="/sys/class/net/${cur_eth}/queues/rx-$i/rps_cpus"
              cpuset=$(dec2hex "$cpu_id")
              echo $cpuset > $xps_file
              echo $cpuset > $rps_file
              let cpu_id=cpu_id*2
          done
      done
