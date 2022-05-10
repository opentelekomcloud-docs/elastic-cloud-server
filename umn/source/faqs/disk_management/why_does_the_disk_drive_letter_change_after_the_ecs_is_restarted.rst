:original_name: en-us_topic_0240831198.html

.. _en-us_topic_0240831198:

Why Does the Disk Drive Letter Change After the ECS Is Restarted?
=================================================================

Symptom
-------

For a Linux ECS, the drive letter may change after an EVS disk is detached and then attached again, or after an EVS disk is detached and then the ECS is restarted. This is a normal phenomenon due to the drive letter allocation mechanism of the Linux system.

For example, an ECS has three disks attached: **/dev/vda1**, **/dev/vdb1**, and **/dev/vdc1**. The mounting parameters in **/etc/fstab** are as follows:

cat /etc/fstab

.. code-block::

   UUID=b9a07b7b-9322-4e05-ab9b-14b8050bdc8a  /  ext4  defaults  0  1
   /dev/vdb1                       /data1   ext4  defaults  0  0
   /dev/vdc1                       /data2   ext4  defaults  0  0

If **/dev/vdb1** is detached, **/dev/vdc1** becomes **/dev/vdb1** and is mounted to **/data1** after the ECS is restarted. In such a case, no disk is mounted to **/data2**.

Solution
--------

To prevent this issue, use a UUID, a unique character string provided by the Linux system for disk partitions, to replace the /dev/vdx device.

#. Run the following command to obtain the partition UUID:

   **blkid** *Disk partition*

   In this example, run the following command to obtain the UUID of the **/dev/vdb1** partition:

   **blkid /dev/vdb1**

   Information similar to the following is displayed:

   .. code-block::

      [root@ecs-test-0001 ~]# blkid /dev/vdb1 
      /dev/vdb1: UUID="b9a07b7b-9322-4e05-ab9b-14b8050cd8cc" TYPE="ext4"

   The UUID of the **/dev/vdb1** partition is displayed.

#. Run the following command to open the **fstab** file using the vi editor:

   **vi /etc/fstab**

#. Press **i** to enter the editing mode.

#. Move the cursor to the end of the file and press **Enter**. Then, add the following information:

   .. code-block::

      UUID=b9a07b7b-9322-4e05-ab9b-14b8050cd8cc /mnt/sdc                ext4    defaults        0 0

   Repeat the preceding operations to add the UUID of the **/dev/vdc1** partition and run the following command to check the disk mounting parameters:

   cat /etc/fstab

   The following information is displayed:

   .. code-block::

      UUID=b9a07b7b-9322-4e05-ab9b-14b8050bdc8a  /  ext4  defaults  0  1
      UUID=b9a07b7b-9322-4e05-ab9b-14b8050cd8cc   /data1   ext4  defaults  0  0
      UUID=b9a07b7b-9322-4e05-ab9b-14b8050ab6bb   /data2   ext4  defaults  0  0
