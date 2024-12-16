:original_name: en-us_topic_0035550301.html

.. _en-us_topic_0035550301:

Memory-optimized ECSs
=====================

Overview
--------

-  M7n ECSs use the third-generation Intel® Xeon® Scalable processors to provide enhanced computing, security, and stability. Each M7n ECS can have a maximum number of 96 vCPUs and a memory speed of 3,200 MHz, and provide a secure and trusted cloud environment for memory-intensive computing applications.
-  M4 ECSs use the second-generation Intel® Xeon® Scalable processors with technologies optimized to offer powerful and stable computing performance. Using 25GE high-speed intelligent NICs, M4 ECSs provide a maximum memory size of 512 GiB based on DDR4 for memory-intensive applications with high requirements on network bandwidth and Packets Per Second (PPS).
-  M3 ECSs are developed based on the KVM virtualization platform and designed for processing large-scale data sets in the memory. They use Intel® Xeon® Scalable processors, network acceleration engines, and DPDK rapid packet processing mechanism to provide higher network performance and up to 512 GiB of DDR4 memory for memory-intensive computing applications.

Specifications
--------------

.. table:: **Table 1** M7n ECS specifications

   +----------------+-------+--------+------------------------+----------+-----------------+-----------+-------------------------------------+----------------+
   | Flavor         | vCPUs | Memory | Max./Assured Bandwidth | Max. PPS | Max. NIC Queues | Max. NICs | EVS Basic Bandwidth/Burst Bandwidth | Virtualization |
   |                |       |        |                        |          |                 |           |                                     |                |
   |                |       | (GiB)  | (Gbit/s)               | (10,000) |                 |           | (Gbit/s)                            |                |
   +================+=======+========+========================+==========+=================+===========+=====================================+================+
   | m7n.large.8    | 2     | 16     | 4/0.8                  | 40       | 2               | 2         | 1.5/6                               | KVM            |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+-------------------------------------+----------------+
   | m7n.xlarge.8   | 4     | 32     | 8/1.6                  | 80       | 2               | 3         | 2/6                                 | KVM            |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+-------------------------------------+----------------+
   | m7n.2xlarge.8  | 8     | 64     | 15/3                   | 150      | 4               | 4         | 3/6                                 | KVM            |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+-------------------------------------+----------------+
   | m7n.3xlarge.8  | 12    | 96     | 17/5                   | 200      | 4               | 6         | 4/6                                 | KVM            |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+-------------------------------------+----------------+
   | m7n.4xlarge.8  | 16    | 128    | 20/6                   | 280      | 8               | 8         | 5/6                                 | KVM            |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+-------------------------------------+----------------+
   | m7n.6xlarge.8  | 24    | 192    | 25/9                   | 400      | 8               | 8         | 6/None                              | KVM            |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+-------------------------------------+----------------+
   | m7n.8xlarge.8  | 32    | 256    | 30/12                  | 550      | 16              | 8         | 8/None                              | KVM            |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+-------------------------------------+----------------+
   | m7n.12xlarge.8 | 48    | 384    | 35/18                  | 750      | 16              | 8         | 12/None                             | KVM            |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+-------------------------------------+----------------+
   | m7n.16xlarge.8 | 64    | 512    | 36/24                  | 800      | 28              | 8         | 16/None                             | KVM            |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+-------------------------------------+----------------+
   | m7n.24xlarge.8 | 96    | 768    | 40/36                  | 850      | 32              | 8         | 24/None                             | KVM            |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+-------------------------------------+----------------+

