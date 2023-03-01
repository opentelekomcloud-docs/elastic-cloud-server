:original_name: en-us_topic_0038024694.html

.. _en-us_topic_0038024694:

Large-Memory ECSs
=================

Overview
--------

Large-memory ECSs provide an even larger amount of memory than memory-optimized ECSs. They are used for applications that require a large amount of memory, rapid data switching, low latency, and capability of processing large volumes of data. Large-memory ECSs provide large memory and high computing, storage, and network performance.

-  Applications

   Large-memory ECSs are suitable for applications that require a large amount of memory, rapid data switching, and low latency, and process large volumes of data.

-  Application scenarios

   OLAP and OLTP applications with hyper-threading enabled

Specifications
--------------

.. table:: **Table 1** E3 ECS specifications

   +----------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+--------------------------------+
   | Flavor         | vCPUs | Memory | Max./Assured Bandwidth | Max. PPS | Max. NIC Queues | Max. NICs | Virtualization | Hardware                       |
   |                |       |        |                        |          |                 |           |                |                                |
   |                |       | (GiB)  | (Gbit/s)               | (10,000) |                 |           |                |                                |
   +================+=======+========+========================+==========+=================+===========+================+================================+
   | e3.7xlarge.12  | 28    | 348    | 25/12                  | 280      | 8               | 8         | KVM            | CPU: Intel® Xeon® Skylake 6151 |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+--------------------------------+
   | e3.14xlarge.12 | 56    | 696    | 25/25                  | 500      | 16              | 8         | KVM            |                                |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+--------------------------------+
   | e3.26xlarge.14 | 104   | 1466   | 30/20                  | 550      | 16              | 8         | KVM            | CPU: Intel® Xeon® Skylake 8176 |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+--------------------------------+
   | e3.52xlarge.14 | 208   | 2932   | 40/40                  | 1,000    | 32              | 8         | KVM            |                                |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+--------------------------------+

Notes
-----

-  Large-memory ECSs do not support NIC hot swapping.

-  Specifications of large-memory ECSs can be modified only within the same flavor family.

-  Affected by the memory loading speed, large-memory ECSs may take longer to start.

-  :ref:`Table 2 <en-us_topic_0038024694__table192771727112217>` lists the OSs supported by large-memory ECSs.

   .. _en-us_topic_0038024694__table192771727112217:

   .. table:: **Table 2** Supported OS versions

      +-----------------------------------+-----------------------------------------------------+
      | OS                                | Version                                             |
      +===================================+=====================================================+
      | CentOS                            | -  CentOS 7.9 64bit                                 |
      |                                   | -  CentOS 7.7 64bit                                 |
      +-----------------------------------+-----------------------------------------------------+
      | EulerOS                           | EulerOS 2.5 64bit                                   |
      +-----------------------------------+-----------------------------------------------------+
      | Fedora                            | -  Fedora 35 64bit                                  |
      |                                   | -  Fedora 34 64bit                                  |
      |                                   | -  Fedora 33 64bit                                  |
      +-----------------------------------+-----------------------------------------------------+
      | OpenSUSE                          | OpenSUSE 15.3 64bit                                 |
      +-----------------------------------+-----------------------------------------------------+
      | Oracle Linux                      | -  Oracle Linux Server release 8.4 64bit            |
      |                                   | -  Oracle Linux Server release 7.6 64bit            |
      +-----------------------------------+-----------------------------------------------------+
      | Red Hat                           | Red Hat Enterprise Linux 7.9 64bit                  |
      +-----------------------------------+-----------------------------------------------------+
      | SUSE                              | -  Novell SUSE Linux Enterprise Server 15 SP3 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 15 SP2 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 15 SP1 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 15 64bit     |
      |                                   | -  Novell SUSE Linux Enterprise Server 12 SP5 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 12 SP4 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 12 SP3 64bit |
      +-----------------------------------+-----------------------------------------------------+
      | SUSE-SAP                          | -  Novell SUSE Linux Enterprise Server 15 SP3 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 15 SP2 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 15 SP1 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 15 64bit     |
      |                                   | -  Novell SUSE Linux Enterprise Server 12 SP5 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 12 SP4 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 12 SP3 64bit |
      +-----------------------------------+-----------------------------------------------------+
      | Ubuntu                            | -  Ubuntu 20.04 server 64bit                        |
      |                                   | -  Ubuntu 18.04 server 64bit                        |
      +-----------------------------------+-----------------------------------------------------+
      | Windows                           | -  Windows Server 2019 Standard 64bit               |
      |                                   | -  Windows Server 2016 Standard 64bit               |
      |                                   | -  Windows Server 2012 R2 Standard 64bit            |
      +-----------------------------------+-----------------------------------------------------+

-  Large-memory ECSs can use ultra-high I/O EVS disks as the system disk and data disks.

-  The primary and extension NICs of a large-memory ECS can be used only in certain scenarios. For details, see :ref:`Table 3 <en-us_topic_0038024694__table1642803151326>`.

   .. _en-us_topic_0038024694__table1642803151326:

   .. table:: **Table 3** Application scenarios of the NICs of a large-memory ECS

      +---------------+----------------------------------+--------------------------------------------------------------------------------------+
      | NIC Type      | Application Scenario             | Remarks                                                                              |
      +===============+==================================+======================================================================================+
      | Primary NIC   | Vertical layer 3 communication   | N/A                                                                                  |
      +---------------+----------------------------------+--------------------------------------------------------------------------------------+
      | Extension NIC | Horizontal layer 2 communication | To improve network performance, you can set the MTU of an extension NIC to **8888**. |
      +---------------+----------------------------------+--------------------------------------------------------------------------------------+

-  An ECS can have a maximum of 60 attached disks, including the system disk. For details about constraints, see :ref:`Can I Attach Multiple Disks to an ECS? <en-us_topic_0018073215>`

   For example, an E3 ECS can have one system disk and 59 EVS disks.

   .. note::

      The maximum number of disks attached to an existing large-memory ECS remains unchanged. If you want to attach 60 disks, enable advanced disk. For details, see :ref:`Enabling Advanced Disk <en-us_topic_0122307169>`.
