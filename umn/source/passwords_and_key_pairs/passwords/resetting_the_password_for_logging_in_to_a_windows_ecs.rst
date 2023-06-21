:original_name: en-us_topic_0021426802.html

.. _en-us_topic_0021426802:

Resetting the Password for Logging In to a Windows ECS
======================================================

Scenarios
---------

You can reset your ECS password if:

-  The password is forgotten.
-  The password has expired.

The method described in this section can only be used to change the password of a local Windows account, but not the password of a domain account.

Prerequisites
-------------

-  A temporary Linux ECS which runs Ubuntu 14.04 or later and locates in the same AZ as the target ECS is available.

-  You have bound an EIP to the temporary ECS and configured the apt-get source.

-  You have used either of the following methods to install **ntfs-3g** and **chntpw** software packages on the temporary ECS:

   Method 1:

   Run the following command to install the **ntfs-3g** and **chntpw** software packages:

   **sudo apt-get install ntfs-3g chntpw**

   Method 2:

   Download the ntfs-3g and chntpw software packages of the version required by the temporary ECS OS.

Procedure
---------

#. Stop the original ECS and detach the system disk.

   a. Log in to the management console.

   b. Click |image1| in the upper left corner and select your region and project.

   c. Under **Computing**, click **Elastic Cloud Server**.

   d. Stop the original Windows ECS, switch to the page providing details about the ECS, and click the **Disks** tab.

      .. note::

         Do not forcibly stop the Windows ECS. Otherwise, password reset may fail.

   e. .. _en-us_topic_0021426802__li49674320202157:

      Locate the row containing the system disk to be detached and click **Detach** to detach the system disk from the ECS.

#. Attach the system disk to the temporary ECS.

   a. On the page providing details about the temporary ECS, click the **Disks** tab.

   b. .. _en-us_topic_0021426802__li12352182016164:

      Click **Attach Disk**. In the displayed dialog box, select the system disk detached in step :ref:`1.e <en-us_topic_0021426802__li49674320202157>` and attach it to the temporary ECS.

   c. Remotely log in to the temporary ECS.

   d. .. _en-us_topic_0021426802__li20334892202157:

      Run the following command to view the directory of the system disk detached from the original Windows ECS now attached to the temporary ECS:

      **fdisk -l**

   e. Run the following command to mount the file system of the detached system disk to the temporary ECS:

      **mount -t ntfs-3g /dev/**\ *Result obtained in step :ref:`2.d <en-us_topic_0021426802__li20334892202157>`* **/mnt/**

      For example, if the result obtained in step :ref:`2.d <en-us_topic_0021426802__li20334892202157>` is **xvde2**, run the following command:

      **mount -t ntfs-3g /dev/xvde2 /mnt/**

      If the following error information is displayed after the preceding command is executed, the NTFS file systems may be inconsistent. In such a case, rectify the file system inconsistency.

      .. code-block::

         The disk contains an unclean file system (0, 0).
         Metadata kept in Windows cache, refused to mount.
         Failed to mount '/dev/xvde2': Operation not permitted
         The NTFS partition is in an unsafe state. Please resume and shutdown
         Windows fully (no hibernation or fast restarting), or mount the volume
         read-only with the 'ro' mount option.

      Back up the disk data, run the following command to rectify the NTFS file system inconsistency, and attach the system disk:

      **ntfsfix /dev/**\ *Result obtained in step :ref:`2.d <en-us_topic_0021426802__li20334892202157>`*

      For example, if the result obtained in step :ref:`2.d <en-us_topic_0021426802__li20334892202157>` is **xvde2**, run the following command:

      **ntfsfix /dev/xvde2**

#. Change the password of the specified user and clear the original password.

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

   a. Stop the temporary ECS, switch to the page providing details about the ECS, and click the **Disks** tab.

   b. .. _en-us_topic_0021426802__li46368402202157:

      Click **Detach** to detach the data disk temporarily attached in step :ref:`2.b <en-us_topic_0021426802__li12352182016164>`.

   c. On the page providing details about the original Windows ECS, click the **Disks** tab.

   d. Click **Attach Disk**. In the displayed dialog box, select the data disk detached in step :ref:`4.b <en-us_topic_0021426802__li46368402202157>` and device name **/dev/sda**.

#. Start the original Windows ECS and set a new login password.

   a. Click **Start** to start the original Windows ECS. After the status becomes **Running**, click **Remote Login** in the **Operation** column.

   b. Click **Start**. Enter **CMD** in the search box and press **Enter**.

   c. Run the following command to change the password (the new password must meet the requirements described in :ref:`Table 1 <en-us_topic_0021426802__en-us_topic_0021426802_table4381109318958>`):

      **net user** **Administrator** *New password*

      .. _en-us_topic_0021426802__en-us_topic_0021426802_table4381109318958:

      .. table:: **Table 1** Password complexity requirements

         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
         | Parameter             | Requirement                                                                                                                                                  | Example Value                                                 |
         +=======================+==============================================================================================================================================================+===============================================================+
         | Password              | -  Consists of 8 to 26 characters.                                                                                                                           | YNbUwp!dUc9MClnv                                              |
         |                       | -  Contains at least three of the following character types:                                                                                                 |                                                               |
         |                       |                                                                                                                                                              | .. note::                                                     |
         |                       |    -  Uppercase letters                                                                                                                                      |                                                               |
         |                       |    -  Lowercase letters                                                                                                                                      |    The example password is generated randomly. Do not use it. |
         |                       |    -  Digits                                                                                                                                                 |                                                               |
         |                       |    -  Special characters: ``$!@%-_=+[]:./^,{}?``                                                                                                             |                                                               |
         |                       |                                                                                                                                                              |                                                               |
         |                       | -  Cannot contain the username or the username spelled backwards.                                                                                            |                                                               |
         |                       | -  Cannot contain more than two consecutive characters in the same sequence as they appear in the username. (This requirement applies only to Windows ECSs.) |                                                               |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0210779229.png
