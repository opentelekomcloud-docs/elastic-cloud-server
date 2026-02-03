:original_name: en-us_topic_0021426802.html

.. _en-us_topic_0021426802:

Resetting the Password of a Windows ECS by Attaching a System Disk to a Temporary ECS
=====================================================================================

Scenarios
---------

You can reset your ECS password if:

-  The password is forgotten.
-  The password has expired.

The method described in this section can only be used to change the password of a local Windows account; it cannot be used to change a domain account password.

Prerequisites
-------------

-  A backup has been created for the system disk. For details, see :ref:`Backing Up an ECS <en-us_topic_0000001128604648>`.

-  A temporary Linux ECS running Ubuntu 14.04 or later is available in the same AZ and has the same CPU architecture as the target ECS.

-  You have bound an EIP to the temporary ECS and configured the apt-get source.

-  You have used either of the following methods to install **ntfs-3g** and **chntpw** software packages on the temporary ECS:

   Method 1:

   Run the following command to install the **ntfs-3g** and **chntpw** software packages:

   **sudo apt-get install ntfs-3g chntpw**

   Method 2:

   Download the **ntfs-3g** and **chntpw** software packages of the version required by the temporary ECS OS and install them.

Procedure
---------

#. Stop the original ECS and detach the system disk.

   a. Log in to the management console.

   b. Click |image1| in the upper left corner and select a region and project.

   c. Under **Computing**, click **Elastic Cloud Server**.

   d. Stop the original Windows ECS, switch to the ECS details page, and click the **Disks** tab.

      .. note::

         Do not forcibly stop the Windows ECS. Otherwise, password reset may fail.

   e. .. _en-us_topic_0021426802__li49674320202157:

      Locate the row containing the system disk to be detached and click **Detach** to detach the system disk from the ECS.

#. Attach the system disk to the temporary ECS.

   a. On the details page of the temporary ECS, click the **Disks** tab.

   b. .. _en-us_topic_0021426802__li12352182016164:

      Click **Attach Disk**. In the displayed dialog box, select the system disk detached in step :ref:`1.e <en-us_topic_0021426802__li49674320202157>` and attach it to the temporary ECS.

   c. Remotely log in to the temporary ECS.

   d. Run the following command to query the system disk partitions attached to the temporary ECS, so you can identify the directory of the system disk:

      **fdisk -l**

   e. Run the following command to mount the file system of the detached system disk to the temporary ECS:

      **mount -t ntfs-3g /dev/**\ *system-disk-directory* **/mnt/**

      For example, if the queried system disk directory is xvde2, run the following command:

      **mount -t ntfs-3g /dev/xvde2 /mnt/**

      If the following error information is returned in the command output, the NTFS file systems between the original Windows ECS and the Linux ECS may be inconsistent.

      .. code-block::

         The disk contains an unclean file system (0, 0).
         Metadata kept in Windows cache, refused to mount.
         Failed to mount '/dev/xvde2': Operation not permitted
         The NTFS partition is in an unsafe state. Please resume and shutdown
         Windows fully (no hibernation or fast restarting), or mount the volume
         read-only with the 'ro' mount option.

      If the file system is inconsistent, back up the disk data first, and run the following command to repair the New Technology File System (NTFS) partition, and then attach the system disk:

      **ntfsfix /dev/**\ *system-disk-directory*

      For example, if the queried system disk directory is xvde2, run the following command:

      **ntfsfix /dev/xvde2**

#. On the temporary ECS, change the password of the specified user and clear the original password.

   a. Run the following command to back up the SAM file:

      **cp /mnt/Windows/System32/config/SAM /mnt/Windows/System32/config/SAM.bak**

   b. Run the following command to change the password of the specified user:

      **chntpw -u** **Administrator /mnt/Windows/System32/config/SAM**

   c. Enter **1**, **q**, and **y** as prompted, and press **Enter**.

      The password has been reset if the following information is displayed:

      .. code-block::

         Select: [q] > 1
         Password cleared!
         Select: [q] > q
         Hives that have changed:
         #Name
         0<SAM>
         Write hive files? (y/n) [n] : y
         0<SAM> - OK

#. Stop the temporary ECS, detach the system disk, and attach the system disk to the original Windows ECS.

   a. Stop the temporary ECS, go to the ECS details page, and click the **Disks** tab.

   b. .. _en-us_topic_0021426802__li46368402202157:

      Click **Detach** to detach the system disk temporarily attached in step :ref:`2.b <en-us_topic_0021426802__li12352182016164>`.

   c. On the details page of the original Windows ECS, click the **Disks** tab.

   d. Click **Attach Disk**. In the displayed dialog box, select the system disk detached in step :ref:`4.b <en-us_topic_0021426802__li46368402202157>` and attach it to the original ECS as the system disk.

#. Start the original Windows ECS and set a new login password.

   a. Click **Start** to start the original Windows ECS. After the status becomes **Running**, click **Remote Login** in the **Operation** column.

   b. Click **Start**. Enter **CMD** in the search box and press **Enter**.

   c. Run the following command to set a new password. The new password must meet the password complexity requirements described in :ref:`Overview of Password Reset <en-us_topic_0035643949>`.

      **net user** **Administrator** *<new-password>*

.. |image1| image:: /_static/images/en-us_image_0000002188678994.png
