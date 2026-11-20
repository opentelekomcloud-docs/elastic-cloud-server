:original_name: en-us_topic_0031523135.html

.. _en-us_topic_0031523135:

Changing the OS
===============

Scenarios
---------

If the OS running on an ECS cannot meet service requirements, change the ECS OS.

The cloud platform supports changing between image types (public images, private images, and shared images) and between OSs. You can change your OS by changing your ECS image.

Constraints
-----------

-  An OS change takes about 1 to 4 minutes to complete. During this process, the ECS status is **Changing OS**.
-  Do not perform any operations on the ECS before the system injects the password or key, or the login will fail.
-  The ECS for which you want to change the OS must be in any of the following states: **Stopped**, **Reinstallation failed**, or **Failed to change the OS**.
-  The target ECS must have a system disk attached.
-  The EVS disk quota must be greater than 0.
-  The system disk type cannot be changed.
-  The system disk can be encrypted.
-  If an ECS OS is changed using a full-ECS image, the ECS system disk can be encrypted.

Important Notes
---------------

-  After the OS is changed, the original OS on your ECS will no longer be retained.
-  Changing the OS clears all data on the system disk, including the system partition and all other partitions. Back up data before changing the OS.
-  Changing the OS does not affect data in data disks.
-  After the OS is changed, your service runtime environment must be deployed on the new OS again.
-  After the OS is changed, the ECS will automatically start up.
-  After the OS is changed, the system disk type of the ECS cannot be changed.
-  After the OS is changed, the IP and MAC addresses of the ECS remain unchanged.
-  After the OS is changed, custom system settings (such as DNS and hostname settings) of the original OS will be reset and need to be reconfigured.
-  An OS change takes about 1 to 4 minutes to complete. During this process, the ECS status is **Changing OS**.
-  After the OS is changed, the password for logging in to the ECS is reset. To retrieve the password, perform the following operations:

   -  For a Linux ECS, log in to it using the key and set a new password. For instructions about how to log in to an ECS using a key pair, see :ref:`Logging In to a Linux ECS Using an SSH Key Pair <en-us_topic_0017955380>`.
   -  For a Windows ECS, retrieve the password by following the instructions provided in :ref:`Obtaining the Password for Logging In to a Windows ECS <en-us_topic_0031107266>`.

-  After the OS is changed, the ECS system disk capacity may increase depending on the selected image.
-  You can choose to encrypt the system disk of an ECS during OS change.
-  When you change the OS from Windows to Linux or vice versa, note the following:

   -  To change Windows to Linux, install a tool or driver (such as NTFS-3G) that enables read and write access to Windows NTFS partitions.
   -  To change Linux to Windows, install software, such as Ext2Read or Ext2Fsd, to identify ext3 or ext4.

      .. note::

         If there are LVM partitions on the Linux ECS, these partitions may fail to be identified after the OS is changed to Windows. Therefore, a change from Linux to Windows is not recommended.

Prerequisites
-------------

-  The ECS data has been backed up.

-  If you want to change the login authentication mode from password to key pair during the OS change, ensure that you have created a key file.

   For details, see :ref:`(Recommended) Creating a Key Pair on the Management Console <en-us_topic_0000001278350057>`.

-  If you plan to use a private image to change the OS, ensure that a private image is available. For details about how to create a private image, see *Image Management Service User Guide*.

   -  If the image of a specified ECS is required, make sure that a private image has been created using this ECS.
   -  If a local image file is required, make sure that the image file has been imported to the cloud platform and registered as a private image.
   -  If a private image from another region is required, make sure that the image has been copied.
   -  If a private image from another account is required, make sure that the image has been shared with you.

.. _en-us_topic_0031523135__section208284422018:

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. Locate the row containing the target ECS and choose **More** > **Manage Image/Backup** > **Change OS** in the **Operation** column.

   Only stopped ECSs support OS changes. If the ECS is not stopped, stop it before proceeding with the change.

#. Select the target image.

   For details, see :ref:`Creating an ECS <en-us_topic_0021831611>`.


   .. figure:: /_static/images/en-us_image_0000002385192025.png
      :alt: **Figure 1** Changing an OS

      **Figure 1** Changing an OS

#. (Optional) Set disk encryption.

   Perform this step only when you need to encrypt the system disk when changing the OS.

   To enable encryption, click **Create Xrole** to grant KMS access permissions to EVS. If you have the required authorization permissions, grant access directly. If you lack the required permissions, contact a user with the Security Administrator permissions to grant access. For details, see :ref:`Can All Users Use the Encryption Feature? <en-us_topic_0047272493>`

   Encryption parameters are as follows:

   -  **Encryption**: indicates that the EVS disk has been encrypted.
   -  **Create Xrole**: assigns KMS access permissions to EVS to obtain KMS keys. After the permissions are assigned, follow-up operations do not require assigning permissions again.
   -  **Xrole Name**: set to **EVSAccessKMS**, which means that permissions have been assigned to EVS to obtain KMS keys for encrypting or decrypting EVS disks.
   -  **KMS Key Name**: specifies the name of the key used by the encrypted EVS disk. You can select an existing key, or click **Create KMS Key** and create a new one on the KMS console. The default value is **evs/default**.
   -  **KMS Key ID**: specifies the ID of the key used by the encrypted data disk.

#. (Optional) Set **License Type** (**Use license from the system** or **Bring your own license (BYOL)**) if the new OS is billed. For more details, see :ref:`License Types <en-us_topic_0046566932>`.

   The following OSs are billed:

   -  SUSE Linux Enterprise Server
   -  Oracle Enterprise Linux
   -  Red Hat Enterprise Linux

#. Set **Login Mode**.

   You can select a desired login mode based on service requirements.

   -  If you select **Key pair** for **Login Mode**, select an available key pair from the drop-down list or create a key pair. For details, see :ref:`(Recommended) Creating a Key Pair on the Management Console <en-us_topic_0000001278350057>`.

#. Click **OK** to start the OS change.

   After the OS change request is submitted, the ECS status changes to **Changing OS**. When this status disappears, the OS change is complete.

Follow-up Procedure
-------------------

-  If the OS before and after the change is Linux, and if auto mount at startup has been enabled for the data disk, the data disk partition mounting information will be lost after the OS is changed. In such a case, you need to update the **/etc/fstab** configuration.

   #. Write the new partition information into **/etc/fstab**.

      It is a good practice to back up the **/etc/fstab** file before writing data into it.

      To enable auto mount at startup, see :ref:`Initializing EVS Data Disks <en-us_topic_0030831989>`.

   #. Mount the partition so that you can use data disks.

      **mount** *disk-partition* *mount-point*

   #. Check the mount result.

      **df -TH**

-  If the OS change fails, perform the operations described in :ref:`Procedure <en-us_topic_0031523135__section208284422018>` again to retry the OS change.
-  If the retry fails, contact customer service for manual recovery at the backend.

.. |image1| image:: /_static/images/en-us_image_0000002188678994.png
