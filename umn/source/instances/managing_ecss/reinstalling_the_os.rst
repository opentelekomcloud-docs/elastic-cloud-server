Reinstalling the OS
===================

Scenarios
---------

If the OS of an ECS fails to start or requires optimization, reinstall the OS.

Notes
-----

-  After the OS is reinstalled, the IP and MAC addresses of the ECS remain unchanged.
-  Reinstalling the OS clears the data in all partitions of the EVS system disk, including the system partition. Therefore, back up data before reinstalling the OS.
-  Reinstalling the OS does not affect data disks.
-  Do not perform any operations on the ECS immediately after its OS is reinstalled. Wait for several minutes until the system successfully injects the password or key. Otherwise, the injection may fail, and the ECS cannot be logged in to.
-  After the OS is reinstalled, the password for logging in to the ECS will be reset. To retrieve the password, perform the following operations:

   -  For a Linux ECS, log in to it using the key and set a new password. For instructions about how to log in to an ECS using a key pair, see `Login Using an SSH Key <instances/logging_in_to_a_linux_ecs/login_using_an_ssh_key>`__.
   -  For a Windows ECS, retrieve the password by following the instructions provided in `Obtaining the Password for Logging In to a Windows ECS <passwords_and_key_pairs/obtaining_the_password_for_logging_in_to_a_windows_ecs>`__.

-  You can choose to encrypt the system disk of an ECS during OS reinstallation.

Constraints
-----------

-  The EVS disk quota must be greater than 0.
-  If the target ECS is created using a private image, ensure that the private image is available.
-  H2 ECSs do not support OS reinstallation.
-  If an ECS OS is to be reinstalled using a full-ECS image, the ECS system disk can be encrypted.

Prerequisites
-------------

-  The target ECS is stopped.
-  The target ECS has a system disk attached.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. Locate the row containing the target ECS. Click **More** in the **Operation** column and select **Manage Image/Disk** > **Reinstall OS**.

   Only stopped ECSs support OS reinstallation. If the ECS is not stopped, stop it before proceeding with reinstallation.

#. (Optional) Select the **Encryption** option to encrypt the system disk during OS reinstallation.

   To enable encryption, click **Create Xrole** to assign KMS access permissions to EVS. If you have rights granting permission, assign the KMS access permissions to EVS. If you do not have the permission, contact the user having the security administrator rights to assign the KMS access permissions. For more details, see `Can All Users Use the Encryption Feature? <faqs/disk_management/can_all_users_use_the_encryption_feature>`__

   Encryption parameters are as follows:

   -  **Encryption**: indicates that the EVS disk has been encrypted.
   -  **Create Xrole**: assigns KMS access permissions to EVS to obtain KMS keys. After the permissions are assigned, follow-up operations do not require assigning permissions again.
   -  **KMS Key Name**: specifies the name of the key used by the encrypted EVS disk. You can select an existing key, or click **Create KMS Key** and create a new one on the KMS console. The default value is **evs/default**.
   -  **Xrole Name: EVSAccessKMS**: specifies that permissions have been assigned to EVS to obtain KMS keys for encrypting or decrypting EVS disks.
   -  **KMS Key ID**: specifies the ID of the key used by the encrypted data disk.

#. (Optional) Select a **License Type** (**Use license from the system** or **Bring your own license (BYOL)**) if the reinstalled OS running on your ECS is billed. For more details, see `License Type <service_overview/security/license_type>`__.

   The following OSs are billed:

   -  SUSE Linux Enterprise Server
   -  Oracle Enterprise Linux
   -  Red Hat Enterprise Linux

#. Configure the login mode.

   If the target ECS uses key pair authentication, you can replace the original key pair.

#. Click **OK**.

#. On the **ECS OS Reinstallation** page, confirm the OS specifications, and click **Submit Application**.After the request is submitted, the ECS status changes to **Reinstalling**. The reinstallation has been completed when the ECS status changes to **Running**.\ |image2|

   A temporary ECS is created during the reinstallation process. After reinstallation, this ECS will be automatically deleted. Do not perform any operation on the temporary ECS during the reinstallation process.

Follow-up Procedure
-------------------

If the reinstallation is unsuccessful, perform steps `3 <#EN-US_TOPIC_0024911405__li20776247143354>`__ to `9 <#EN-US_TOPIC_0024911405__li31062819143541>`__ again to retry reinstalling the OS again.

If the second reinstallation attempt is unsuccessful, contact customer service for manual recovery at the backend.


.. |image1| image:: /_static/images/en-us_image_0210779229.png

.. |image2| image:: /_static/images/note_3.0-en-us.png
