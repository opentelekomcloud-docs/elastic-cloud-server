.. _en-us_topic_0021427650:

Resetting the Password for Logging In to a Linux ECS
====================================================

Scenarios
---------

Keep your password secure. Reset the password if:

-  The password is forgotten.
-  The password has expired.

This section describes how to reset the password of user **root**. After resetting the password, you can log in to the ECS, and change the private key or reset the password of a non-**root** user.

Prerequisites
-------------

-  A temporary Linux ECS which locates in the same AZ as the target ECS is available.
-  You have bound an EIP to the temporary ECS.

Procedure
---------

#. Download the script for resetting the password and upload the script to the temporary ECS.

   Contact customer service to obtain the password reset script. Use a connection tool, such as WinSCP, to upload the obtained **changepasswd.sh** script to the temporary ECS.

   To download WinSCP, log in at https://winscp.net/.

#. .. _en-us_topic_0021427650__li19814359584:

   Stop the original Linux ECS, detach the system disk from it, and attach the system disk to the temporary ECS.

   a. Stop the original ECS, switch to the page providing details about the ECS, and click the **Disks** tab.

      .. note::

         Do not forcibly stop the original ECS. Otherwise, password reset may fail.

   b. .. _en-us_topic_0021427650__li5640121684418:

      Locate the row containing the system disk to be detached and click **Detach** to detach the system disk from the ECS.

   c. On the page providing details about the temporary ECS, click the **Disks** tab.

   d. Click **Attach Disk**. In the displayed dialog box, select the system disk detached in step :ref:`2.b <en-us_topic_0021427650__li5640121684418>` and attach it to the temporary ECS.

#. Log in to the temporary ECS remotely and reset the password.

   a. Locate the row containing the temporary ECS and click **Remote Login** in the **Operation** column.

   b. .. _en-us_topic_0021427650__li664021617445:

      Run the following command to view the directory of the system disk detached from the original Linux ECS now attached to the temporary ECS:

      **fdisk -l**

   c. Run the following commands in the directory where the script is stored to run the script for resetting the password:

      **chmod +x changepasswd.sh**

      **./changepasswd.sh**

      When you run the password reset script, if the system displays a message indicating that there is no command related to logical volume manager (LVM), such as the message "no lvs command", install an LVM tool on the temporary ECS. The LVM2 tool is recommended, which can be installed by running the **yum install lvm2** command.

      .. note::

         If the original ECS and the temporary ECS both run CentOS 7, a mount failure may occur during script execution. To resolve this issue, replace **mount $dev $mountPath** with **mount -o nouuid $dev $mountPath** in the script.

   d. Enter the new password and the directory obtained in step :ref:`3.b <en-us_topic_0021427650__li664021617445>` as prompted.

      If the following information is displayed, the password has been changed:

      .. code-block::

         set password success.

#. For a non-**root** user, perform the following operations to enable the login permission of user **root**:

   **vi /etc/ssh/sshd_config**

   Modify the following parameters:

   -  Change **PasswordAuthentication no** to **PasswordAuthentication yes**.

      Alternatively, delete the comment tag (#) before **PasswordAuthentication yes**.

   -  Change **PermitRootLogin no** to **PermitRootLogin yes**.

      Alternatively, delete the comment tag (#) before **PermitRootLogin yes**.

   -  Change the value of **AllowUsers** to **root**.

      Search for **AllowUsers** in the file. If **AllowUsers** is unavailable, add it at the end of the file.

#. Stop the temporary ECS, detach the system disk, attach the system disk to the original Linux ECS, and restart the original Linux ECS.

   a. Stop the temporary ECS, switch to the page providing details about the ECS, and click the **Disks** tab.

   b. .. _en-us_topic_0021427650__li964031614447:

      Click **Detach** to detach the data disk attached in step :ref:`2 <en-us_topic_0021427650__li19814359584>`.

   c. On the page providing details about the original Linux ECS, click the **Disks** tab.

   d. Click **Attach Disk**. In the displayed dialog box, select the data disk detached in step :ref:`5.b <en-us_topic_0021427650__li964031614447>` and device name **/dev/sda**.

   e. Restart the original Linux ECS.
