Initializing a Linux Data Disk (fdisk)
======================================

Scenarios
---------

This section uses CentOS 7.4 64bit to describe how to initialize a data disk attached to a server running Linux and use fdisk to partition the data disk.

The maximum disk capacity supported by MBR is 2 TB, and that supported by GPT is 18 EB. Therefore, use the GPT partition style if your disk capacity is larger than 2 TB. In Linux, if you choose to use the GPT partition style, the fdisk partitioning tool cannot be used. Use the parted partitioning tool instead. For details about disk partition styles, see `Scenarios and Disk Partitions <en-us_topic_0030831623.html>`__.

The method for initializing a disk varies depending on the OS running on the server. This document is used for reference only. For the detailed operations and differences, see the product documents of the corresponding OS.

Prerequisites
-------------

-  A data disk has been attached to a server and has not been initialized.
-  You have logged in to the server.

   -  For how to log in to an ECS, see the *Elastic Cloud Server User Guide*.
   -  For how to log in to a BMS, see the *Bare Metal Server User Guide*.

Creating and Mounting a Partition
---------------------------------

The following example shows you how a new primary partition can be created on a new data disk that has been attached to a server. The primary partition will be created using fdisk, and MBR is the default partition style. Furthermore, the partition will be formatted using the ext4 file system, mounted on **/mnt/sdc**, and configured with automatic mounting at system start.

#. Run the following command to query information about the new data disk:

   **fdisk -l**

   Information similar to the following is displayed:

   .. code::

      [root@ecs-test-0001 ~]# fdisk -l

      Disk /dev/vda: 42.9 GB, 42949672960 bytes, 83886080 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x000bcb4e

         Device Boot      Start         End      Blocks   Id  System
      /dev/vda1   *        2048    83886079    41942016   83  Linux

      Disk /dev/vdb: 107.4 GB, 107374182400 bytes, 209715200 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes

   In the command output, the server contains two disks. **/dev/vda** is the system disk, and **/dev/vdb** is the new data disk.

#. Run the following command to enter fdisk to partition the new data disk:

   **fdisk** *New data disk*

   In this example, run the following command:

   **fdisk /dev/vdb**

   Information similar to the following is displayed:

   .. code::

      [root@ecs-test-0001 ~]# fdisk /dev/vdb
      Welcome to fdisk (util-linux 2.23.2).

      Changes will remain in memory only, until you decide to write them.
      Be careful before using the write command.

      Device does not contain a recognized partition table
      Building a new DOS disklabel with disk identifier 0x38717fc1.

      Command (m for help): 

#. Enter **n** and press **Enter** to create a new partition.

   Information similar to the following is displayed:

   .. code::

      Command (m for help): n
      Partition type:
         p   primary (0 primary, 0 extended, 4 free)
         e   extended

   There are two types of disk partitions:

   -  Choosing **p** creates a primary partition.
   -  Choosing **e** creates an extended partition.

   |image1|

   If the MBR partition style is used, a maximum of 4 primary partitions, or 3 primary partitions and 1 extended partition can be created. The extended partition cannot be used directly and must be divided into logical partitions before use.

   Disk partitions created using GPT are not categorized.

#. In this example, a primary partition is created. Therefore, enter **p** and press **Enter** to create a primary partition.

   Information similar to the following is displayed:

   .. code::

      Select (default p): p
      Partition number (1-4, default 1): 

   **Partition number** indicates the serial number of the primary partition. The value ranges from **1** to **4**.

#. Enter the serial number of the primary partition and press **Enter**. Primary partition number **1** is used in this example. One usually starts with partition number **1** when partitioning an empty disk.

   Information similar to the following is displayed:

   .. code::

      Partition number (1-4, default 1): 1
      First sector (2048-209715199, default 2048):

   **First sector** indicates the start sector. The value ranges from **2048** to **209715199**, and the default value is **2048**.

#. Select the default start sector **2048** and press **Enter**.

   The system displays the start and end sectors of the partition's available space. You can customize the value within this range or use the default value. The start sector must be smaller than the partition's end sector.

   Information similar to the following is displayed:

   .. code::

      First sector (2048-209715199, default 2048):
      Using default value 2048
      Last sector, +sectors or +size{K,M,G} (2048-209715199, default 209715199):

   **Last sector** indicates the end sector. The value ranges from **2048** to **209715199**, and the default value is **209715199**.

#. Select the default end sector **209715199** and press **Enter**.

   The system displays the start and end sectors of the partition's available space. You can customize the value within this range or use the default value. The start sector must be smaller than the partition's end sector.

   Information similar to the following is displayed:

   .. code::

      Last sector, +sectors or +size{K,M,G} (2048-209715199, default 209715199):
      Using default value 209715199
      Partition 1 of type Linux and of size 100 GiB is set

      Command (m for help):

   A primary partition has been created for the new data disk.

