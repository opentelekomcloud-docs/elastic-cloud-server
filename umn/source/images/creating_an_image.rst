:original_name: en-us_topic_0101604508.html

.. _en-us_topic_0101604508:

Creating an Image
=================

Scenarios
---------

You can use an existing ECS to create a system disk image, data disk image, and full-ECS image.

-  System disk image: contains an OS and application software for running services. You can use a system disk image to create ECSs and migrate your services to the cloud.
-  Data disk image: contains only service data. You can create a data disk image from an ECS data disk. You can also use a data disk image to create EVS disks and migrate your service data to the cloud.
-  Full-ECS image: contains all the data of an ECS, including the data on the data disks attached to the ECS. A full-ECS image can be used to rapidly create ECSs with service data.

You can use a private image to change the OS. For instructions about how to create a private image, see *Image Management Service User Guide*.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select your region and project.
#. Under **Computing**, click **Elastic Cloud Server**.
#. Locate the row that contains the target ECS and choose **More** > **Manage Image/Disk/Backup** > **Create Image** in the **Operation** column.
#. Configure image information.

   -  **Source**: **ECS**
   -  **ECS**: Retain default settings.
   -  **Name**: Customize your image name.

#. Click **Create Now**.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
