:original_name: en-us_topic_0038024694.html

.. _en-us_topic_0038024694:

Large-Memory ECSs
=================

Overview
--------

Large-memory ECSs provide an even larger amount of memory than memory-optimized ECSs. They are used for applications that require a large amount of memory, rapid data switching, low latency, and process large volumes of data. Large-memory ECSs provide large memory and high computing, storage, and network performance.

-  Applications

   Large-memory ECSs are suitable for applications that require a large amount of memory, rapid data switching, and low latency, and process large volumes of data.

-  Application scenarios

   OLAP and OLTP applications with hyper-threading enabled

Specifications
--------------

.. table:: **Table 1** E3 ECS specifications

   +----------------+-------+--------+---------------------------+-------------+-----------------+--------------+---------------------+--------------------------------+
   | Flavor         | vCPUs | Memory | Maximum/Assured Bandwidth | Maximum PPS | NIC Multi-Queue | Maximum NICs | Virtualization Type | Hardware                       |
   |                |       |        |                           |             |                 |              |                     |                                |
   |                |       | (GiB)  | (Gbit/s)                  | (10,000)    |                 |              |                     |                                |
   +================+=======+========+===========================+=============+=================+==============+=====================+================================+
   | e3.7xlarge.12  | 28    | 348    | 25/12                     | 280         | 8               | 8            | KVM                 | CPU: Intel® Xeon® Skylake 6151 |
   +----------------+-------+--------+---------------------------+-------------+-----------------+--------------+---------------------+--------------------------------+
   | e3.14xlarge.12 | 56    | 696    | 25/25                     | 500         | 16              | 8            | KVM                 |                                |
   +----------------+-------+--------+---------------------------+-------------+-----------------+--------------+---------------------+--------------------------------+
   | e3.26xlarge.14 | 104   | 1466   | 30/20                     | 550         | 16              | 8            | KVM                 | CPU: Intel® Xeon® Skylake 8176 |
   +----------------+-------+--------+---------------------------+-------------+-----------------+--------------+---------------------+--------------------------------+
   | e3.52xlarge.14 | 208   | 2932   | 40/40                     | 1000        | 32              | 8            | KVM                 |                                |
   +----------------+-------+--------+---------------------------+-------------+-----------------+--------------+---------------------+--------------------------------+

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
      | RedHat                            | Redhat Linux Enterprise 7.9 64bit                   |
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

-  The primary and extension NICs of a large-memory ECS have specified application scenarios. For details, see :ref:`Table 3 <en-us_topic_0038024694__table1642803151326>`.

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

   An example is provided as follows:

   An E3 ECS is to be created. It can have a maximum of 60 attached disks, where:

   -  The number of system disks is 1.
   -  The number of EVS disks is at most 59.

   .. note::

      The maximum number of disks attached to an existing large-memory ECS remains unchanged. To attach 60 disks, enable advanced disk. For details, see :ref:`Enabling Advanced Disk <en-us_topic_0122307169>`.
