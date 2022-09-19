:original_name: en-us_topic_0085634798.html

.. _en-us_topic_0085634798:

Initializing a Linux Data Disk (parted)
=======================================

Scenarios
---------

This section uses CentOS 7.4 64bit to describe how to initialize a data disk attached to a server running Linux and use parted to partition the data disk.

The maximum partition size that MBR supports is 2 TB and that GPT supports is 18 EB. If the disk size you need to partition is greater than 2 TB, partition the disk using GPT.

The partitioning tool fdisk is suitable only for MBR partitions, and parted is suitable for both MBR and GPT partitions. For more information, see :ref:`Scenarios and Disk Partitions <en-us_topic_0030831623>`.

The method for initializing a disk varies depending on the OS running on the server. This document is used for reference only. For the detailed operations and differences, see the product documents of the corresponding OS.

Prerequisites
-------------

-  A data disk has been attached to a server and has not been initialized.
-  You have logged in to the server.

   -  For how to log in to an ECS, see the *Elastic Cloud Server User Guide*.
   -  For how to log in to a BMS, see the *Bare Metal Server User Guide*.

Creating and Mounting a Partition
---------------------------------

The following example shows you how a new partition can be created on a new data disk that has been attached to a server. The partition will be created using parted, and GPT will be used. Furthermore, the partition will be formatted using the ext4 file system, mounted on **/mnt/sdc**, and configured with automatic mounting at system start.

#. Run the following command to query information about the new data disk:

   **lsblk**

   Information similar to the following is displayed:

   .. code-block::

      root@ecs-test-0001 ~]# lsblk
      NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
      vda    253:0    0   40G  0 disk
      └─vda1 253:1    0   40G  0 part /
      vdb    253:16   0  100G  0 disk

   In the command output, the server contains two disks. **/dev/vda** is the system disk, and **/dev/vdb** is the new data disk.

#. Run the following command to enter parted to partition the new data disk:

   **parted** *New data disk*

   In this example, run the following command:

   **parted /dev/vdb**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# parted /dev/vdb
      GNU Parted 3.1
      Using /dev/vdb
      Welcome to GNU Parted! Type 'help' to view a list of commands.
      (parted)

#. Enter **p** and press **Enter** to view the current disk partition style.

   Information similar to the following is displayed:

   .. code-block::

      (parted) p
      Error: /dev/vdb: unrecognised disk label
      Model: Virtio Block Device (virtblk)
      Disk /dev/vdb: 107GB
      Sector size (logical/physical): 512B/512B
      Partition Table: unknown
      Disk Flags:
      (parted)

   In the command output, the **Partition Table** value is **unknown**, indicating that no partition style is set for the new disk.

#. Run the following command to set the disk partition style:

   **mklabel** *Disk partition style*

   In this example, run the following command to set the partition style to GPT: (Disk partition styles can be MBR or GPT.)

   **mklabel gpt**

   .. important::

      The maximum disk capacity supported by MBR is 2 TB, and that supported by GPT is 18 EB. Because a data disk currently supports up to 32 TB, use the GPT partition style if your disk capacity is larger than 2 TB.

      If you change the disk partition style after the disk has been used, the data on the disk will be cleared. Therefore, select a proper disk partition style when initializing the disk.

#. Enter **p** and press **Enter** to view the disk partition style.

   Information similar to the following is displayed:

   .. code-block::

      (parted) mklabel gpt
      (parted) p
      Model: Virtio Block Device (virtblk)
      Disk /dev/vdb: 107GB
      Sector size (logical/physical): 512B/512B
      Partition Table: gpt
      Disk Flags:

      Number  Start  End  Size  File system  Name  Flags

      (parted)

   In the command output, the **Partition Table** value is **gpt**, indicating that the disk partition style is GPT.

#. Enter **unit s** and press **Enter** to set the measurement unit of the disk to sector.

#. Run the following command and press **Enter**:

   **mkpart** *Partition name Start sector* *End sector*

   In this example, run the following command:

   **mkpart test 2048s 100%**

   In this example, one partition is created for the new data disk. Variable *2048s* indicates the disk start sector, and variable *100%* indicates the disk end sector. The two values are used for reference only. You can determine the number of partitions and the partition size based on your service requirements.

   Information similar to the following is displayed:

   .. code-block::

      (parted) mkpart opt 2048s 100%
      (parted)

#. Enter **p** and press **Enter** to view details about the new partition.

   Information similar to the following is displayed:

   .. code-block::

      (parted) p
      Model: Virtio Block Device (virtblk)
      Disk /dev/vdb: 209715200s
      Sector size (logical/physical): 512B/512B
      Partition Table: gpt
      Disk Flags:

      Number  Start  End         Size        File system  Name  Flags
       1      2048s  209713151s  209711104s               test

      (parted)

#. Enter **q** and press **Enter** to exit parted.

   Information similar to the following is displayed:

   .. code-block::

      (parted) q
      Information: You may need to update /etc/fstab.

   You can set automatic disk mounting by updating the **/etc/fstab** file. Before updating the file, set the file system format for the partition and mount the partition on the mount point.

#. Run the following command to view the disk partition information:

   **lsblk**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# lsblk
      NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
      vda    253:0    0   40G  0 disk
      └─vda1 253:1    0   40G  0 part /
      vdb    253:16   0  100G  0 disk
      └─vdb1 253:17   0  100G  0 part

   In the command output, **/dev/vdb1** is the partition you created.

