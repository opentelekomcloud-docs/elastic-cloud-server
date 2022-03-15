Scenarios and Disk Partitions
=============================

If you have added a data disk during ECS creation, you must initialize the data disk after logging in to the ECS.

Scenarios
---------

After a disk is attached to a server, you need to log in to the server to initialize the disk, that is, format the disk. You must initialize a disk before accessing it.

-  System disk

   A system disk does not require manual initialization because it is automatically created and initialized upon server creation. The default disk partition style is master boot record (MBR).

-  Data disk

   -  If a data disk is created along with a server, it will be automatically attached to the server.
   -  If a data disk is created separately, you need to manually attach it to a server.

   In both cases, you must initialize the data disk before using it. Choose a proper disk partition style based on your service plan.

Disk Partition Styles
---------------------

`Table 1 <#ENUSTOPIC0030831623enustopic0085245975table2729705994129>`__ lists the common disk partition styles. In Linux, different disk partition styles require different partitioning tools.



.. _ENUSTOPIC0030831623enustopic0085245975table2729705994129:

.. table:: **Table 1** Disk partition styles

   +----------------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
   | Disk Partition Style       | Maximum Disk Capacity Supported | Maximum Number of Partitions Supported                                                                                                                                                                                                                                     | Linux Partitioning Tool |
   +============================+=================================+============================================================================================================================================================================================================================================================================+=========================+
   | Master Boot Record (MBR)   | 2 TB                            | -  4 primary partitions                                                                                                                                                                                                                                                    | -  fdisk                |
   |                            |                                 | -  3 primary partitions and 1 extended partition                                                                                                                                                                                                                           | -  parted               |
   |                            |                                 |                                                                                                                                                                                                                                                                            |                         |
   |                            |                                 | With MBR, one may create several primary partitions and an extended partition. An extended partition must be divided into several logical partitions before use. For example, if 6 partitions need to be created, you can create the partitions in the following two ways: |                         |
   |                            |                                 |                                                                                                                                                                                                                                                                            |                         |
   |                            |                                 | -  3 primary partitions and 1 extended partition, with the extended partition divided into 3 logical partitions                                                                                                                                                            |                         |
   |                            |                                 | -  1 primary partition and 1 extended partition, with the extended partition divided into 5 logical partitions                                                                                                                                                             |                         |
   +----------------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
   | GUID Partition Table (GPT) | 18 EB                           | Unlimited                                                                                                                                                                                                                                                                  | parted                  |
   |                            |                                 |                                                                                                                                                                                                                                                                            |                         |
   |                            | 1 EB = 1048576 TB               | Disk partitions created using GPT are not categorized.                                                                                                                                                                                                                     |                         |
   +----------------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+

|image1|

The maximum disk capacity supported by MBR is 2 TB, and that supported by GPT is 18 EB. Because a data disk currently supports up to 32 TB, use the GPT partition style if your disk capacity is larger than 2 TB.

If you change the disk partition style after the disk has been used, the data on the disk will be cleared. Therefore, select a proper disk partition style when initializing the disk.



.. |image1| image:: /_static/images/notice_3.0-en-us.png
