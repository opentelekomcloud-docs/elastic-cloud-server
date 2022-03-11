Large-Memory ECSs
=================

Overview
--------

Large-memory ECSs provide an even larger amount of memory than memory-optimized ECSs. They are used for applications that require a large amount of memory, rapid data switching, low latency, and process large volumes of data. Large-memory ECSs provide large memory and high computing, storage, and network performance.

-  Applications

   Large-memory ECSs are suitable for applications that require a large amount of memory, rapid data switching, and low latency, and process large volumes of data.

-  Application scenarios

   E3 ECSs: OLAP and OLTP applications with hyper-threading enabled

Specifications
--------------



.. _EN-US_TOPIC_0038024694__table990906134813:

.. table:: **Table 1** E3 ECS specifications

   +-------------+-------+-------------+-------------+-------------+-------------+-------------+-------------+
   | Flavor      | vCPUs | Memory      | Maxi        | Maximum PPS | NIC         | Vir         | Hardware    |
   |             |       | (GiB)       | mum/Assured | (10,000)    | Multi-Queue | tualization |             |
   |             |       |             | Bandwidth   |             |             | Type        |             |
   |             |       |             | (Gbit/s)    |             |             |             |             |
   +=============+=======+=============+=============+=============+=============+=============+=============+
   | e3          | 28    | 348         | 25/12       | 280         | 8           | KVM         | CPU: Intel® |
   | .7xlarge.12 |       |             |             |             |             |             | Xeon®       |
   |             |       |             |             |             |             |             | Skylake     |
   |             |       |             |             |             |             |             | 6151        |
   +-------------+-------+-------------+-------------+-------------+-------------+-------------+-------------+
   | e3.         | 56    | 696         | 25/25       | 500         | 16          | KVM         |             |
   | 14xlarge.12 |       |             |             |             |             |             |             |
   +-------------+-------+-------------+-------------+-------------+-------------+-------------+-------------+

Notes
-----

-  Large-memory ECSs do not support NIC hot swapping.

-  E3 ECSs support the following OSs that have been verified:

   SUSE Enterprise Linux Server 12 SP2 64bit

   SUSE Enterprise Linux Server 12 SP3 64bit

-  E3 ECSs can use ultra-high I/O EVS disks as the system disk and data disks.

-  The primary and extension NICs of a large-memory ECS have specified application scenarios. For details, see `Table 2 <#EN-US_TOPIC_0038024694__table1642803151326>`__.
   

.. _EN-US_TOPIC_0038024694__table1642803151326:

   .. table:: **Table 2** Application scenarios of the NICs of a large-memory ECS

      +---------------+----------------------------------+-----------------------------------------------------------------+
      | NIC Type      | Application Scenario             | Remarks                                                         |
      +===============+==================================+=================================================================+
      | Primary NIC   | Vertical layer 3 communication   | N/A                                                             |
      +---------------+----------------------------------+-----------------------------------------------------------------+
      | Extension NIC | Horizontal layer 2 communication | To improve network performance, you can set the MTU of an       |
      |               |                                  | extension NIC to **8888**.                                      |
      +---------------+----------------------------------+-----------------------------------------------------------------+

-  An ECS can have a maximum of 60 attached disks, including the system disk. For details about constraints, see `Can I Attach Multiple Disks to an ECS? <faqs/disk_management/can_i_attach_multiple_disks_to_an_ecs>`__

   An example is provided as follows:

   An E3 ECS is to be created. It can have a maximum of 60 attached disks, where:

   -  The number of system disks is 1.
   -  The number of EVS disks is at most 59.

   |image1|

   The maximum number of disks attached to an existing large-memory ECS remains unchanged. To attach 60 disks, enable advanced disk. For details, see `Enabling Advanced Disk <evs_disks/enabling_advanced_disk>`__.


.. |image1| image:: /_static/images/note_3.0-en-us.png
