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

#. Locate the row containing the target ECS and choose **More** > **Manage Image/Backup** > **Create Image** in the **Operation** column.

#. Configure the following information:

   :ref:`Table 1 <en-us_topic_0101604508__en-us_topic_0030713149_table050019474117>` and :ref:`Table 2 <en-us_topic_0101604508__en-us_topic_0030713149_table6978715749>` list the parameters in the **Image Type and Source** and **Image Information** areas, respectively.

   .. _en-us_topic_0101604508__en-us_topic_0030713149_table050019474117:

   .. table:: **Table 1** Image type and source

      +------------+-----------------------------------------------------------------------+
      | Parameter  | Description                                                           |
      +============+=======================================================================+
      | Type       | Select **Create Image**.                                              |
      +------------+-----------------------------------------------------------------------+
      | Region     | Select a region close to your business.                               |
      +------------+-----------------------------------------------------------------------+
      | Image Type | Select **System disk image**.                                         |
      +------------+-----------------------------------------------------------------------+
      | Source     | Click the **ECS** tab and select an ECS with required configurations. |
      +------------+-----------------------------------------------------------------------+

   .. _en-us_topic_0101604508__en-us_topic_0030713149_table6978715749:

   .. table:: **Table 2** Image information

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================+
      | Encryption                        | This parameter specifies whether the image will be encrypted. The value is provided by the system and cannot be changed.                                                                                                         |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | -  Only an unencrypted private image can be created from an unencrypted ECS.                                                                                                                                                     |
      |                                   | -  Only an encrypted private image can be created from an encrypted ECS.                                                                                                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                              | Set a name for the image.                                                                                                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | Select an enterprise project from the drop-down list. This parameter is available only if you have enabled enterprise projects or your account is an enterprise account. To enable this function, contact your customer manager. |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | An enterprise project provides central management of cloud resources on a project.                                                                                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tag                               | (Optional) Set a tag key and a tag value for the image to make identification and management of your images easier.                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | (Optional) Enter a description of the image.                                                                                                                                                                                     |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Create Now**.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
