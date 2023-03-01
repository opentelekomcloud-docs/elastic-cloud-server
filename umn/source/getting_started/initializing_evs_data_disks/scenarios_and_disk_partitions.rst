:original_name: en-us_topic_0030831623.html

.. _en-us_topic_0030831623:

Scenarios and Disk Partitions
=============================

If you have added a data disk during ECS creation, you must initialize the data disk after logging in to the ECS.

Scenarios
---------

After a disk is attached to a server, you need to log in to the server to initialize the disk, that is, format the disk. You must initialize a disk before accessing it.

-  System disk

   A system disk does not require manual initialization because it is automatically created and initialized upon server creation. The default partition style is master boot record (MBR).

-  Data disk

   -  If a data disk is created along with a server, it will be automatically attached to the server.
   -  If a data disk is created separately, you need to manually attach it to a server.

   In both cases, you must initialize the data disk before using it. Choose an appropriate partition style based on your service plan.

Partitioning Operation Guide
----------------------------

:ref:`Table 1 <en-us_topic_0030831623__en-us_topic_0085245975_table2729705994129>` lists the common disk partition styles. In Linux, different disk partition styles require different partitioning tools.

.. _en-us_topic_0030831623__en-us_topic_0085245975_table2729705994129:

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
