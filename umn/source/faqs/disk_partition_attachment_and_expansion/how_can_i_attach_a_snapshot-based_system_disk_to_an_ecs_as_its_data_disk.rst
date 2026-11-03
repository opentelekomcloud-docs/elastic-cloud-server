:original_name: en-us_topic_0152643976.html

.. _en-us_topic_0152643976:

How Can I Attach a Snapshot-based System Disk to an ECS as Its Data Disk?
=========================================================================

Scenarios
---------

To restore data, a system disk snapshot of ECS A is used to create disk A. Then, disk A is attached to ECS B as a data disk. However, after ECS B is restarted, data disk A may be attached as the root file system but not the system disk of ECS B. In such a case, the data of ECS A is contained in the root file system of ECS B.

Possible Causes
---------------

When Linux ECSs start, the root file systems to be mounted are identified by disk label but not UUID. However, system disk labels are the same, which may lead to a system disk attachment error.

Solution
--------

Replace the **/dev/disk/by-label/ROOT** files in **/etc/fstab** with the files in **/dev/disk/by-id**. The new files start with a unique virtio-EVS-ID.

To do so, perform the following operations:

#. Check whether the root file system is identified by disk label. If information similar to the following is displayed in the configuration files in **/etc/fstab** of the target ECS, its root file system is identified by disk label:

   .. code-block::

      /dev/disk/by-label/ROOT  /  ext4 defaults 1 1

#. After attaching data disk A to ECS B, run the following command to obtain the disk ID:

   **$ ls -l /dev/disk/by-id/**

   .. code-block::

      total 0
      lrwxrwxrwx. 1 root root 9 Nov 16 19:40 virtio-20211065-0f57-46d4-9 -> ../../vda
      lrwxrwxrwx. 1 root root 10 Nov 16 19:40 virtio-20211065-0f57-46d4-9-part1 -> ../../vda1
      lrwxrwxrwx. 1 root root 9 Nov 16 19:40 virtio-842dbfd3-9f2c-4273-9 -> ../../vdb
      lrwxrwxrwx. 1 root root 10 Nov 16 19:40 virtio-842dbfd3-9f2c-4273-9-part1 -> ../../vdb1

#. Run the following command to change the disk ID to the desired one in the configuration files in **/etc/fstab** of ECS B:

   **vi /etc/fstab**

   .. code-block::

      /dev/disk/by-id/virtio-20211065-0f57-46d4-9-part1 / ext4 defaults 1 1
      /dev/disk/by-id/virtio-842dbfd3-9f2c-4273-9-part1 /vdb1-test ext4 defaults 1 1

#. Press **Esc** to exit editing mode.

#. Run the following command to save the configuration and exit:

   **:wq**

#. Restart the ECS for the modification to take effect.
