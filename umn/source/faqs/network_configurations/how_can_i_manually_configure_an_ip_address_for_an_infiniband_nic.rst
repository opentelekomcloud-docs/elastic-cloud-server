:original_name: en-us_topic_0083225171.html

.. _en-us_topic_0083225171:

How Can I Manually Configure an IP Address for an InfiniBand NIC?
=================================================================

IP over InfiniBand (IPoIB) allows IP data transmission over InfiniBand. For SUSE high-performance H2 and HL1 ECSs, if IPoIB is required, you must manually configure an IP address for the InfiniBand NIC after installing the InfiniBand NIC driver.

Prerequisites
-------------

The InfiniBand NIC driver has been installed on the high-performance H2 or HL1 ECSs.

.. _en-us_topic_0083225171__section42060912112551:

Background
----------

To prevent IP address conflict of the InfiniBand NICs configured for the ECSs of a tenant, determine the IP address to be configured for an InfiniBand NIC according to the IP addresses available in the VPC. The method is as follows:

For example, if the first two eight-bits of the IP address (specified by **IPADDR**) to be configured for the InfiniBand NIC are consistently **169.254**, the latter two eight-bits must be the same as those of the **eth0** IP address, and the subnet mask must be the same as that of the **eth0** NIC.

An example is provided as follows:

If the IP address of the **eth0** NIC is 192.168.0.100/24, the IP address to be configured for the InfiniBand NIC is 169.254.0.100/24.

Procedure
---------

#. Log in to the ECS.

#. Run the following command to switch to user **root**:

   **sudo su -**

#. Run the following command to edit the **/etc/sysconfig/network/ifcfg-ib0** file:

   **vi /etc/sysconfig/network/ifcfg-ib0**

#. Enter the following information:

   **DEVICE=ib0**

   **BOOTPROTO=static**

   **IPADDR=**\ *IP address to be configured for the InfiniBand NIC*

   **NETMASK=**\ *Subnet mask*

   **STARTMODE=auto**

   .. note::

      For instructions about how to obtain the IP address and subnet mask for an InfiniBand NIC, see :ref:`Background <en-us_topic_0083225171__section42060912112551>`.

#. Run the following command to restart the network for the configuration to take effect:

   **service network restart**
