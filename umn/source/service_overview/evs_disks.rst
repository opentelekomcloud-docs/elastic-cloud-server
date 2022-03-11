EVS Disks
=========

What Is Elastic Volume Service?
-------------------------------

Elastic Volume Service (EVS) offers scalable block storage for ECSs. With high reliability, high performance, and rich specifications, EVS disks can be used for distributed file systems, development and test environments, data warehouse applications, and high-performance computing (HPC) scenarios to meet diverse service requirements.

Disk Types
----------

EVS disk types differ in performance. Choose the disk type based on your requirements.

For more information about EVS disk specifications and performance, see *Elastic Volume Service User Guide*.

Device Types
------------

EVS disks have two device types, Virtual Block Device (VBD) and Small Computer System Interface (SCSI).

-  VBD

   When you create an EVS disk on the management console, **Device Type** of the EVS disk is VBD by default. VBD EVS disks support only simple SCSI read/write commands.

-  SCSI

   You can create EVS disks whose **Device Type** is SCSI on the management console. These EVS disks support transparent SCSI command transmission, allowing ECS OS to directly access underlying storage media. SCSI EVS disks support both basic and advanced SCSI commands.

   |image1|

   For more information about how to use SCSI EVS disks, for example, how to install the driver, see "Device Types and Usage Instructions" in *Elastic Volume Service User Guide*.

Helpful Links
-------------

-  `Which ECSs Can Be Attached with SCSI EVS Disks? <faqs/disk_management/which_ecss_can_be_attached_with_scsi_evs_disks>`__


.. |image1| image:: /_static/images/note_3.0-en-us.png
