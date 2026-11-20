:original_name: en-us_topic_0038024694.html

.. _en-us_topic_0038024694:

Large-Memory ECSs
=================

Overview
--------

Large-memory ECSs provide an even larger amount of memory than memory-optimized ECSs. They are used for applications that require a large amount of memory, rapid data exchange and processing, low latency, and capability of processing large volumes of data. Large-memory ECSs provide large memory and high computing, storage, and network performance.

-  Features

   The applications are for large-scale, enterprise-class, in-memory applications, process large volumes of data, and require rapid data switching, processing and low latency storage resource.

-  Scenarios

   OLTP and OLAP scenarios

Specifications
--------------

.. table:: **Table 1** E6 ECS specifications

   +----------------+-------+--------+--------------------------------+------------------+-----------------+-----------+----------------+----------------+--------------------------------+
   | Flavor         | vCPUs | Memory | Max./Assured Network Bandwidth | Max. Network PPS | Max. NIC Queues | Max. NICs | Max. EVS Disks | Virtualization | Hardware                       |
   |                |       |        |                                |                  |                 |           |                |                |                                |
   |                |       | (GiB)  | (Gbit/s)                       | (10,000)         |                 |           |                |                |                                |
   +================+=======+========+================================+==================+=================+===========+================+================+================================+
   | e6.26xlarge.28 | 104   | 2,948  | 30/20                          | 550              | 16              | 8         | 60             | KVM            | CPU: Intel® Xeon® Skylake 8280 |
   +----------------+-------+--------+--------------------------------+------------------+-----------------+-----------+----------------+----------------+--------------------------------+
   | e6.52xlarge.28 | 208   | 5,896  | 40/40                          | 1,000            | 32              | 8         | 60             | KVM            |                                |
   +----------------+-------+--------+--------------------------------+------------------+-----------------+-----------+----------------+----------------+--------------------------------+

.. table:: **Table 2** E3 ECS specifications

   +----------------+-------+--------+--------------------------------+------------------+-----------------+-----------+----------------+----------------+--------------------------------+
   | Flavor         | vCPUs | Memory | Max./Assured Network Bandwidth | Max. Network PPS | Max. NIC Queues | Max. NICs | Max. EVS Disks | Virtualization | Hardware                       |
   |                |       |        |                                |                  |                 |           |                |                |                                |
   |                |       | (GiB)  | (Gbit/s)                       | (10,000)         |                 |           |                |                |                                |
   +================+=======+========+================================+==================+=================+===========+================+================+================================+
   | e3.7xlarge.12  | 28    | 348    | 25/12                          | 280              | 8               | 8         | 60             | KVM            | CPU: Intel® Xeon® Skylake 6151 |
   +----------------+-------+--------+--------------------------------+------------------+-----------------+-----------+----------------+----------------+--------------------------------+
   | e3.14xlarge.12 | 56    | 696    | 25/25                          | 500              | 16              | 8         | 60             | KVM            |                                |
   +----------------+-------+--------+--------------------------------+------------------+-----------------+-----------+----------------+----------------+--------------------------------+
   | e3.26xlarge.14 | 104   | 1,466  | 30/20                          | 540              | 16              | 8         | 60             | KVM            | CPU: Intel® Xeon® Skylake 8176 |
   +----------------+-------+--------+--------------------------------+------------------+-----------------+-----------+----------------+----------------+--------------------------------+
   | e3.52xlarge.14 | 208   | 2,932  | 40/40                          | 1,000            | 32              | 8         | 60             | KVM            |                                |
   +----------------+-------+--------+--------------------------------+------------------+-----------------+-----------+----------------+----------------+--------------------------------+

Notes
-----

-  Large-memory ECSs do not support NIC hot swapping.

-  Specifications of large-memory ECSs can be modified only within the same flavor family.

-  Affected by the memory loading speed, large-memory ECSs may take longer to start.

