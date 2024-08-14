:original_name: en-us_topic_0085634798.html

.. _en-us_topic_0085634798:

Initializing a Linux Data Disk (parted)
=======================================

Scenarios
---------

This section uses CentOS 7.4 64bit to describe how to initialize a data disk attached to a server running Linux and use parted to partition the data disk.

The maximum partition size that MBR supports is 2 TiB and that GPT supports is 18 EiB. If the disk size you need to partition is greater than 2 TiB, partition the disk using GPT.

The fdisk partitioning tool is suitable only for MBR partitions, and the parted partitioning tool is suitable for both MBR and GPT partitions. For more information, see :ref:`Scenarios and Disk Partitions <en-us_topic_0030831623>`.

The method for initializing a disk varies slightly depending on the OS running on the server. This document is used for reference only. For the detailed operations and differences, see the product documents of the corresponding OS.

.. important::

   When using a disk for the first time, if you have not initialized it, including creating partitions and file systems, the additional space added to this disk in an expansion later may not be normally used.

Prerequisites
-------------

-  A data disk has been attached to a server and has not been initialized.
-  You have logged in to the server.

   -  For how to log in to an ECS, see the *Elastic Cloud Server User Guide*.
   -  For how to log in to a BMS, see the *Bare Metal Server User Guide*.

Creating and Mounting a Partition
---------------------------------

The following example shows you how a new partition can be created on a new data disk that has been attached to a server. The partition will be created using parted, and GPT will be used. Furthermore, the partition will be formatted using the ext4 file system, mounted on **/mnt/sdc**, and configured to mount automatically at startup.

#. Query information about the new data disk.

   **lsblk**

   Information similar to the following is displayed:

   .. code-block::

      root@ecs-test-0001 ~]# lsblk
      NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
      vda    253:0    0   40G  0 disk
      └─vda1 253:1    0   40G  0 part /
      vdb    253:16   0  100G  0 disk

   In the command output, this server contains two disks. **/dev/vda** and **/dev/vdb**. **/dev/vda** is the system disk, and **/dev/vdb** is the new data disk.

#. Launch parted to partition the new data disk.

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
      Disk /dev/vdb: 107GiB
      Sector size (logical/physical): 512B/512B
      Partition Table: unknown
      Disk Flags:
      (parted)

   In the command output, the **Partition Table** value is **unknown**, indicating that no partition style is set for the new disk.

#. Set the disk partition style.

   **mklabel** *Disk partition style*

   This command lets you control whether to use MBR or GPT for your partition table. In this example, GPT is used.

   **mklabel gpt**

   .. important::

      The maximum disk size supported by MBR is 2 TiB, and that supported by GPT is 18 EiB. Because an EVS data disk currently supports up to 32 TiB, use GPT if your disk size is larger than 2 TiB.

      If the partition style is changed after the disk has been used, all data on the disk will be lost, so take care to select an appropriate partition style when initializing the disk. If you must change the partition style to GPT after a disk has been used, it is recommended that you back up the disk data before the change.

#. Enter **p** and press **Enter** to view the disk partition style.

   Information similar to the following is displayed:

   .. code-block::

      (parted) mklabel gpt
      (parted) p
      Model: Virtio Block Device (virtblk)
      Disk /dev/vdb: 107GiB
      Sector size (logical/physical): 512B/512B
      Partition Table: gpt
      Disk Flags:

      Number  Start  End  Size  File system  Name  Flags

      (parted)

   In the command output, the **Partition Table** value is **gpt**, indicating that the disk partition style is GPT.

#. Enter **unit s** and press **Enter** to set the measurement unit of the disk to sector.

#. Create a new partition.

   **mkpart** *Partition name Start sector* *End sector*

   In this example, run the following command:

   **mkpart test 2048s 100%**

   In this example, one partition is created for the new data disk, starting on **2048** and using **100%** of the rest of the disk. The two values are used for reference only. You can determine the number of partitions and the partition size based on your service requirements.

   Information similar to the following is displayed:

   .. code-block::

      (parted) mkpart opt 2048s 100%
      (parted)

