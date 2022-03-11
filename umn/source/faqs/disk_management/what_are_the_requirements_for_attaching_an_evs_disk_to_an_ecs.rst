What Are the Requirements for Attaching an EVS Disk to an ECS?
==============================================================

-  The EVS disk and the target ECS must be located in the same AZ.

-  For a non-shared disk, the EVS disk must be in **Available** state.

   For a shared disk, the target EVS disk must be in **In-use** or **Available** state.

-  The target ECS must be in **Running** or **Stopped** state.

-  A SCSI EVS disk cannot be used as an ECS system disk.

-  Certain ECSs support SCSI EVS disk attachment. For details, see `Which ECSs Can Be Attached with SCSI EVS Disks? <faqs/disk_management/which_ecss_can_be_attached_with_scsi_evs_disks>`__