#. Enter **p** and press **Enter** to view details about the new partition.

   Information similar to the following is displayed:

   .. code::

      Command (m for help): p

      Disk /dev/vdb: 107.4 GB, 107374182400 bytes, 209715200 sectors
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

   .. code::

      Command (m for help): w
      The partition table has been altered!

      Calling ioctl() to re-read partition table.
      Syncing disks.

   The partition is created.

   |image2|

   In case that you want to discard the changes made before, you can exit fdisk by entering **q**.

#. Run the following command to synchronize the new partition table to the OS:

   **partprobe**

#. Run the following command to set the file system format for the new partition:

   **mkfs** **-t** *File system format* **/dev/vdb1**

   In this example, run the following command to set the **ext4** file system for the new partition:

   **mkfs -t ext4 /dev/vdb1**

   Information similar to the following is displayed:

   .. code::

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

   |image3|

   The partition sizes supported by file systems vary. Therefore, you are advised to choose an appropriate file system based on your service requirements.

#. Run the following command to create a mount point:

   **mkdir** *Mount point*

   In this example, run the following command to create the **/mnt/sdc** mount point:

   **mkdir /mnt/sdc**

#. Run the following command to mount the new partition on the created mount point:

   **mount** *Disk partition* *Mount point*

   In this example, run the following command to mount the new partition **/dev/vdb1** on **/mnt/sdc**:

   **mount /dev/vdb1 /mnt/sdc**

#. Run the following command to view the mount result:

   **df -TH**

   Information similar to the following is displayed:

   .. code::

      [root@ecs-test-0001 ~]# df -TH
      Filesystem     Type      Size  Used Avail Use% Mounted on
      /dev/vda1      ext4       43G  1.9G   39G   5% /
      devtmpfs       devtmpfs  2.0G     0  2.0G   0% /dev
      tmpfs          tmpfs     2.0G     0  2.0G   0% /dev/shm
      tmpfs          tmpfs     2.0G  9.1M  2.0G   1% /run
      tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
      tmpfs          tmpfs     398M     0  398M   0% /run/user/0
      /dev/vdb1      ext4      106G   63M  101G   1% /mnt/sdc

   New partition **/dev/vdb1** is mounted on **/mnt/sdc**.

   |image4|

   If the server is restarted, the mounting will become invalid. You can set automatic mounting for partitions at system start by modifying the **/etc/fstab** file. For details, see `Setting Automatic Mounting at System Start <#EN-US_TOPIC_0085634797__en-us_topic_0044524669_section15839912195453>`__.

Setting Automatic Mounting at System Start
------------------------------------------

Modify the **fstab** file to set automatic disk mounting at server start. You can also set automatic mounting for the servers containing data. This operation will not affect the existing data.

The following procedure shows how to set automatic disk mounting at server start by using UUIDs to identify disks in the **fstab** file. You are advised not to use device names to identify disks in the file because a device name may change (for example, from /dev/vdb1 to /dev/vdb2) during the server stop or start, resulting in improper server running after restart.

|image5|

UUID is the unique character string for disk partitions in a Linux system.

#. Run the following command to query the partition UUID:

   **blkid** *Disk partition*

   In this example, run the following command to query the UUID of the **/dev/vdb1** partition:

   **blkid /dev/vdb1**

   Information similar to the following is displayed:

   .. code::

      [root@ecs-test-0001 ~]# blkid /dev/vdb1
      /dev/vdb1: UUID="0b3040e2-1367-4abb-841d-ddb0b92693df" TYPE="ext4"

   The UUID of the **/dev/vdb1** partition is displayed.

#. Run the following command to open the **fstab** file using the vi editor:

   **vi /etc/fstab**

#. Press **i** to enter the editing mode.

#. Move the cursor to the end of the file and press **Enter**. Then, add the following information:

   .. code::

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

      If information similar to the following is displayed, the automatic mounting function takes effect:

      .. code::

         root@ecs-test-0001 ~]# mount | grep /mnt/sdc
         /dev/vdb1 on /mnt/sdc type ext4 (rw,relatime,data=ordered)


.. |image1| image:: /_static/images/note_3.0-en-us.png
.. |image2| image:: /_static/images/note_3.0-en-us.png
.. |image3| image:: /_static/images/notice_3.0-en-us.png
.. |image4| image:: /_static/images/note_3.0-en-us.png
.. |image5| image:: /_static/images/note_3.0-en-us.png
