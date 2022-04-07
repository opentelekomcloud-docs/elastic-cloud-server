.. _en-us_topic_0251012483:

What Should I Do If the Data Disk Attached a Windows ECS Is Unavailable?
========================================================================

Symptom
-------

After logging in to my Windows ECS, I cannot find the attached data disk.

.. caution::

   Formatting a disk will cause data loss. Therefore, before formatting a disk, create a backup for it.

Possible Causes
---------------

-  A newly added data disk has not been partitioned or initialized.
-  The disk becomes offline after the ECS OS is changed or the ECS specifications are modified.

Newly Added Data Disk Has Not Been Partitioned or Initialized
-------------------------------------------------------------

A new data disk does not have partitions and file systems by default. That is why it is unavailable in **My Computer**. To resolve this issue, manually initialize the disk.

Disk Becomes Offline After the ECS OS Is Changed or the ECS Specifications Are Modified
---------------------------------------------------------------------------------------

After the ECS OS is changed, data disks may become unavailable due to file system inconsistency. After the specifications of a Windows ECS are modified, data disks may be offline.

#. Log in to the ECS, open the **cmd** window, and enter **diskmgmt.msc** to switch to the **Disk Management** page.

   Check whether the affected disk is offline.

#. Set the affected disk to be online.

   In the disk list, right-click the affected disk and choose **Online** from the shortcut menu to make it online.

   .. _en-us_topic_0251012483__fig1869603017195:

   .. figure:: /_static/images/en-us_image_0251063932.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 1** Setting disk online

#. In **My Computer**, check whether the data disk is displayed properly.

   If the fault persists, initialize and partition the disk again. Before initializing the disk, create a backup for it.