#. Run the following command to set the file system format for the new partition:

   **mkfs** **-t** *File system format* **/dev/vdb1**

   In this example, run the following command to set the **ext4** file system for the new partition:

   **mkfs -t ext4 /dev/vdb1**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# mkfs -t ext4 /dev/vdb1
      mke2fs 1.42.9 (28-Dec-2013)
      Filesystem label=
      OS type: Linux
      Block size=4096 (log=2)
      Fragment size=4096 (log=2)
      Stride=0 blocks, Stripe width=0 blocks
      6553600 inodes, 26213888 blocks
      1310694 blocks (5.00%) reserved for the super user
      First data block=0
      Maximum filesystem blocks=2174746624
      800 block groups
      32768 blocks per group, 32768 fragments per group
      8192 inodes per group
      Superblock backups stored on blocks:
              32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
              4096000, 7962624, 11239424, 20480000, 23887872

      Allocating group tables: done
      Writing inode tables: done
      Creating journal (32768 blocks): done
      Writing superblocks and filesystem accounting information: done

   The formatting takes a period of time. Observe the system running status and do not exit.

   .. important::

      The partition sizes supported by file systems vary. Therefore, you are advised to choose an appropriate file system based on your service requirements.

#. Run the following command to create a mount point:

   **mkdir** *Mount point*

   In this example, run the following command to create the **/mnt/sdc** mount point:

   **mkdir /mnt/sdc**

   .. note::

      The **/mnt** directory exists on all Linux systems. If the mount point fails to create, it may be that the **/mnt** directory has been accidentally deleted. Run the **mkdir -p /mnt/sdc** command to create the mount point.

#. Run the following command to mount the new partition on the created mount point:

   **mount** *Disk partition* *Mount point*

   In this example, run the following command to mount the new partition **/dev/vdb1** on **/mnt/sdc**:

   **mount /dev/vdb1 /mnt/sdc**

#. Run the following command to view the mount result:

   **df -TH**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# df -TH
      Filesystem     Type      Size  Used Avail Use% Mounted on
      /dev/vda1      ext4       43G  1.9G   39G   5% /
      devtmpfs       devtmpfs  2.0G     0  2.0G   0% /dev
      tmpfs          tmpfs     2.0G     0  2.0G   0% /dev/shm
      tmpfs          tmpfs     2.0G  9.0M  2.0G   1% /run
      tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
      tmpfs          tmpfs     398M     0  398M   0% /run/user/0
      /dev/vdb1      ext4      106G   63M  101G   1% /mnt/sdc

   New partition **/dev/vdb1** is mounted on **/mnt/sdc**.

   .. note::

      If the server is restarted, the mounting will become invalid. You can set automatic mounting for partitions at system start by modifying the **/etc/fstab** file. For details, see :ref:`Setting Automatic Mounting at System Start <en-us_topic_0085634798__en-us_topic_0084935709_section15839912195453>`.

.. _en-us_topic_0085634798__en-us_topic_0084935709_section15839912195453:

Setting Automatic Mounting at System Start
------------------------------------------

Modify the **fstab** file to set automatic disk mounting at server start. You can also set automatic mounting for the servers containing data. This operation will not affect the existing data.

The following procedure shows how to set automatic disk mounting at server start by using UUIDs to identify disks in the **fstab** file. You are advised not to use device names to identify disks in the file because a device name may change (for example, from /dev/vdb1 to /dev/vdb2) during the server stop or start, resulting in improper server running after restart.

.. note::

   UUID is the unique character string for disk partitions in a Linux system.

#. Run the following command to query the partition UUID:

   **blkid** *Disk partition*

   In this example, run the following command to query the UUID of the **/dev/vdb1** partition:

   **blkid /dev/vdb1**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# blkid /dev/vdb1
      /dev/vdb1: UUID="0b3040e2-1367-4abb-841d-ddb0b92693df" TYPE="ext4"

   The UUID of the **/dev/vdb1** partition is displayed.

#. Run the following command to open the **fstab** file using the vi editor:

   **vi /etc/fstab**

#. Press **i** to enter editing mode.

#. Move the cursor to the end of the file and press **Enter**. Then, add the following information:

   .. code-block::

      UUID=0b3040e2-1367-4abb-841d-ddb0b92693df /mnt/sdc                ext4    defaults        0 2

#. Press **Esc**, enter **:wq**, and press **Enter**.

   The system saves the configurations and exits the vi editor.

#. Perform the following operations to verify the automatic mounting function:

   a. Run the following command to unmount the partition:

      **umount** *Disk partition*

      In this example, run the following command:

      **umount /dev/vdb1**

   b. Run the following command to reload all the content in the **/etc/fstab** file:

      **mount -a**

   c. Run the following command to query the file system mounting information:

      **mount** **\|** **grep** *Mount point*

      In this example, run the following command:

      **mount** **\|** **grep** **/mnt/sdc**

      If information similar to the following is displayed, automatic mounting has been configured:

      .. code-block::

         root@ecs-test-0001 ~]# mount | grep /mnt/sdc
         /dev/vdb1 on /mnt/sdc type ext4 (rw,relatime,data=ordered)