#. Enter **p** and press **Enter** to print the partition details.

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

   You can configure automatic mounting by updating the **/etc/fstab** file. Before doing so, format the partition with a desired file system and mount the partition on the mount point.

#. View the disk partition information.

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

#. Format the new partition with a desired file system format.

   **mkfs** **-t** *File system format* **/dev/vdb1**

   In this example, the **ext4** format is used for the new partition.

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

      The partition sizes supported by file systems vary. Choose an appropriate file system format based on your service requirements.

#. Create a mount point.

   **mkdir** *Mount point*

   In this example, the **/mnt/sdc** mount point is created.

   **mkdir /mnt/sdc**

   .. note::

      The **/mnt** directory exists on all Linux systems. If the mount point cannot be created, it may be that the **/mnt** directory has been accidentally deleted. You can run **mkdir -p /mnt/sdc** to create the mount point.

#. Mount the new partition on the created mount point.

   **mount** *Disk partition* *Mount point*

   In this example, the **/dev/vdb1** partition is mounted on **/mnt/sdc**.

   **mount /dev/vdb1 /mnt/sdc**

#. Check the mount result.

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

   You should now see that partition **/dev/vdb1** is mounted on **/mnt/sdc**.

   .. note::

      After the server is restarted, the disk will not be automatically mounted. To configure automount at startup, you will need to modify the **/etc/fstab** file. For details, see :ref:`Configuring Automatic Mounting at System Start <en-us_topic_0085634798__en-us_topic_0084935709_section15839912195453>`.

.. _en-us_topic_0085634798__en-us_topic_0084935709_section15839912195453:

Configuring Automatic Mounting at System Start
----------------------------------------------

The **fstab** file controls what disks are automatically mounted at startup. You can use **fstab** to configure your data disks to mount automatically. This operation will not affect the existing data.

The example here uses UUIDs to identify disks in the **fstab** file. You are advised not to use device names to identify disks in the file because device names are assigned dynamically and may change (for example, from /dev/vdb1 to /dev/vdb2) after a reboot. This can even prevent your disk from booting up.

.. note::

   UUID is the unique character string for disk partitions in a Linux system.

#. Query the partition UUID.

   **blkid** *Disk partition*

   In this example, the UUID of the **/dev/vdb1** partition is queried.

   **blkid /dev/vdb1**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# blkid /dev/vdb1
      /dev/vdb1: UUID="0b3040e2-1367-4abb-841d-ddb0b92693df" TYPE="ext4"

   Carefully record the UUID, as you will need it for the following step.

#. Open the **fstab** file using the vi editor.

   **vi /etc/fstab**

#. Press **i** to enter editing mode.

#. Move the cursor to the end of the file and press **Enter**. Then, add the following information:

   .. code-block::

      UUID=0b3040e2-1367-4abb-841d-ddb0b92693df /mnt/sdc                ext4    defaults        0 2

#. Press **Esc**, enter **:wq**, and press **Enter**.

   The system saves the configurations and exits the vi editor.

#. Verify that the disk is auto-mounted at startup.

   a. Unmount the partition.

      **umount** *Disk partition*

      In this example, run the following command:

      **umount /dev/vdb1**

   b. Reload all the content in the **/etc/fstab** file.

      **mount -a**

   c. Query the file system mounting information.

      **mount** **\|** **grep** *Mount point*

      In this example, run the following command:

      **mount** **\|** **grep** **/mnt/sdc**

      If information similar to the following is displayed, automatic mounting has been configured:

      .. code-block::

         root@ecs-test-0001 ~]# mount | grep /mnt/sdc
         /dev/vdb1 on /mnt/sdc type ext4 (rw,relatime,data=ordered)
