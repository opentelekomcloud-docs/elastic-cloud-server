:original_name: en-us_topic_0030828256.html

.. _en-us_topic_0030828256:

EVS Disks
=========

What Is Elastic Volume Service?
-------------------------------

Elastic Volume Service (EVS) offers scalable block storage for ECSs. With high reliability, high performance, and rich specifications, EVS disks can be used for distributed file systems, development and test environments, data warehouses, and high-performance computing (HPC) scenarios to meet diverse service requirements.

Disk Types
----------

EVS disk types differ in performance. Choose a disk type based on your requirements.

For more information about EVS disk specifications and performance, see *Elastic Volume Service User Guide*.

Device Types
------------

EVS disks have two device types, Virtual Block Device (VBD) and Small Computer System Interface (SCSI).

-  VBD

   When you create an EVS disk on the management console, **Device Type** of the EVS disk is VBD by default. VBD EVS disks support only simple SCSI read/write commands.

-  SCSI

   You can create EVS disks whose **Device Type** is SCSI on the management console. These EVS disks support transparent SCSI command transmission, allowing ECS OS to directly access underlying storage media. SCSI EVS disks support both basic and advanced SCSI commands.

   .. note::

      For more information about how to use SCSI EVS disks, for example, how to install a driver for SCSI EVS disks, see "Device Types and Usage Instructions" in *Elastic Volume Service User Guide*.

Helpful Links
-------------

-  :ref:`Which ECSs Can Be Attached with SCSI EVS Disks? <en-us_topic_0077938284>`
