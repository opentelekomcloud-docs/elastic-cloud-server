.. _en-us_topic_0093492522:

Expanding the Capacity of an EVS Disk
=====================================

Scenarios
---------

When your disk capacity is insufficient, you can handle the insufficiency by expanding the disk capacity.

Procedure
---------

The capacity of an EVS disk can be expanded in either of the following ways:

-  Create an EVS disk and attach it to an ECS.

-  Expand the capacity of an existing EVS disk. The capacities of both system disks and data disks can be expanded.

   You can expand the disk capacities when the EVS disks are in the **In-use** or **Available** state.

   -  Expanding an **In-use** EVS disk means that the to-be-expanded EVS disk has been attached to an ECS. Only certain ECS OSs support the expansion of **In-use** EVS disks. For details, see "Expanding an In-use EVS Disk" in *Elastic Volume Service User Guide*.
   -  Expanding an **Available** EVS disk means that the to-be-expanded EVS disk has not been attached to an ECS. For details, see "Expanding an Available EVS Disk" in *Elastic Volume Service User Guide*.

.. note::

   After the capacity is expanded through the management console, only the storage capacity of the EVS disk is expanded. To use the expanded capacity, you also need to log in to the ECS and expand the partition and file system.
