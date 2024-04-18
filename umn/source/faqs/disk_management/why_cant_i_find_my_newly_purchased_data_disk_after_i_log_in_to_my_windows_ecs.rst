:original_name: en-us_topic_0251012483.html

.. _en-us_topic_0251012483:

Why Can't I Find My Newly Purchased Data Disk After I Log In to My Windows ECS?
===============================================================================

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

For details, see `Introduction to Data Disk Initialization Scenarios and Partition Styles <https://docs.otc.t-systems.com/elastic-volume-service/umn/getting_started/initialize_an_evs_data_disk/introduction_to_data_disk_initialization_scenarios_and_partition_styles.html>`__.

Disk Becomes Offline After the ECS OS Is Changed or the ECS Specifications Are Modified
---------------------------------------------------------------------------------------

After the ECS OS is changed, data disks may become unavailable due to file system inconsistency. After the specifications of a Windows ECS are modified, data disks may be offline.

#. Log in to the ECS, open the **cmd** window, and enter **diskmgmt.msc** to switch to the **Disk Management** page.

   Check whether the affected disk is offline.

#. Set the affected disk to be online.

   In the disk list, right-click the affected disk and choose **Online** from the shortcut menu to make it online.


   .. figure:: /_static/images/en-us_image_0251063932.png
      :alt: **Figure 1** Setting disk online

      **Figure 1** Setting disk online

#. In **My Computer**, check whether the data disk is displayed properly.

   If the fault persists, initialize and partition the disk again. Before initializing the disk, create a backup for it.
