:original_name: en-us_topic_0013771112.html

.. _en-us_topic_0013771112:

What Is ECS?
============

An Elastic Cloud Server (ECS) is a basic computing unit that consists of vCPUs, memory, OS, and Elastic Volume Service (EVS) disks.

You can create an ECS by specifying its vCPUs, memory, OS, and login mode. After creating an ECS, you can use it on the cloud like using your local PC or physical server. You can also modify its specifications if necessary. ECS lets your applications run in a reliable, secure, efficient computing environment.

-  For details about the operating systems supported by an ECS, see :ref:`Image Types <en-us_topic_0030828254>`.
-  For details about the login authentication modes, see :ref:`Logging In to an ECS <en-us_topic_0092494193>`.

System Architecture
-------------------

ECS works with other products and services to provide computing, storage, and network resources.

-  You can deploy ECSs across different availability zones (AZs) that are connected over an intranet. If one AZ becomes unavailable, ECSs in other AZs can continue to provide services.
-  Virtual Private Cloud (VPC) helps you build your own dedicated network on the cloud. You can set subnets and security groups within your VPC for further isolation. You can also bind an EIP to your ECSs for Internet access.
-  With the Image Management Service (IMS), you can use an image to create ECSs. You can also use an existing ECS to create a private image and use the private image to create the same ECSs for rapid service deployment.
-  Elastic Volume Service (EVS) provides storage space. Volume Backup Service (VBS) provides data backup and restoration.
-  Cloud Eye lets you keep a close eye on the performance and resource utilization of ECSs, ensuring ECS reliability and availability.
-  Volume Backup Service (VBS) allows you to create data backups for EVS disks and use the backups to restore the EVS disks. This maximizes user data correctness and security.
-  Backup protection: You can back up all EVS disks (including the system disk and data disks) attached to an ECS and use the backup to restore the ECS data.


.. figure:: /_static/images/en-us_image_0071898891.png
   :alt: **Figure 1** System architecture

   **Figure 1** System architecture

Access Methods
--------------

You can access ECS through the web-based management console or HTTPS-based application programming interfaces (APIs).

-  Accessing ECSs through APIs

   Use this method if you intend to integrate ECSs into a third-party system for secondary development. For details, see *Elastic Cloud Server API Reference*.

-  Accessing ECSs through the management console

   Use this method if you are not required to integrate ECSs with a third-party system.

   Log in to the management console with your account and choose **Elastic Cloud Server** on the homepage.
