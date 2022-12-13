:original_name: en-us_topic_0000001174675379.html

.. _en-us_topic_0000001174675379:

CBR
===

What Is CBR?
------------

Cloud Backup and Recovery (CBR) enables you to back up cloud servers and disks with ease. In case of a virus attack, accidental deletion, or software or hardware fault, you can restore data to any point in the past when the data was backed up.

CBR protects your services by ensuring the security and consistency of your data.

Differences Between Cloud Server Backup and Cloud Disk Backup
-------------------------------------------------------------

You can back up ECS data using Cloud Server Backup or Cloud Disk Backup.

-  Cloud Server Backup (recommended): Use this backup function if you want to back up the data of all EVS disks (system and data disks) on an ECS. This prevents data inconsistency caused by time difference in creating a backup.
-  Cloud Disk Backup: Use this backup function if you want to back up the data of one or more EVS disks (system or data disk) on an ECS. This minimizes backup costs on the basis of data security.

.. table:: **Table 1** Differences between cloud server backup and cloud disk backup

   +---------------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Item                                  | Cloud Server Backup                                                              | Cloud Disk Backup                                                                                       |
   +=======================================+==================================================================================+=========================================================================================================+
   | Resources to be backed up or restored | All disks (system and data disks) on a server                                    | One or more specified disks (system or data disks)                                                      |
   +---------------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Recommended scenario                  | An entire cloud server needs to be protected.                                    | Only data disks need to be backed up, because the system disk does not contain users' application data. |
   +---------------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Advantages                            | All disks on a server are backed up at the same time, ensuring data consistency. | Backup cost is reduced without compromising data security.                                              |
   +---------------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
