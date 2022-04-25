:original_name: en-us_topic_0093492519.html

.. _en-us_topic_0093492519:

Deleting a NIC
==============

Scenarios
---------

An ECS can have up to 12 NICs, including one primary NIC that cannot be deleted and extension NICs. This section describes how to delete an extension NIC.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the **Elastic Cloud Server** page, click the name of the target ECS.

   The page providing details about the ECS is displayed.

#. Click the **NICs** tab. Then, click **Delete** in the row of the target NIC.

   .. note::

      You are not allowed to delete the primary ECS NIC. By default, the primary ECS NIC is the first NIC displayed in the NIC list.

#. Click **Yes** in the displayed dialog box.

   .. note::

      Certain ECSs do not support NIC deletion when they are running. For details about these ECSs, see the GUI display. To delete a NIC from such an ECS, stop the ECS.

.. |image1| image:: /_static/images/en-us_image_0093507592.png

