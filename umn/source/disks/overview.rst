:original_name: en-us_topic_0140313880.html

.. _en-us_topic_0140313880:

Overview
========

What Is Elastic Volume Service?
-------------------------------

Elastic Volume Service (EVS) offers scalable block storage for ECSs. With high reliability, high performance, and rich specifications, EVS disks can be used for distributed file systems, development and test environments, data warehouses, and high-performance computing (HPC) scenarios to meet diverse service requirements.

Just like the physical disks in local PC need to be installed before they can be used, EVS disks need to be attached to servers before they can be used. They cannot be used alone. You also need to partition and create file systems on them before they can be used for persistent data storage.


.. figure:: /_static/images/en-us_image_0205523160.png
   :alt: **Figure 1** EVS architecture

   **Figure 1** EVS architecture

-  A system disk runs the server OS. It is like drive C in a PC.

   When a server is created, a system disk is automatically created and attached. You cannot create a system disk separately. The maximum size of a system disk is 1,024 GiB.

-  Data disks store the server data. They are like drive D, drive E, and drive F in a PC.

   Data disks can be created during or after the server creation. If you create data disks during the server creation, the system will automatically attach the data disks to the server. If you create data disks after the server creation, you need to manually attach the data disks. The maximum size of a data disk is 32,768 GiB.

Disk Types
----------

EVS disk types differ in performance. Choose a disk type based on your requirements.

For more information about EVS disk specifications and performance, see *Elastic Volume Service User Guide*.

Device Types
------------

EVS disks have two device types, Virtual Block Device (VBD) and Small Computer System Interface (SCSI).

-  VBD:

   When you create an EVS disk on the management console, **Device Type** of the EVS disk is VBD by default. VBD EVS disks support only simple SCSI read/write commands.

-  SCSI:

   You can create EVS disks whose **Device Type** is SCSI on the management console. These EVS disks support transparent SCSI command transmission, allowing ECS OS to directly access underlying storage media. SCSI EVS disks support both basic and advanced SCSI commands.

   .. note::

      For more information about how to use SCSI EVS disks, for example, how to install a driver for SCSI EVS disks, see "Device Types and Usage Instructions" in the *Elastic Volume Service User Guide*.
