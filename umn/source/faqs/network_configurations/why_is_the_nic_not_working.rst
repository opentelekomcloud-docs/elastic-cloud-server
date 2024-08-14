:original_name: en-us_topic_0036068717.html

.. _en-us_topic_0036068717:

Why Is the NIC Not Working?
===========================

Symptom
-------

The NIC equipped on a disk-intensive or large-memory ECS does not work.

Possible Causes
---------------

The NIC driver has not been correctly installed.

Solution
--------

Disk-intensive and large-memory ECSs use passthrough NICs to improve network performance. You must install the passthrough NIC driver on the ECSs or the image that is used for creating the ECSs.

.. note::

   If you mount the CD/DVD-ROM driver over a VPN, ensure that the VPN bandwidth is greater than 8 Mbit/s.

To install the passthrough NICE driver, do as follows:

#. Obtain the passthrough NIC driver.

   Passthrough NIC driver versions vary depending on the OS. For details, see :ref:`Table 1 <en-us_topic_0036068717__table39612229174432>`.

   .. _en-us_topic_0036068717__table39612229174432:

   .. table:: **Table 1** NIC driver versions and OSs

      +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+
      | NIC Driver Version    | OS                                        | How to Obtain                                                         |
      +=======================+===========================================+=======================================================================+
      | ixgbevf 2.16.4        | CentOS 7.2 64bit                          | https://sourceforge.net/projects/e1000/files/ixgbevf%20stable/2.16.4/ |
      +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+
      |                       | Red Hat Enterprise Linux 7.2 64bit        |                                                                       |
      +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+
      | ixgbevf 2.16.1        | SUSE Linux Enterprise Server 11 SP3 64bit | https://sourceforge.net/projects/e1000/files/ixgbevf%20stable/2.16.1/ |
      |                       |                                           |                                                                       |
      |                       | SUSE Linux Enterprise Server 11 SP4 64bit |                                                                       |
      +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+

#. Log in to the ECS.

   For more details, see :ref:`Login Overview <en-us_topic_0013771089>`.

#. Install the passthrough NIC driver on the ECS. In this procedure, Red Hat Enterprise Linux 7.2 64bit is used as an example.

   a. Configure the passthrough NIC.

      Not all ECS OSs identify passthrough NICs using the standard NIC naming rule of **eth**\ *x*, where *x* is a number. If this is the case, you must configure the ECS so that it can identify the passthrough NIC. The procedure is as follows:

      #. Run the following command to view all NICs on the ECS and identify the passthrough NIC:

         **ifconfig -a**

      #. Run the following command to switch to the directory where configuration files are stored:

         **cd /etc/sysconfig/network-scripts/**

      #. Run the following command to create a configuration file for the passthrough NIC:

         **cp ifcfg-eth0 ifcfg-**\ *NIC_name*

         In the preceding command, *NIC_name* specifies the name of the passthrough NIC.

      #. Use the vi editor to edit this configuration file:

         **vi ifcfg-**\ *NIC_name*

      #. Set the **DEVICE** parameter in the configuration file to the name of the passthrough NIC. The following is an example configuration:

         .. code-block::

            DEVICE="NIC_name"
            BOOTPROTO="dhcp"
            ONBOOT="yes"
            STARTMODE="onboot"

      #. Run the following command to restart the network service and allow the configuration to take effect:

         **service network restart**

   b. Upload the obtained passthrough NIC driver to a directory on the ECS, for example, **/home**.

   c. Switch to user **root** on the ECS CLI and open the target directory.

      In this example, the passthrough NIC driver is stored in the **/home** directory. Run the **cd** */home* command to switch to the target directory.

   d. Run the following command to decompress the software package. (In this procedure, ixgbevf version 2.16.4 is used as an example.)

      **tar -zxvf ixgbevf-2.16.4.tar.gz**

   e. Run the following command to switch to the generated **src** directory:

      **cd ixgbevf-2.16.4/src**

   f. Run the following commands to install the driver:

      **make**

      **make install**

   g. Run the following command to restart the ECS to make the drive take effect:

      **reboot**

   h. Switch to user **root** on the ECS CLI and open the **src** directory, for example, by running the **cd** */home/ixgbevf-2.16.4/src* command. Then, run the following commands to check whether the driver has been installed:

      **rmmod ixgbevf**

      **insmod ./ixgbevf.ko**

      **ethtool -i** *NIC_name*

      In the preceding command, *NIC_name* specifies the passthrough NIC name, for example, **ens5**.

      .. note::

         -  After you run the **rmmod ixgbevf** command, the system may display an error message. This message does not affect the installation of the passthrough NIC driver and can be ignored.
         -  *NIC_name* specifies the passthrough NIC name, for example, **ens5.**

   i. Check the driver status based on the displayed information.

      In this example, the driver is installed if **driver** is **ixgbevf** and **version** is **2.16.4**.
