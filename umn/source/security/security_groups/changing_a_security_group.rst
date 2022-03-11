Changing a Security Group
=========================

Scenarios
---------

To change the security group of an ECS NIC, perform the operations described in this section.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the ECS list, locate the row that contains the target ECS. Click **More** in the **Operation** column and select **Manage Network** > **Change Security Group**.

   The **Change Security Group** dialog box is displayed.

   | **Figure 1** Change Security Group
   | |image2|

#. Select the target NIC and security groups as prompted.

   You can select multiple security groups. In such a case, the rules of all the selected security groups will be aggregated to apply on the ECS.

   To create a security group, click **Create Security Group**.

   |image3|

   Using multiple security groups may deteriorate ECS network performance. You are suggested to select no more than five security groups.

#. Click **OK**.



.. |image1| image:: /_static/images/en-us_image_0093507575.png

.. |image2| image:: /_static/images/en-us_image_0122999741.png
   :class: imgResize

.. |image3| image:: /_static/images/note_3.0-en-us.png
