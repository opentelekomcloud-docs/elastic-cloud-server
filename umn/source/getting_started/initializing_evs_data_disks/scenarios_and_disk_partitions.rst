:original_name: en-us_topic_0030831623.html

.. _en-us_topic_0030831623:

Scenarios and Disk Partitions
=============================

If you have added a data disk during ECS creation, you must initialize the data disk after logging in to the ECS.

Scenarios
---------

After a disk is attached to a server, you need to log in to the server to initialize the disk, that is, format the disk. You must initialize a disk before accessing it.

-  System disk

   A system disk does not require manual initialization because it is automatically created and initialized upon the server creation. The default partition style is master boot record (MBR).

-  Data disk

   -  If a data disk is created along with a server, it will be automatically attached to the server.
   -  If a data disk is created separately, you need to manually attach it to a server.

   In both cases, you must initialize the data disk before using it. Choose an appropriate partition style based on your service plan.

Notes and Constraints
---------------------

-  A disk created from a data source does not need to be initialized. Such a disk contains the source data in the beginning. Initializing the disk may clear the initial data on it.
-  Initializing a disk does not change the server's IP address or the disk ID.
-  Initializing a disk does not delete the snapshots created for the disk, so you can still use snapshots to roll back data to the source disk after the disk is initialized.

Disk Partition Styles
---------------------

:ref:`Table 1 <en-us_topic_0030831623__en-us_topic_0000002015294542_en-us_topic_0000001855947921_en-us_topic_0000001808490252_table2729705994129>` lists the common disk partition styles. In Linux, different partition styles require different partitioning tools.

.. _en-us_topic_0030831623__en-us_topic_0000002015294542_en-us_topic_0000001855947921_en-us_topic_0000001808490252_table2729705994129:

.. table:: **Table 1** Disk partition styles

   +----------------------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
   | Disk Partition Style       | Maximum Disk Capacity Supported | Maximum Number of Partitions Supported                                                                                                                                                                                                                     | Linux Partitioning Tool |
   +============================+=================================+============================================================================================================================================================================================================================================================+=========================+
   | Master Boot Record (MBR)   | 2 TiB                           | -  4 primary partitions                                                                                                                                                                                                                                    | -  fdisk                |
   |                            |                                 | -  3 primary partitions and 1 extended partition                                                                                                                                                                                                           | -  parted               |
   |                            |                                 |                                                                                                                                                                                                                                                            |                         |
   |                            |                                 | With MBR, you can create several primary partitions and one extended partition. The extended partition must be divided into logical partitions before use. For example, if 6 partitions need to be created, you can create them in the following two ways: |                         |
   |                            |                                 |                                                                                                                                                                                                                                                            |                         |
   |                            |                                 | -  3 primary partitions and 1 extended partition, with the extended partition divided into 3 logical partitions                                                                                                                                            |                         |
   |                            |                                 | -  1 primary partition and 1 extended partition, with the extended partition divided into 5 logical partitions                                                                                                                                             |                         |
   +----------------------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
   | GUID Partition Table (GPT) | 18 EiB                          | Unlimited                                                                                                                                                                                                                                                  | parted                  |
   |                            |                                 |                                                                                                                                                                                                                                                            |                         |
   |                            | 1 EiB = 1048576 TiB             | Disk partitions created using GPT are not categorized.                                                                                                                                                                                                     |                         |
   +----------------------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+

.. important::

   The maximum disk size supported by MBR is 2 TiB, and that supported by GPT is 18 EiB. Because an EVS data disk currently supports up to 32 TiB, use GPT if your disk size is greater than 2 TiB.

   If the partition style is changed after the disk has been used, all data on the disk will be lost, so take care to select an appropriate partition style when initializing the disk. If you must change the partition style to GPT after a disk has been used, it is recommended that you back up the disk data before the change.
