:original_name: en-us_topic_0035470099.html

.. _en-us_topic_0035470099:

Disk-intensive ECSs
===================

Overview
--------

D2 ECSs are developed based on KVM virtualization. They use local storage and provide high storage performance and intranet bandwidth for distributed Hadoop computing, large data warehouse, distributed file system, and log/data processing.

Specifications
--------------

.. table:: **Table 1** D2 ECS specifications

   +---------------+-------+--------+--------------------------------+------------------+-----------------+----------------+----------------+-------------+-----------------------------+
   | Flavor        | vCPUs | Memory | Max./Assured Network Bandwidth | Max. Network PPS | Max. NIC Queues | Max. EVS Disks | Virtualization | Local Disks | Hardware                    |
   |               |       |        |                                |                  |                 |                |                |             |                             |
   |               |       | (GiB)  | (Gbit/s)                       | (10,000)         |                 |                |                | (GiB)       |                             |
   +===============+=======+========+================================+==================+=================+================+================+=============+=============================+
   | d2.xlarge.8   | 4     | 32     | 4/1.4                          | 40               | 2               | 31             | KVM            | 2 x 1675    | CPU: Intel® Xeon® Gold 6151 |
   +---------------+-------+--------+--------------------------------+------------------+-----------------+----------------+----------------+-------------+-----------------------------+
   | d2.2xlarge.8  | 8     | 64     | 6/2.8                          | 80               | 4               | 31             | KVM            | 4 x 1675    |                             |
   +---------------+-------+--------+--------------------------------+------------------+-----------------+----------------+----------------+-------------+-----------------------------+
   | d2.4xlarge.8  | 16    | 128    | 10/5.6                         | 160              | 6               | 31             | KVM            | 8 x 1675    |                             |
   +---------------+-------+--------+--------------------------------+------------------+-----------------+----------------+----------------+-------------+-----------------------------+
   | d2.6xlarge.8  | 24    | 192    | 15/8.5                         | 250              | 8               | 31             | KVM            | 12 x 1675   |                             |
   +---------------+-------+--------+--------------------------------+------------------+-----------------+----------------+----------------+-------------+-----------------------------+
   | d2.8xlarge.8  | 32    | 256    | 17/11                          | 320              | 8               | 31             | KVM            | 16 x 1675   |                             |
   +---------------+-------+--------+--------------------------------+------------------+-----------------+----------------+----------------+-------------+-----------------------------+
   | d2.15xlarge.9 | 60    | 540    | 17/17                          | 500              | 16              | 31             | KVM            | 24 x 1675   |                             |
   +---------------+-------+--------+--------------------------------+------------------+-----------------+----------------+----------------+-------------+-----------------------------+

Scenarios
---------

-  Applications

   Disk-intensive ECSs are suitable for applications that require large volumes of data to process, high I/O performance, and rapid data switching and processing, such as MapReduce, Hadoop, and data-intensive computing.

-  Application scenarios

   Big data computing, network file systems, data processing, MapReduce, Hadoop, and data-intensive computing

D2 ECS Features
---------------

-  D2 ECSs use local disks to provide high sequential read/write performance and low latency, improving file read/write performance.
-  D2 ECSs provide powerful and stable computing capabilities, ensuring efficient data processing.
-  D2 ECSs with a vCPU/memory ratio of 1:8 process large volumes of data.
-  D2 ECSs provide high intranet performance, including high intranet bandwidth and packets per second (PPS), meeting requirements for data exchange between ECSs during peak hours.
-  Each D2 ECS supports a maximum configuration of 24 local disks, 60 vCPUs, and 540 GiB memory.

.. table:: **Table 2** Specifications of a Single SAS HDD Disk Attached to a D2 ECS

   ================== ===================
   Metric             Performance
   ================== ===================
   Disk capacity      1,675 GiB
   Maximum throughput 230 MB/s
   Access latency     Within milliseconds
   ================== ===================

Notes
-----

