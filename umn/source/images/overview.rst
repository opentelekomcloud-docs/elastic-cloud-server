:original_name: en-us_topic_0177457773.html

.. _en-us_topic_0177457773:

Overview
========

Image
-----

An image is an ECS or BMS template that contains an OS or service data. It may also contain proprietary software and application software, such as database software. Images are classified into public, private, and shared images.

Image Management Service (IMS) allows you to easily create and manage images. You can create an ECS using a public image, private image, or shared image. You can also use an existing ECS or external image file to create a private image.

Public Image
------------

A public image is a standard, widely used image that contains a common OS, such as Ubuntu, CentOS, or Debian, and preinstalled public applications. This image is available to all users. Select your desired public image. Alternatively, create a private image based on a public image to copy an existing ECS or rapidly create ECSs in a batch. You can customize a public image by configuring the application environment or software.

Private Image
-------------

A private image contains an OS or service data, preinstalled public applications, and private applications. It is available only to the user who created it.

.. table:: **Table 1** Private image types

   +-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Image Type        | Description                                                                                                                                          |
   +===================+======================================================================================================================================================+
   | System disk image | Contains an OS and application software for running services. You can use a system disk image to create ECSs and migrate your services to the cloud. |
   +-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data disk image   | Contains only service data. You can use a data disk image to create EVS disks and migrate your service data to the cloud.                            |
   +-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Full-ECS image    | Contains an OS, application software, and data for running services. A full-ECS image contains the system disk and all data disks attached to it.    |
   +-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

If you plan to use a private image to change the OS, ensure that the private image is available. For instructions about how to create a private image, see *Image Management Service User Guide*.

-  If the image of a specified ECS is required, make sure that a private image has been created using this ECS.
-  If a local image file is required, make sure that the image file has been imported to the cloud platform and registered as a private image.
-  If a private image from another region is required, make sure that the image has been copied.
-  If a private image from another user account is required, make sure that the image has been shared with you.

Shared Image
------------

A shared image is a private image shared by another user and can be used as your own private image.

-  Images can be shared within a region only.
-  Each image can be shared to a maximum of 128 tenants.
-  You can stop sharing images anytime without notifying the recipient.
-  You can delete shared image anytime without notifying the recipient.
-  Encrypted images cannot be shared.
-  Full-ECS images cannot be shared.
-  Only the full-ECS images created using CBR can be shared.
