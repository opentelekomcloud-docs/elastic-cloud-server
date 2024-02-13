:original_name: en-us_topic_0093492519.html

.. _en-us_topic_0093492519:

Deleting a Network Interface
============================

Scenarios
---------

An ECS can have up to 12 network interfaces, including one primary network interface that cannot be deleted and extension network interfaces. This section describes how to delete a network interface.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the **Elastic Cloud Server** page, click the name of the target ECS.

   The page providing details about the ECS is displayed.

#. Click the **NICs** tab. Then, click **Delete** in the row of the target network interface.

   .. note::

      You are not allowed to delete the primary ECS network interface. By default, the primary ECS network interface is the first network interface displayed in the network interface list.

#. In the displayed dialog box, click OK.

   .. note::

      Certain ECSs do not support network interface deletion when they are running. For details, see the GUI display. To delete a network interface from such an ECS, stop the ECS first.

.. |image1| image:: /_static/images/en-us_image_0093507592.png
