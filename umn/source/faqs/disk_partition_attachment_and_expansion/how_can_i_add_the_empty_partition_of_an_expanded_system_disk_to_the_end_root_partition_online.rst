:original_name: en-us_topic_0078300749.html

.. _en-us_topic_0078300749:

How Can I Add the Empty Partition of an Expanded System Disk to the End Root Partition Online?
==============================================================================================

Scenarios
---------

If the capacity of system disk partitions is inconsistent with the actual system disk capacity after an ECS is created, you can add the empty partition to the root partition of the system disk.

This section describes how to add the empty partition to the end root partition online.

Procedure
---------

In the following operations, the ECS that runs CentOS 6.5 64bit and has a 50 GB system disk is used as an example. The system disk has two partitions, **/dev/xvda1: swap** and **/dev/xvda2: root**, and the root partition is the end partition.

#. Run the following command to view disk partitions:

   **parted -l /dev/xvda**

   .. code-block:: console

      [root@sluo-ecs-5e7d ~]# parted -l /dev/xvda
      Disk /dev/xvda: 53.7GB
      Sector size (logical/physical): 512B/512B
      Partition Table: msdos

      Number  Start   End     Size    Type     File system     Flags
       1      1049kB  4296MB  4295MB  primary  linux-swap(v1)
       2      4296MB  42.9GB  38.7GB  primary  ext4            boot

#. Run the following command to obtain the file system type and UUID:

   **blkid**

   .. code-block::

      /dev/xvda1: UUID="25ec3bdb-ba24-4561-bcdc-802edf42b85f" TYPE="swap"
      /dev/xvda2: UUID="1a1ce4de-e56a-4e1f-864d-31b7d9dfb547" TYPE="ext4"

#. Run the following command to install the growpart tool:

   This tool may be integrated in the **cloud-utils-growpart/cloud-utils/cloud-initramfs-tools/cloud-init** package. Run the **yum install cloud-\*** command to ensure it is available.

   **yum install cloud-utils-growpart**

#. Run the following command to expand the root partition (the second partition) using growpart:

   **growpart /dev/xvda 2**

   .. code-block:: console

      [root@sluo-ecs-5e7d ~]# growpart /dev/xvda 2
      CHANGED: partition=2 start=8390656 old: size=75495424 end=83886080 new: size=96465599,end=104856255

#. Run the following command to verify that online capacity expansion is successful:

   **parted -l /dev/xvda**

   .. code-block:: console

      [root@sluo-ecs-5e7d ~]# parted -l /dev/xvda
      Disk /dev/xvda: 53.7GB
      Sector size (logical/physical): 512B/512B
      Partition Table: msdos

      Number  Start   End     Size    Type     File system     Flags
       1      1049kB  4296MB  4295MB  primary  linux-swap(v1)
       2      4296MB  53.7GB  49.4GB  primary  ext4            boot

#. Run the following command to expand the capacity of the file system:

   **resize2fs -f $Partition name**

   Suppose the partition name is **/dev/xvda2**, run the following command:

   .. code-block:: console

      [root@sluo-ecs-a611 ~]# resize2fs -f /dev/xvda2
      resize2fs 1.42.9 (28-Dec-2013)
      Filesystem at /dev/xvda2 is mounted on /; on-line resizing required
      old_desc_blocks = 3, new_desc_blocks = 3
      ....
      [root@sluo-ecs-a611 ~] # df -hT    //Check file system capacity expansion