.. table:: **Table 2** M4 ECS specifications

   +---------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+-------------------------------------+
   | Flavor        | vCPUs | Memory | Max./Assured Bandwidth | Max. PPS | Max. NIC Queues | Max. NICs | Virtualization | Hardware                            |
   |               |       |        |                        |          |                 |           |                |                                     |
   |               |       | (GiB)  | (Gbit/s)               | (10,000) |                 |           |                |                                     |
   +===============+=======+========+========================+==========+=================+===========+================+=====================================+
   | m4.large.8    | 2     | 16     | 4/1.2                  | 40       | 2               | 2         | KVM            | CPU: Intel® Xeon® Cascade Lake 6266 |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+-------------------------------------+
   | m4.xlarge.8   | 4     | 32     | 8/2.4                  | 80       | 2               | 3         | KVM            |                                     |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+-------------------------------------+
   | m4.2xlarge.8  | 8     | 64     | 15/4.5                 | 150      | 4               | 4         | KVM            |                                     |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+-------------------------------------+
   | m4.3xlarge.8  | 12    | 96     | 17/7                   | 200      | 4               | 6         | KVM            |                                     |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+-------------------------------------+
   | m4.4xlarge.8  | 16    | 128    | 20/9                   | 280      | 8               | 8         | KVM            |                                     |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+-------------------------------------+
   | m4.6xlarge.8  | 24    | 192    | 25/14                  | 400      | 8               | 8         | KVM            |                                     |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+-------------------------------------+
   | m4.8xlarge.8  | 32    | 256    | 30/18                  | 550      | 16              | 8         | KVM            |                                     |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+-------------------------------------+
   | m4.16xlarge.8 | 64    | 512    | 40/36                  | 1,000    | 32              | 8         | KVM            |                                     |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+-------------------------------------+
   | m4.2xlarge.16 | 8     | 128    | 15/4.5                 | 150      | 4               | 4         | KVM            |                                     |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+-------------------------------------+
   | m4.2xlarge.32 | 8     | 256    | 15/4.5                 | 150      | 4               | 4         | KVM            |                                     |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+-------------------------------------+

.. table:: **Table 3** M3 ECS specifications

   +---------------+-------+--------+------------------------+----------+-----------------+-----------+---------------------+----------------+--------------------------------+
   | Flavor        | vCPUs | Memory | Max./Assured Bandwidth | Max. PPS | Max. NIC Queues | Max. NICs | EVS Basic Bandwidth | Virtualization | Hardware                       |
   |               |       |        |                        |          |                 |           |                     |                |                                |
   |               |       | (GiB)  | (Gbit/s)               | (10,000) |                 |           | (Gbit/s)            |                |                                |
   +===============+=======+========+========================+==========+=================+===========+=====================+================+================================+
   | m3.large.8    | 2     | 16     | 1.5/0.6                | 30       | 2               | 12        | 1                   | KVM            | CPU: Intel® Xeon® Skylake 6151 |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+---------------------+----------------+--------------------------------+
   | m3.xlarge.8   | 4     | 32     | 3/1.1                  | 50       | 2               | 12        | 1.5.                | KVM            |                                |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+---------------------+----------------+--------------------------------+
   | m3.2xlarge.8  | 8     | 64     | 5/2                    | 90       | 4               | 12        | 2                   | KVM            |                                |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+---------------------+----------------+--------------------------------+
   | m3.4xlarge.8  | 16    | 128    | 10/4.5                 | 130      | 4               | 12        | 3                   | KVM            |                                |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+---------------------+----------------+--------------------------------+
   | m3.8xlarge.8  | 32    | 256    | 15/9                   | 260      | 8               | 12        | 4                   | KVM            |                                |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+---------------------+----------------+--------------------------------+
   | m3.15xlarge.8 | 60    | 512    | 17/17                  | 500      | 16              | 12        | 8                   | KVM            |                                |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+---------------------+----------------+--------------------------------+

Scenarios
---------

-  High-performance relational (MySQL) and NoSQL (MongoDB and Cassandra) databases
-  Distributed web scale cache stores that provide in-memory caching of key-value type data (Memcached and Redis)
-  Applications processing big unstructured data in real time (financial services, Hadoop/Spark clusters)
-  High-performance computing (HPC) and electronic design automation (EDA)

Notes
-----

:ref:`Table 4 <en-us_topic_0035550301__table192771727112217>` lists the OSs supported by memory-optimized ECSs.

.. _en-us_topic_0035550301__table192771727112217:

