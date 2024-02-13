:original_name: en-us_topic_0087382187.html

.. _en-us_topic_0087382187:

Why Does a Linux ECS with a SCSI Disk Attached Fails to Be Restarted?
=====================================================================

Symptom
-------

For a Linux ECS with a SCSI disk attached, if you have enabled automatic SCSI disk attachment upon ECS startup in **/etc/fstab** and the disk drive letter (for example, **/dev/sdb**) is used, the ECS fails to restart.

Possible Causes
---------------

SCSI disk allocation is determined based on the ID of the slot accommodating the disk as well as the available drive letter in the ECS. Each time you attach a disk to the ECS, an idle drive letter is automatically allocated in sequence. When the ECS starts, the disks are loaded in slot sequence. Therefore, a slot ID corresponds to a drive letter.

After the SCSI disk is detached from the running ECS, the slot sequence for disks may change, leading to the disk drive letter being changed after the ECS is restarted. As a result, the slot IDs do not correspond to the drive letters, and the ECS fails to restart.

Solution
--------

#. Log in to the Linux ECS.

#. Run the following command to switch to user **root**:

   **sudo su -**

#. .. _en-us_topic_0087382187__li2064141120446:

   Run the following command to obtain the SCSI ID according to the drive letter of the SCSI disk:

   **ll /dev/disk/by-id/|grep** *Disk drive letter*

   For example, if the drive letter of the SCSI disk is **/dev/sdb**, run the following command:

   **ll /dev/disk/by-id/|grep sdb**

   .. code-block::

      CNA64_22:/opt/galax/eucalyptus/ecs_scripts # ll /dev/disk/by-id/|grep sdb
      lrwxrwxrwx 1 root root  9 Dec  6 11:26 scsi-3688860300001436b005014f890338280 -> ../../sdb
      lrwxrwxrwx 1 root root  9 Dec  6 11:26 wwn-0x688860300001436b005014f890338280 -> ../../sdb

#. Change the drive letter (for example, **/dev/sdb**) of the SCSI disk to the corresponding SCSI ID in the **/etc/fstab** file.

   **/dev/disk/by-id/**\ *SCSI ID*

   For example, if the SCSI ID obtained in step :ref:`3 <en-us_topic_0087382187__li2064141120446>` is scsi-3688860300001436b005014f890338280, use the following data to replace **/dev/sdb**:

   **/dev/disk/by-id/scsi-3688860300001436b005014f890338280**
