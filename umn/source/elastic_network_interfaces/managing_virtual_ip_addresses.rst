:original_name: en-us_topic_0093492520.html

.. _en-us_topic_0093492520:

Managing Virtual IP Addresses
=============================

Background
----------

Generally, cloud servers use private IP addresses for internal communications. Virtual IP addresses provide similar access and support communications within a VPC at Layer 2 and Layer 3, between VPCs with VPC peering connections, between cloud and on-premises networks with VPN or Direct Connect, and Internet access with EIPs. :ref:`Figure 1 <en-us_topic_0093492520__en-us_topic_0118498951_fig945012352420>` describes how private IP addresses, the virtual IP address, and EIPs work together.

-  Private IP addresses are used for internal network communication.
-  The virtual IP address works with Keepalived to build an HA cluster. ECSs in this cluster can be accessed through one virtual IP address.
-  EIPs are used for Internet communication.

.. _en-us_topic_0093492520__en-us_topic_0118498951_fig945012352420:

.. figure:: /_static/images/en-us_image_0000001952856164.png
   :alt: **Figure 1** Different types of IP addresses used by ECSs

   **Figure 1** Different types of IP addresses used by ECSs

For details about virtual IP addresses, see "Virtual IP Address Overview" in the *Virtual Private Cloud User Guide*.

Constraints
-----------

It is recommended that a maximum of eight virtual IP addresses be bound to an ECS. If an ECS has multiple virtual IP addresses, each virtual IP address is used by a specific service. If there are too many services, the ECS may become overloaded and compromise user experience.

Scenarios
---------

A virtual IP address provides the second IP address for one or more ECS NICs, improving high availability between the ECSs.

One NIC can be bound with up to 10 virtual IP addresses, and one virtual IP address can be bound to up to 10 NICs. Multiple ECSs deployed to work in active/standby mode can be bound with the same virtual IP address for disaster recovery.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the **Elastic Cloud Server** page, click the name of the target ECS.

   The ECS details page is displayed.

#. Click the **Network Interfaces** tab. Then, click **Manage Virtual IP Address**.

   The **Virtual Private Cloud** page is displayed.

#. On the **IP Addresses** tab, select a desired one or click **Assign Virtual IP Address** for a new one.

#. Click **Bind to Server** in the **Operation** column and select the target ECS name and the NIC to bind the virtual IP address to the ECS NIC.

   For more information about virtual IP addresses, see *Virtual Private Cloud User Guide*.

.. |image1| image:: /_static/images/en-us_image_0000002188678994.png
