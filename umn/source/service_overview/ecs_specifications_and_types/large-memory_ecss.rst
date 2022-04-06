.. _en-us_topic_0038024694:

Large-Memory ECSs
=================



.. _en-us_topic_0038024694__section25374905172644:

Overview
--------

Large-memory ECSs provide an even larger amount of memory than memory-optimized ECSs. They are used for applications that require a large amount of memory, rapid data switching, low latency, and process large volumes of data. Large-memory ECSs provide large memory and high computing, storage, and network performance.

-  Applications

   Large-memory ECSs are suitable for applications that require a large amount of memory, rapid data switching, and low latency, and process large volumes of data.

-  Application scenarios

   E3 ECSs: OLAP and OLTP applications with hyper-threading enabled



.. _en-us_topic_0038024694__section60740876172648:

Specifications
--------------



.. _en-us_topic_0038024694__table990906134813:

.. table:: **Table 1** E3 ECS specifications

   +----------------+-------+--------------+------------------------------------+----------------------+-----------------+---------------------+--------------------------------+
   | Flavor         | vCPUs | Memory (GiB) | Maximum/Assured Bandwidth (Gbit/s) | Maximum PPS (10,000) | NIC Multi-Queue | Virtualization Type | Hardware                       |
   +================+=======+==============+====================================+======================+=================+=====================+================================+
   | e3.7xlarge.12  | 28    | 348          | 25/12                              | 280                  | 8               | KVM                 | CPU: Intel® Xeon® Skylake 6151 |
   +----------------+-------+--------------+------------------------------------+----------------------+-----------------+---------------------+--------------------------------+
   | e3.14xlarge.12 | 56    | 696          | 25/25                              | 500                  | 16              | KVM                 |                                |
   +----------------+-------+--------------+------------------------------------+----------------------+-----------------+---------------------+--------------------------------+



.. _en-us_topic_0038024694__section3320087010555:

Notes
-----

-  Large-memory ECSs do not support NIC hot swapping.

-  E3 ECSs support the following OSs that have been verified:

   SUSE Enterprise Linux Server 12 SP2 64bit

   SUSE Enterprise Linux Server 12 SP3 64bit

-  E3 ECSs can use ultra-high I/O EVS disks as the system disk and data disks.

-  The primary and extension NICs of a large-memory ECS have specified application scenarios. For details, see :ref:`Table 2 <en-us_topic_0038024694__table1642803151326>`.

   

.. _en-us_topic_0038024694__table1642803151326:

   .. table:: **Table 2** Application scenarios of the NICs of a large-memory ECS

      +---------------+----------------------------------+--------------------------------------------------------------------------------------+
      | NIC Type      | Application Scenario             | Remarks                                                                              |
      +===============+==================================+======================================================================================+
      | Primary NIC   | Vertical layer 3 communication   | N/A                                                                                  |
      +---------------+----------------------------------+--------------------------------------------------------------------------------------+
      | Extension NIC | Horizontal layer 2 communication | To improve network performance, you can set the MTU of an extension NIC to **8888**. |
      +---------------+----------------------------------+--------------------------------------------------------------------------------------+

-  An ECS can have a maximum of 60 attached disks, including the system disk. For details about constraints, see :ref:`Can I Attach Multiple Disks to an ECS? <en-us_topic_0018073215>`

   An example is provided as follows:

   An E3 ECS is to be created. It can have a maximum of 60 attached disks, where:

   -  The number of system disks is 1.
   -  The number of EVS disks is at most 59.

   .. note::

      The maximum number of disks attached to an existing large-memory ECS remains unchanged. To attach 60 disks, enable advanced disk. For details, see :ref:`Enabling Advanced Disk <en-us_topic_0122307169>`.
