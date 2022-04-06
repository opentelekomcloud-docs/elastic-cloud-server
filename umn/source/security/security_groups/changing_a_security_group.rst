.. _en-us_topic_0093492517:

Changing a Security Group
=========================



.. _en-us_topic_0093492517__section5630193654713:

Scenarios
---------

To change the security group of an ECS NIC, perform the operations described in this section.



.. _en-us_topic_0093492517__section148110439474:

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the ECS list, locate the row that contains the target ECS. Click **More** in the **Operation** column and select **Manage Network** > **Change Security Group**.

   The **Change Security Group** dialog box is displayed.

   

.. _en-us_topic_0093492517__fig1673733486:

   .. figure:: /_static/images/en-us_image_0122999741.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 1** Change Security Group

#. Select the target NIC and security groups as prompted.

   You can select multiple security groups. In such a case, the rules of all the selected security groups will be aggregated to apply on the ECS.

   To create a security group, click **Create Security Group**.

   .. note::

      Using multiple security groups may deteriorate ECS network performance. You are suggested to select no more than five security groups.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0093507575.png

