:original_name: en-us_topic_0093492517.html

.. _en-us_topic_0093492517:

Changing a Security Group
=========================

Scenarios
---------

To change the security group associated with an ECS network interface, perform the operations described in this section.

Constraints
-----------

-  Changing the security group will overwrite the original security group settings.
-  Using multiple security groups may deteriorate ECS network performance. You are advised to select no more than five security groups.

Procedure
---------

#. Log in to the management console and access the ECS list page.

#. Click |image1| in the upper left corner and select a region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the ECS list, choose **More** > **Manage Network** > **Change Security Group** in the **Operation** column.

   The **Change Security Group** panel slides out.


   .. figure:: /_static/images/en-us_image_0000002385344877.png
      :alt: **Figure 1** Change Security Group

      **Figure 1** Change Security Group

#. Select the target NIC and security groups.

   You can select multiple security groups. In such a case, the rules of all the selected security groups will apply to the ECS.

   To create a security group, click **Create Security Group**.

   .. note::

      Using multiple security groups may deteriorate ECS network performance. You are advised to select no more than five security groups.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000002188678994.png