-  :ref:`Table 3 <en-us_topic_0035470099__table192771727112217>` lists the OSs supported by disk-intensive ECSs.

   .. _en-us_topic_0035470099__table192771727112217:

   .. table:: **Table 3** Supported OS versions

      +-----------------------------------+---------------------------------------------------+
      | OS                                | Version                                           |
      +===================================+===================================================+
      | AlmaLinux                         | -  AlmaLinux 9 64bit                              |
      |                                   | -  AlmaLinux 8 64bit                              |
      +-----------------------------------+---------------------------------------------------+
      | CentOS                            | CentOS Stream 9 64bit                             |
      +-----------------------------------+---------------------------------------------------+
      | Debian                            | -  Debian GNU/Linux 13 64bit                      |
      |                                   | -  Debian GNU/Linux 12 64bit                      |
      +-----------------------------------+---------------------------------------------------+
      | EulerOS                           | -  EulerOS 2.10 64bit                             |
      |                                   | -  Cloud-EulerOS 2.0                              |
      +-----------------------------------+---------------------------------------------------+
      | Fedora                            | -  Fedora Linux 43 64bit                          |
      |                                   | -  Fedora Linux 41 64bit                          |
      +-----------------------------------+---------------------------------------------------+
      | openSUSE                          | openSUSE Leap 16.0 64bit                          |
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
      | SUSE-SAP                          | Novell SUSE Linux Enterprise Server 15.7          |
      +-----------------------------------+---------------------------------------------------+
      | Ubuntu                            | -  Ubuntu 24.04 server 64bit                      |
      |                                   | -  Ubuntu 22.04 server 64bit                      |
      +-----------------------------------+---------------------------------------------------+
      | Windows                           | -  Windows Server 2025 Standard 64bit             |
      |                                   | -  Windows Server 2025 Standard Core 64bit        |
      |                                   | -  Windows Server 2025 Datacenter 64bit           |
      |                                   | -  Windows Server 2022 Standard 64bit             |
      |                                   | -  Windows Server 2022 Standard Core 64bit        |
      |                                   | -  Windows Server 2022 Datacenter 64bit           |
      |                                   | -  Windows Server 2019 Standard 64bit             |
      |                                   | -  Windows Server 2019 Standard Core 64bit        |
      |                                   | -  Windows Server 2019 Datacenter 64bit           |
      |                                   | -  Windows Server 2016 Standard 64bit             |
      |                                   | -  Windows Server 2016 Standard Core 64bit        |
      |                                   | -  Windows Server 2016 Datacenter 64bit           |
      +-----------------------------------+---------------------------------------------------+

-  If the host where a D2 ECS is deployed becomes faulty, the ECS cannot be migrated.

-  To improve network performance, you can set the NIC MTU of a D2 ECS to **8888**.

-  D2 ECSs do not support specification modification.

-  D2 ECSs do not support local disk snapshots or backups.

-  D2 ECSs do not support OS reinstallation or change.

-  D2 ECSs can use both local disks and EVS disks to store data. In addition, they can have EVS disks attached to provide a larger storage size. Note the following when using the two types of storage media:

   -  Only an EVS disk, not a local disk, can be used as the system disk of a D2 ECS.

   -  Both EVS disks and local disks can be used as data disks of a D2 ECS.

   -  A maximum of 60 disks (including VBD, SCSI, and local disks) can be attached to a D2 ECS. Among the 60 disks, the maximum number of SCSI disks is 30, and the VBD disks (including the system disk) is 24. For details, see :ref:`Can I Attach Multiple Disks to an ECS? <en-us_topic_0018073215>`

      .. note::

         The maximum number of disks attached to an existing D2 ECS remains unchanged.

   -  You are advised to use World Wide Names (WWNs), but not drive letters, in applications to perform operations on local disks to prevent drive letter drift (low probability) on Linux. Take local disk attachment as an example:

      If the local disk WWN is wwn-0x50014ee2b14249f6, run the **mount /dev/disk/by-id/wwn-0x50014ee2b14249f6** command.

      .. note::

         How can I view the local disk WWN?

         #. Log in to the ECS.

         #. Run the following command:

            **ll /dev/disk/by-id**

-  The local disk data of a D2 ECS may be lost if an exception occurs, such as physical server breakdown or local disk damage. If your application does not use the data reliability architecture, it is a good practice to use EVS disks to build your ECS.

-  When a D2 ECS is deleted, its local disk data will also be automatically deleted. Back up data in advance. Deleting local disk data will increase the time needed to release resources compared with ECSs without local disks.

-  Do not store service data in local disks for a long time. Instead, store it in EVS disks. To improve data security, use a high availability architecture and back up data in a timely manner.

-  Local disks can only be purchased during D2 ECS creation. The quantity and capacity of your local disks are determined according to the specifications of your ECS.