.. table:: **Table 4** Supported OS versions

   +-----------------------------------+-----------------------------------------------------+
   | OS                                | Version                                             |
   +===================================+=====================================================+
   | Alma                              | Alma 8 64bit                                        |
   +-----------------------------------+-----------------------------------------------------+
   | CentOS                            | -  CentOS Stream 9.6 64bit                          |
   |                                   | -  CentOS Stream 8.6 64bit                          |
   |                                   | -  CentOS 8.5 64bit                                 |
   |                                   | -  CentOS 8.4 64bit                                 |
   |                                   | -  CentOS 8.3 64bit                                 |
   |                                   | -  CentOS 8.2 64bit                                 |
   |                                   | -  CentOS 8.1 64bit                                 |
   |                                   | -  CentOS 7.9 64bit                                 |
   |                                   | -  CentOS 7.7 64bit                                 |
   +-----------------------------------+-----------------------------------------------------+
   | Debian                            | -  Debian GNU/Linux 12.0.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.7.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.6.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.5.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.4.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.3.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.2.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.1.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.0.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.13.0 64bit                   |
   |                                   | -  Debian GNU/Linux 10.12.0 64bit                   |
   |                                   | -  Debian GNU/Linux 10.11.0 64bit                   |
   |                                   | -  Debian GNU/Linux 10.10.0 64bit                   |
   |                                   | -  Debian GNU/Linux 10.9.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.8.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.7.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.6.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.5.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.4.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.3.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.2.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.1.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10 64bit                        |
   +-----------------------------------+-----------------------------------------------------+
   | EulerOS                           | -  EulerOS 2.12 64bit                               |
   |                                   | -  EulerOS 2.11 64bit                               |
   |                                   | -  EulerOS 2.10 64bit                               |
   |                                   | -  EulerOS 2.8 64bit                                |
   |                                   | -  EulerOS 2.7 64bit                                |
   |                                   | -  EulerOS 2.5 64bit                                |
   +-----------------------------------+-----------------------------------------------------+
   | Fedora                            | -  Fedora 39 64bit                                  |
   |                                   | -  Fedora 38 64bit                                  |
   |                                   | -  Fedora 37 64bit                                  |
   |                                   | -  Fedora 36 64bit                                  |
   |                                   | -  Fedora 35 64bit                                  |
   |                                   | -  Fedora 34 64bit                                  |
   |                                   | -  Fedora 33 64bit                                  |
   |                                   | -  Fedora 32 64bit                                  |
   |                                   | -  Fedora 31 64bit                                  |
   +-----------------------------------+-----------------------------------------------------+
   | OpenSUSE                          | -  OpenSUSE 15.5 64bit                              |
   |                                   | -  OpenSUSE 15.4 64bit                              |
   |                                   | -  OpenSUSE 15.3 64bit                              |
   |                                   | -  OpenSUSE 15.2 64bit                              |
   +-----------------------------------+-----------------------------------------------------+
   | Oracle Linux                      | -  Oracle Linux Server release 8.4 64bit            |
   |                                   | -  Oracle Linux Server release 7.6 64bit            |
   +-----------------------------------+-----------------------------------------------------+
   | Red Hat                           | -  Red Hat Enterprise Linux 9.1 64bit               |
   |                                   | -  Red Hat Enterprise Linux 9.0 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.7 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.6 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.5 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.4 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.3 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.2 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.1 64bit               |
   |                                   | -  Red Hat Enterprise Linux 7.9 64bit               |
   |                                   | -  Red Hat Enterprise Linux 6.10 64bit              |
   +-----------------------------------+-----------------------------------------------------+
   | Rocky                             | -  9.2 64bit                                        |
   |                                   | -  9.1 64bit                                        |
   |                                   | -  9.0 64bit                                        |
   |                                   | -  8.8 64bit                                        |
   |                                   | -  8.7 64bit                                        |
   |                                   | -  8.6 64bit                                        |
   |                                   | -  8.5 64bit                                        |
   |                                   | -  8.4 64bit                                        |
   |                                   | -  8.3 64bit                                        |
   |                                   | -  8 64bit                                          |
   +-----------------------------------+-----------------------------------------------------+
   | SUSE                              | -  Novell SUSE Linux Enterprise Server 15 SP5 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP4 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP3 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP2 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP1 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 64bit     |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP5 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP4 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP3 64bit |
   +-----------------------------------+-----------------------------------------------------+
   | Ubuntu                            | -  Ubuntu 22.04 Server 64bit                        |
   |                                   | -  Ubuntu 20.04 server 64bit                        |
   |                                   | -  Ubuntu 18.04 server 64bit                        |
   +-----------------------------------+-----------------------------------------------------+
   | Windows                           | -  Windows Server 2022 Standard 64bit               |
   |                                   | -  Windows Server 2022 Datacenter 64bit             |
   |                                   | -  Windows Server 2019 Datacenter 64bit             |
   |                                   | -  Windows Server 2019 Standard 64bit               |
   |                                   | -  Windows Server 2016 Standard 64bit               |
   |                                   | -  Windows Server 2012 R2 Standard 64bit            |
   +-----------------------------------+-----------------------------------------------------+
   | openEuler                         | -  openEuler 22.03 SP1 64bit                        |
   |                                   | -  openEuler 22.03 64bit                            |
   |                                   | -  openEuler 20.03 SP3 64bit                        |
   |                                   | -  openEuler 20.03 SP2 64bit                        |
   |                                   | -  openEuler 20.03 SP1 64bit                        |
   |                                   | -  openEuler 20.03 64bit                            |
   +-----------------------------------+-----------------------------------------------------+
