:original_name: en-us_topic_0078300750.html

.. _en-us_topic_0078300750:

How Can I Add the Empty Partition of an Expanded System Disk to the Non-end Root Partition Online?
==================================================================================================

Scenarios
---------

If the capacity of system disk partitions is inconsistent with the actual system disk capacity after an ECS is created, you can add the empty partition to the root partition of the system disk.

This section describes how to add the empty partition to the non-end root partition online.

Procedure
---------

In the following operations, the ECS that runs CentOS 6.5 64bit and has a 100 GB system disk is used as an example. The system disk has two partitions, **/dev/xvda1: root** and **/dev/xvda2: swap**, and the root partition is not the end partition.

#. Run the following command to view disk partitions:

   **parted -l /dev/xvda**

   .. code-block:: console

      [root@sluo-ecs-a611 ~]# parted -l /dev/xvda
      Disk /dev/xvda: 107GB
      Sector size (logical/physical): 512B/512B
      Partition Table: msdos
      Disk Flags:

      Number  Start   End     Size    Type     File system     Flags
       1      1049kB  41.0GB  40.9GB  primary  ext4            boot
       2      41.0GB  42.9GB  2000MB  primary  linux-swap(v1)

   The first is the root partition, and the second is the swap partition.

#. View and edit the fstab partition table to delete the swap partition attaching information.

   a. Run the following command to view the fstab partition table:

      **tail -n 3 /etc/fstab**

      .. code-block:: console

         [root@sluo-ecs-a611 ~]# tail -n 3 /etc/fstab
         #
         UUID=7c4fce5d-f8f7-4ed6-8463-f2bd22d0ddea /                       ext4    defaults        1 1
         UUID=5de3cf2c-30c6-4fb2-9e63-830439d4e674 swap                    swap    defaults        0 0

   b. Run the following command to edit the fstab partition table and delete the swap partition attaching information.

      **vi /etc/fstab**

      **tail -n 3 /etc/fstab**

      .. code-block:: console

         [root@sluo-ecs-a611 ~]# vi /etc/fstab
         [root@sluo-ecs-a611 ~]# tail -n 3 /etc/fstab
         #
         UUID=7c4fce5d-f8f7-4ed6-8463-f2bd22d0ddea /                       ext4    defaults        1 1

#. Run the following command to disable the swap partition:

   **swapoff -a**

#. Delete the swap partition.

   a. Run the following command to view the partition:

      **parted /dev/xvda**

      .. code-block:: console

         [root@sluo-ecs-a611 ~]# parted /dev/xvda
         GNU Parted 3.1
         Using /dev/xvda
         Welcome to GNU Parted! Type ´help´ to view a list of commands.
         (parted) help
           align-check TYPE N                        check partition N for TYPE(min|opt) alignment
           help [COMMAND]                           print general help, or help on COMMAND
           mklabel,mktable LABEL-TYPE               create a new disklabel (partition table)
           mkpart PART-TYPE [FS-TYPE] START END     make a partition
           name NUMBER NAME                         name partition NUMBER as NAME
           print [devices|free|list,all|NUMBER]     display the partition table, available devices, free space, all found partitions, or a
                 particular partition
           quit                                     exit program
           rescue START END                         rescue a lost partition near START and END
           rm NUMBER                                delete partition NUMBER
           select DEVICE                            choose the device to edit
           disk_set FLAG STATE                      change the FLAG on selected device
           disk_toggle [FLAG]                       toggle the state of FLAG on selected device
           set NUMBER FLAG STATE                    change the FLAG on partition NUMBER
           toggle [NUMBER [FLAG]]                   toggle the state of FLAG on partition NUMBER
           unit UNIT                                set the default unit to UNIT
           version                                  display the version number and copyright information of GNU Parted
         (parted)

   b. Press **p**.

      .. code-block::

         Disk /dev/xvda: 107GB
         Sector size (logical/physical): 512B/512B
         Partition Table: msdos
         Disk Flags:

         Number  Start   End     Size    Type     File system     Flags
          1      1049kB  41.0GB  40.9GB  primary  ext4            boot
          2      41.0GB  42.9GB  2000MB  primary  linux-swap(v1)


   c. Run the following command to delete the partition:

      **rm 2**

      .. code-block::

         (parted) rm2

   d. Press **p**.

      .. code-block::

         (parted) p
         Disk /dev/xvda: 107GB
         Sector size (logical/physical): 512B/512B
         Partition Table: msdos
         Disk Flags:

         Number  Start   End     Size    Type     File system  Flags
          1      1049kB  41.0GB  40.9GB  primary  ext4         boot

   e. Run the following command to edit the fstab partition table:

      **quit**

      .. code-block::

         (parted) quit
         Information: You may need to update /etc/fstab.

#. Run the following command to view partition after the swap partition is deleted:

   **parted -l /dev/xvda**

   .. code-block:: console

      [root@sluo-ecs-a611 ~]# parted -l /dev/xvda
      Disk /dev/xvda: 107GB
      Sector size (logical/physical): 512B/512B
      Partition Table: msdos
      Disk Flags:

      Number  Start   End     Size    Type     File system  Flags
       1      1049kB  41.0GB  40.9GB  primary  ext4         boot

#. Run the following command to install the growpart tool:

   This tool may be integrated in the **cloud-utils-growpart/cloud-utils/cloud-initramfs-tools/cloud-init** package. Run the **yum install cloud-\*** command to ensure it is available.

   **yum install cloud-utils-growpart**

#. Run the following command to expand the root partition (the first partition) using growpart:

   **growpart /dev/xvda 1**

   .. code-block:: console

      [root@sluo-ecs-a611 ~]# growpart /dev/xvda 1
      CHANGED: partition=1 start=2048 old: size=79978496 end=79980544 new: size=209710462,end=209712510

#. Run the following command to verify that online capacity expansion is successful:

   .. code-block:: console

      [root@sluo-ecs-a611 ~]# parted -l /dev/xvda
      Disk /dev/xvda: 107GB
      Sector size (logical/physical): 512B/512B
      Partition Table: msdos
      Disk Flags:

      Number  Start   End    Size   Type     File system  Flags
       1      1049kB  107GB  107GB  primary  ext4         boot

#. Run the following command to expand the capacity of the file system:

   **resize2fs -f $Partition name**

   Suppose the partition name is **/dev/xvda1**, run the following command:

   .. code-block:: console

      [root@sluo-ecs-a611 ~]# resize2fs -f /dev/xvda1
      resize2fs 1.42.9 (28-Dec-2013)
      Filesystem at /dev/xvda1 is mounted on /; on-line resizing required
      old_desc_blocks = 3, new_desc_blocks = 3
      ....
      [root@sluo-ecs-a611 ~] # df -hT     //Check file system capacity expansion