-  :ref:`Table 3 <en-us_topic_0038024694__table192771727112217>` lists the OSs supported by large-memory ECSs.

   .. _en-us_topic_0038024694__table192771727112217:

   .. table:: **Table 3** Supported OS versions

      +-----------------------------------+---------------------------------------------------+
      | OS                                | Version                                           |
      +===================================+===================================================+
      | AlmaLinux                         | -  AlmaLinux 9 64bit                              |
      |                                   | -  AlmaLinux 8 64bit                              |
      +-----------------------------------+---------------------------------------------------+
      | CentOS                            | CentOS Stream 9 64bit                             |
      +-----------------------------------+---------------------------------------------------+
      | Debian                            | -  Debian GNU/Linux 12 64bit                      |
      |                                   | -  Debian GNU/Linux 11 64bit                      |
      +-----------------------------------+---------------------------------------------------+
      | EulerOS                           | EulerOS 2.0 64bit                                 |
      +-----------------------------------+---------------------------------------------------+
      | Fedora                            | -  Fedora Linux 43 64bit                          |
      |                                   | -  Fedora Linux 41 64bit                          |
      +-----------------------------------+---------------------------------------------------+
      | OpenSUSE                          | openSUSE Leap 16.0 64bit                          |
      +-----------------------------------+---------------------------------------------------+
      | Oracle Linux                      | -  Oracle Linux Server 9 64bit                    |
      |                                   | -  Oracle Linux Server 8 64bit                    |
      +-----------------------------------+---------------------------------------------------+
      | Red Hat                           | -  Red Hat Enterprise Linux Server 9 64bit        |
      |                                   | -  Red Hat Enterprise Linux Server 8 64bit        |
      |                                   | -  Red Hat Enterprise Linux Server 7 64bit        |
      +-----------------------------------+---------------------------------------------------+
      | Rocky Linux                       | -  Rocky Linux 9 64bit                            |
      |                                   | -  Rocky Linux 8 64bit                            |
      +-----------------------------------+---------------------------------------------------+
      | SUSE                              | -  Novell SUSE Linux Enterprise Server 16.0 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 15.7 64bit |
      +-----------------------------------+---------------------------------------------------+
      | Ubuntu                            | -  Ubuntu 24.04 server 64bit                      |
      |                                   | -  Ubuntu 22.04 server 64bit                      |
      +-----------------------------------+---------------------------------------------------+
      | Windows                           | -  Windows Server 2025 Standard 64bit             |
      |                                   | -  Windows Server 2025 Datacenter 64bit           |
      |                                   | -  Windows Server 2022 Standard 64bit             |
      |                                   | -  Windows Server 2022 Datacenter 64bit           |
      |                                   | -  Windows Server 2019 Standard 64bit             |
      |                                   | -  Windows Server 2019 Datacenter 64bit           |
      |                                   | -  Windows Server 2016 Standard 64bit             |
      |                                   | -  Windows Server 2016 Datacenter 64bit           |
      +-----------------------------------+---------------------------------------------------+

-  Large-memory ECSs can use ultra-high I/O EVS disks as the system disk and data disks.

-  The primary and extension NICs of a large-memory ECS can only be used in the scenarios listed in :ref:`Table 4 <en-us_topic_0038024694__table1642803151326>`.

   .. _en-us_topic_0038024694__table1642803151326:

   .. table:: **Table 4** Application scenarios of the NICs of a large-memory ECS

      +---------------+----------------------------------+--------------------------------------------------------------------------------------+
      | NIC Type      | Application Scenario             | Remarks                                                                              |
      +===============+==================================+======================================================================================+
      | Primary NIC   | Vertical layer 3 communication   | N/A                                                                                  |
      +---------------+----------------------------------+--------------------------------------------------------------------------------------+
      | Extension NIC | Horizontal layer 2 communication | To improve network performance, you can set the MTU of an extension NIC to **8888**. |
      +---------------+----------------------------------+--------------------------------------------------------------------------------------+

-  An ECS can have a maximum of 60 attached disks, including the system disk. For details about constraints, see :ref:`Can I Attach Multiple Disks to an ECS? <en-us_topic_0018073215>`

   For example, an E3 ECS can have one system disk and 59 data disks.
