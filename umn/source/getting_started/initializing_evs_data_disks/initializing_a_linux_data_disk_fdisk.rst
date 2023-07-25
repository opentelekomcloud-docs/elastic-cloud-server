:original_name: en-us_topic_0085634797.html

.. _en-us_topic_0085634797:

Initializing a Linux Data Disk (fdisk)
======================================

Scenarios
---------

This section uses CentOS 7.4 64bit to describe how to initialize a data disk attached to a server running Linux and use fdisk to partition the data disk.

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

The following example shows you how a new primary partition can be created on a new data disk that has been attached to a server. The primary partition will be created using fdisk, and MBR will be used. Furthermore, the partition will be formatted using the ext4 file system, mounted on **/mnt/sdc**, and configured to mount automatically at startup.

#. Query what block devices are available on the server.

   **fdisk -l**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# fdisk -l

      Disk /dev/vda: 42.9 GiB, 42949672960 bytes, 83886080 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x000bcb4e

         Device Boot      Start         End      Blocks   Id  System
      /dev/vda1   *        2048    83886079    41942016   83  Linux

      Disk /dev/vdb: 107.4 GiB, 107374182400 bytes, 209715200 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes

   In the command output, this server contains two disks. **/dev/vda** and **/dev/vdb**. **/dev/vda** is the system disk, and **/dev/vdb** is the new data disk.

#. Launch fdisk to partition the new data disk.

   **fdisk** *New data disk*

   In this example, run the following command:

   **fdisk /dev/vdb**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# fdisk /dev/vdb
      Welcome to fdisk (util-linux 2.23.2).

      Changes will remain in memory only, until you decide to write them.
      Be careful before using the write command.

      Device does not contain a recognized partition table
      Building a new DOS disklabel with disk identifier 0x38717fc1.

      Command (m for help):

#. Enter **n** and press **Enter** to create a new partition.

   Information similar to the following is displayed:

   .. code-block::

      Command (m for help): n
      Partition type:
         p   primary (0 primary, 0 extended, 4 free)
         e   extended

   There are two types of disk partitions:

   -  Choosing **p** creates a primary partition.
   -  Choosing **e** creates an extended partition.

   .. note::

      If the MBR partition style is used, a maximum of 4 primary partitions, or 3 primary partitions and 1 extended partition can be created. The extended partition cannot be used directly and must be divided into logical partitions before use.

      Disk partitions created using GPT are not categorized.

#. Enter **p** and press **Enter** to create a primary partition in this example.

   Information similar to the following is displayed:

   .. code-block::

      Select (default p): p
      Partition number (1-4, default 1):

   **Partition number** indicates the serial number of the primary partition. The value ranges from **1** to **4**.

#. Enter the serial number of the primary partition and press **Enter**. Primary partition number **1** is used in this example. One usually starts with partition number **1** when partitioning an empty disk.

   Information similar to the following is displayed:

   .. code-block::

      Partition number (1-4, default 1): 1
      First sector (2048-209715199, default 2048):

   **First sector** indicates the start sector. The value ranges from **2048** to **209715199**, and the default value is **2048**.

#. Select the default start sector **2048** and press **Enter**.

   The system displays the start and end sectors of the partition's available space. You can customize the value within this range or use the default value. The start sector must be smaller than the partition's end sector.

   Information similar to the following is displayed:

   .. code-block::

      First sector (2048-209715199, default 2048):
      Using default value 2048
      Last sector, +sectors or +size{K,M,G} (2048-209715199, default 209715199):

   **Last sector** indicates the end sector. The value ranges from **2048** to **209715199**, and the default value is **209715199**.

#. Select the default end sector **209715199** and press **Enter**.

   The system displays the start and end sectors of the partition's available space. You can customize the value within this range or use the default value. The start sector must be smaller than the partition's end sector.

   Information similar to the following is displayed:

   .. code-block::

      Last sector, +sectors or +size{K,M,G} (2048-209715199, default 209715199):
      Using default value 209715199
      Partition 1 of type Linux and of size 100 GiB is set

      Command (m for help):

   A primary partition has been created for the new data disk.

#. Enter **p** and press **Enter** to print the partition details.

   Information similar to the following is displayed:

   .. code-block::

      Command (m for help): p

      Disk /dev/vdb: 107.4 GiB, 107374182400 bytes, 209715200 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x38717fc1

         Device Boot      Start         End      Blocks   Id  System
      /dev/vdb1            2048   209715199   104856576   83  Linux

      Command (m for help):

   Details about the **/dev/vdb1** partition are displayed.

#. Enter **w** and press **Enter** to write the changes to the partition table.

   Information similar to the following is displayed:

   .. code-block::

      Command (m for help): w
      The partition table has been altered!

      Calling ioctl() to re-read partition table.
      Syncing disks.

   The partition is created.

   .. note::

      In case that you want to discard the changes made before, you can exit fdisk by entering **q**.

#. Synchronize the new partition table to the OS.

   **partprobe**

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
      6553600 inodes, 26214144 blocks
      1310707 blocks (5.00%) reserved for the super user
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
      tmpfs          tmpfs     2.0G  9.1M  2.0G   1% /run
      tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
      tmpfs          tmpfs     398M     0  398M   0% /run/user/0
      /dev/vdb1      ext4      106G   63M  101G   1% /mnt/sdc

   You should now see that partition **/dev/vdb1** is mounted on **/mnt/sdc**.

   .. note::

      After the server is restarted, the disk will not be automatically mounted. To configure automount at startup, you will need to modify the **/etc/fstab** file. For details, see :ref:`Configuring Automatic Mounting at System Start <en-us_topic_0085634797__en-us_topic_0044524669_section15839912195453>`.

.. _en-us_topic_0085634797__en-us_topic_0044524669_section15839912195453:

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
