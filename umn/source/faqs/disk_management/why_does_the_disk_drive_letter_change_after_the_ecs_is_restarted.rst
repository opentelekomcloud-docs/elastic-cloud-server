:original_name: en-us_topic_0240831198.html

.. _en-us_topic_0240831198:

Why Does the Disk Drive Letter Change After the ECS Is Restarted?
=================================================================

Symptom
-------

For a Linux ECS, the drive letter may change after an EVS disk is detached and then attached again, or after an EVS disk is detached and then the ECS is restarted.

Root Cause
----------

When a Linux ECS has multiple disks attached, it allocates drive letters in the attachment sequence and names the disks as **/dev/vda1**, **/dev/vdb1**, and **/dev/vdc1**, etc.

After a disk is detached and then attached again, or after a disk is detached and the ECS is restarted, the drive letter may change.

For example, an ECS has three disks attached: **/dev/vda1**, **/dev/vdb1**, and **/dev/vdc1**. The mounting parameters in **/etc/fstab** are as follows:

**cat /etc/fstab**

.. code-block::

   UUID=b9a07b7b-9322-4e05-ab9b-14b8050bdc8a  /  ext4  defaults  0  1
   /dev/vdb1                       /data1   ext4  defaults  0  0
   /dev/vdc1                       /data2   ext4  defaults  0  0

After **/dev/vdb1** is detached and the ECS is restarted, **/dev/vdc1** becomes **/dev/vdb1** and is mounted to **/data**. In such a case, no disk is mounted to **/data2**.

The change of drive letters can affect the running of applications. To solve this problem, you are advised to use the universally unique identifiers (UUIDs) to replace **/dev/vdx** because a UUID uniquely identifies a disk partition in the Linux OS.

Solution
--------

#. Log in to the ECS.

#. .. _en-us_topic_0240831198__li1692132771619:

   Run the following command to obtain the partition UUID:

   **blkid** *Disk partition*

   In this example, run the following command to obtain the UUID of the **/dev/vdb1** partition:

   **blkid /dev/vdb1**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# blkid /dev/vdb1
      /dev/vdb1: UUID="b9a07b7b-9322-4e05-ab9b-14b8050cd8cc" TYPE="ext4"

   The UUID of the **/dev/vdb1** partition is displayed.

#. Run the following command to open the **fstab** file using the vi editor:

   **vi /etc/fstab**

#. Press **i** to enter the editing mode.

#. .. _en-us_topic_0240831198__li101765321710:

   Move the cursor to the end of the file and press **Enter**. Then, add the following information:

   .. code-block::

      UUID=b9a07b7b-9322-4e05-ab9b-14b8050cd8cc    /data1   ext4    defaults        0 0

   The parameters are defined as follows:

   -  **UUID=b9a07b7b-9322-4e05-ab9b-14b8050cd8cc**: UUID of a disk partition.
   -  **/data1**: directory on which the partition is mounted. You can run **df -TH** to query the directory.
   -  **ext4**: File system format of the partition. You can run **df -TH** to query the format.
   -  **defaults**: partition mount option. Normally, this parameter is set to **defaults**.
   -  **0** (the first one): whether to use Linux dump backup.

      -  **0**: Linux dump backup is not used. Normally, dump backup is not used, and you can set this parameter to **0**.
      -  **1**: Linux dump backup is used.

   -  **0** (the second one): fsck option, that is, whether to use fsck to check disks during startup.

      -  **0**: fsck is not used.

      -  If the mount point is the root partition (**/**), this parameter must be set to **1**.

         When this parameter is set to **1** for the root partition, this parameter for other partitions must start with **2** so that the system checks the partitions in the ascending order of the values.

#. Repeat steps :ref:`2 <en-us_topic_0240831198__li1692132771619>` to :ref:`5 <en-us_topic_0240831198__li101765321710>` to replace the UUID of **/dev/vdc1**.

#. Run the following command again to check the disk mounting parameters:

   **cat /etc/fstab**

   The following information is displayed:

   .. code-block::

      UUID=b9a07b7b-9322-4e05-ab9b-14b8050bdc8a  /  ext4  defaults  0  1
      UUID=b9a07b7b-9322-4e05-ab9b-14b8050cd8cc   /data1   ext4  defaults  0  0
      UUID=b9a07b7b-9322-4e05-ab9b-14b8050ab6bb   /data2   ext4  defaults  0  0
