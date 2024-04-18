:original_name: en-us_topic_0133339807.html

.. _en-us_topic_0133339807:

Modifying a Private IP Address
==============================

Scenarios
---------

You can modify the private IP address of the NIC. If you want to modify the private IP address of an extension NIC, delete the NIC and attach a new NIC.

Constraints
-----------

-  The ECS must be stopped.
-  If a virtual IP address or DNAT rule has been configured for the NIC, cancel the configuration before modifying the private IP address.
-  If the NIC has an IPv6 address, its private IP address (IPv4 or IPv6 address) cannot be modified.
-  Before changing the private IP address of an ELB backend server, delete the backend server group.

Procedure
---------

#. Log in to the management console.

#. Under **Computing**, click **Elastic Cloud Server**.

#. Click the name of the target ECS.

   The ECS details page is displayed.

#. Click the **NICs** tab. Locate the row containing the network interface and click **Modify Private IP**.

   The **Modify Private IP** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0000001707364141.png
      :alt: **Figure 1** Modifying the private IP address

      **Figure 1** Modifying the private IP address

#. Change the subnet and private IP address of the NIC as required.

   .. note::

      Subnets can be changed only within the same VPC.

   If the target private IP address is not specified, the system will automatically assign one to the primary NIC.
