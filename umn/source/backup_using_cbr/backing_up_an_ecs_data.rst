:original_name: en-us_topic_0000001128604648.html

.. _en-us_topic_0000001128604648:

Backing Up an ECS Data
======================

Scenarios
---------

CBR enhances data integrity and service continuity. For example, if an ECS or EVS disk is faulty or a misoperation causes data loss, you can use data backups to quickly restore data. This section describes how to back up ECSs and EVS disks.

For more information, :ref:`CBR Architecture <en-us_topic_0000001128445638__section10399144613501>`, :ref:`Backup Mechanism <en-us_topic_0000001128445638__section696712594578>`, and :ref:`Backup Options <en-us_topic_0000001128445638__section533362013>`.

You can back up ECS data using Cloud Server Backup or Cloud Disk Backup.

-  Cloud Server Backup (recommended): Use this backup function if you want to back up the data of all EVS disks (system and data disks) on an ECS. This prevents data inconsistency caused by time difference in creating a backup.
-  Cloud Disk Backup: Use this backup function if you want to back up the data of one or more EVS disks (system or data disk) on an ECS. This minimizes backup costs on the basis of data security.

ECS Backup Procedure
--------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, choose **Elastic Cloud Server**.

#. In the ECS list, locate the row containing the target ECS and choose **More** > **Manage Image/Backup** > **Create Server Backup** in the **Operation** column.

   -  If the ECS has been associated with a vault, configure the backup information as prompted.

      -  **Server List**: The ECS to be backed up is selected by default.
      -  **Name**: Customize your backup name.
      -  **Description**: Supplementary information about the backup.
      -  **Full Backup**: If this option is selected, the system will perform full backup for the ECS to be associated. The storage capacity used by the backup increases accordingly.

   -  If the ECS is not associated with a vault, buy a vault first and then configure the backup information as prompted.

      For details, see `Creating a Server Backup Vault <https://docs.otc.t-systems.com/cloud-backup-recovery/umn/getting_started/step_1_create_a_vault/creating_a_server_backup_vault.html>`__.

#. Click **OK**. The system automatically creates a backup for the ECS.

   On the **Backups** tab page, if the status of the backup is **Available**, the backup task is successful.

   The ECS can be restarted if the backup progress of an ECS exceeds 10%. However, to ensure data integrity, restart it after the backup is complete.

   After the backup is complete, you can restore server data or create images on the **Backups** tab page. For details, see `Restoring from a Cloud Server Backup <https://docs.otc.t-systems.com/cloud-backup-recovery/umn/restoring_data/restoring_from_a_cloud_server_backup.html>`__ and `Using a Backup to Create an Image <https://docs.otc.t-systems.com/cloud-backup-recovery/umn/backup_management/using_a_backup_to_create_an_image.html>`__.

EVS Disk Backup Procedure
-------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select your region and project.

#. Under **Computing**, choose **Elastic Cloud Server**.

#. In the ECS list, locate the row containing the target ECS and choose **More** > **Manage Image/Backup** > **Create Disk Backup** in the **Operation** column.

   -  If the ECS has been associated with a vault, configure the backup information as prompted.

      -  **Server List**: The ECS to be backed up is selected by default. Click |image3| to view the disks attached to the ECSs. Select the disks to be backed up.
      -  **Name**: Customize your backup name.
      -  **Description**: Supplementary information about the backup.
      -  **Full Backup**: If this option is selected, the system will perform full backup for the disks to be associated. The storage capacity used by the backup increases accordingly.

   -  If the ECS is not associated with a vault, buy a vault first and then configure the backup information as prompted.

      For details, see `Creating a Disk Backup Vault <https://docs.otc.t-systems.com/cloud-backup-recovery/umn/getting_started/step_1_create_a_vault/creating_a_disk_backup_vault.html>`__.

#. Click **OK**. The system automatically creates a backup for the disk.

   On the **Backups** tab page, if the status of the backup is **Available**, the backup task is successful.

   If some files are deleted from the disk during the backup, the deleted files may fail to be backed up. Therefore, to ensure data integrity, delete the target data after the backup is complete.

   After the backup is complete, you can restore disk data on the **Backups** tab page. For details, see `Restoring from a Cloud Disk Backup <https://docs.otc.t-systems.com/cloud-backup-recovery/umn/restoring_data/restoring_from_a_cloud_disk_backup.html>`__.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
.. |image2| image:: /_static/images/en-us_image_0210779229.png
.. |image3| image:: /_static/images/en-us_image_0000001128656892.png
