:original_name: en-us_topic_0040863659.html

.. _en-us_topic_0040863659:

What Are the Requirements for Attaching an EVS Disk to an ECS?
==============================================================

-  The EVS disk and the target ECS must be located in the same AZ.

-  For a non-shared disk, the EVS disk must be in **Available** state.

   For a shared disk, the target EVS disk must be in **In-use** or **Available** state.

-  The target ECS must be in **Running** or **Stopped** state.

-  Certain ECSs support SCSI EVS disk attachment. For details, see :ref:`Which ECSs Can Be Attached with SCSI EVS Disks? <en-us_topic_0077938284>`
