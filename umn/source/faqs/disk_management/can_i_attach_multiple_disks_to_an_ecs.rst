:original_name: en-us_topic_0018073215.html

.. _en-us_topic_0018073215:

Can I Attach Multiple Disks to an ECS?
======================================

Yes. The ECSs created after the disk function upgrade can have up to 60 attached disks.

-  When you create an ECS, you can attach 24 disks to it.
-  After you create an ECS, you can attach up to 60 disks to it.

   .. table:: **Table 1** Numbers of disks that can be attached to a newly created ECS

      +---------------------+-------------------+--------------------+-------------------------------------------------------------------------------+
      | ECS Type            | Maximum VBD Disks | Maximum SCSI Disks | Constraint                                                                    |
      +=====================+===================+====================+===============================================================================+
      | KVM                 | 24                | 59                 | VBD disks + SCSI disks <= 60 (This constraint does not apply to local disks.) |
      |                     |                   |                    |                                                                               |
      | (excluding D2 ECSs) |                   |                    | The number of local disks is determined based on the ECS flavor.              |
      +---------------------+-------------------+--------------------+-------------------------------------------------------------------------------+
      | D2                  | 24                | 30                 | VBD disks + SCSI disks <= 54 (This constraint does not apply to local disks.) |
      |                     |                   |                    |                                                                               |
      |                     |                   |                    | The number of local disks is determined based on the ECS flavor.              |
      +---------------------+-------------------+--------------------+-------------------------------------------------------------------------------+

   .. note::

      -  The system disk of an ECS is of VBD type. Therefore, the maximum number of SCSI disks is 59.
      -  For a D-series KVM ECS, its local disks use two SCSI controllers, indicating that 30 SCSI drive letters are used. Therefore, a maximum of 30 SCSI disks can be attached to such an ECS.

The maximum number of disks that you can attach to an ECS that was created before the disk function upgrade remains unchanged, as shown in :ref:`Table 2 <en-us_topic_0018073215__table3150162605720>`.

.. _en-us_topic_0018073215__table3150162605720:

.. table:: **Table 2** Numbers of disks that can be attached to an existing ECS

   +-------------------+--------------------+---------------------+------------------------------+
   | Maximum VBD Disks | Maximum SCSI Disks | Maximum Local Disks | Constraint                   |
   +===================+====================+=====================+==============================+
   | 24                | 23                 | 59                  | VBD disks + SCSI disks <= 24 |
   +-------------------+--------------------+---------------------+------------------------------+

How Can I Check Whether an ECS Is Created Before or After the Disk Function Upgrade?
------------------------------------------------------------------------------------

#. Log in to management console.
#. Under **Computing**, click **Elastic Cloud Server**.
#. Click the name of the target ECS. The page providing details about the ECS is displayed.
#. Click the **Disks** tab.
#. Check the number of disks that can be attached to the ECS to determine the total number of disks.

   -  If the total number of disks that can be attached is 24 (including the system disk), the ECS is created before the disk function upgrade.
   -  If the total number of disks that can be attached is 60 (including the system disk), the ECS is created after the disk function upgrade.
