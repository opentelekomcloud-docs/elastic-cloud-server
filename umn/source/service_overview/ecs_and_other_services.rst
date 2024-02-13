:original_name: en-us_topic_0013771111.html

.. _en-us_topic_0013771111:

ECS and Other Services
======================

:ref:`Figure 1 <en-us_topic_0013771111__fig44795566546>` shows the relationships between ECS and other services.

.. _en-us_topic_0013771111__fig44795566546:

.. figure:: /_static/images/en-us_image_0225439857.png
   :alt: **Figure 1** Relationships between ECS and other services

   **Figure 1** Relationships between ECS and other services

ECS-related Services
--------------------

-  Auto Scaling (AS)

   Automatically adjusts ECS resources based on the configured AS policies. This improves resource usage and reduces resource costs.

-  Elastic Load Balancing (ELB)

   Automatically distributes traffic to multiple ECSs. This enhances system service and fault tolerance capabilities.

-  Elastic Volume Service (EVS)

   Enables you to attach EVS disks to an ECS and expand their capacity.

-  Virtual Private Cloud (VPC)

   Enables you to configure internal networks and change network configurations by customizing security groups, VPNs, IP address ranges, and bandwidth. This simplifies network management. You can also customize the ECS access rules within a security group and between security groups to improve ECS security.

-  Image Management Service (IMS)

   Enables you to create ECSs using images. This improves the efficiency of ECS creation.

-  Cloud Eye

   Allows you to check the status of monitored service objects after you have obtained an ECS. This can be done without requiring additional plug-ins be installed. For details about the metrics supported by ECS, see :ref:`Basic ECS Metrics <en-us_topic_0030911465>`.

-  Key Management Service (KMS)

   The encryption feature relies on KMS. You can use an encrypted image or EVS disks when creating an ECS. In such a case, you need to use the key provided by KMS to improve data security.

-  Cloud Trace Service (CTS)

   Records ECS-related operations for later query, audit, and backtrack.

-  Cloud Backup and Recovery (CBR)

   Backs up EVS disks and ECSs for restoration. You can back up all EVS disks (including the system disk and data disks) attached to an ECS and use the backup to restore the ECS data.

-  Tag Management Service (TMS)

   Tags can be used to identify ECSs for easy management.
