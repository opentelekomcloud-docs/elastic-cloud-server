:original_name: en-us_topic_0093492520.html

.. _en-us_topic_0093492520:

Managing Virtual IP Addresses
=============================

Scenarios
---------

A virtual IP address provides the second IP address for one or more ECS NICs, improving high availability between the ECSs.

One NIC can be bound with up to 10 virtual IP addresses, and one virtual IP address can be bound to up to 10 NICs. Multiple ECSs deployed to work in active/standby mode can be bound with the same virtual IP address for disaster recovery.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the **Elastic Cloud Server** page, click the name of the target ECS.

   The page providing details about the ECS is displayed.

#. Click the **NICs** tab. Then, click **Manage Virtual IP Address**.

   The **Virtual Private Cloud** page is displayed.

#. On the **IP Addresses** tab, select a desired one or click **Assign Virtual IP Address** for a new one.

#. Click **Bind to Server** in the **Operation** column and select the target ECS name and the NIC to bind the virtual IP address to the ECS NIC.

   For more information about virtual IP addresses, see *Virtual Private Cloud User Guide*.

.. |image1| image:: /_static/images/en-us_image_0093518909.png
