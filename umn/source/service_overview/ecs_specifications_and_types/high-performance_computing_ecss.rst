:original_name: en-us_topic_0035470100.html

.. _en-us_topic_0035470100:

High-Performance Computing ECSs
===============================

Overview
--------

H2 ECSs are designed to meet high-end computational needs, such as molecular modeling and computational fluid dynamics. In addition to the substantial CPU power, the H2 ECSs offer diverse options for low-latency RDMA networking using EDR InfiniBand NICs to support memory-intensive computational requirements.

HL1 ECSs are the second generation of high-computing ECSs, featuring large memory capacity. They are interconnected with each other using 100 Gbit/s RDMA InfiniBand NICs and support 56 Gbit shared high I/O storage.

Specifications
--------------

.. table:: **Table 1** H2 ECS specifications

   +---------------+-------+--------------+---------------------------------+-------------------+-----------------+-----------+----------------+-------------+-----------------+---------------------------+------------------------------+
   | Flavor        | vCPUs | Memory (GiB) | Max./Assured Bandwidth (Gbit/s) | Max. PPS (10,000) | Max. NIC Queues | Max. NICs | Virtualization | Local Disks | Local Disk (TB) | Network                   | Hardware                     |
   +===============+=======+==============+=================================+===================+=================+===========+================+=============+=================+===========================+==============================+
   | h2.3xlarge.10 | 16    | 128          | 13/13                           | 90                | 8               | 12        | KVM            | 1           | 3.2             | 100 Gbit/s EDR InfiniBand | CPU: Intel® Xeon® E5-2667 v4 |
   +---------------+-------+--------------+---------------------------------+-------------------+-----------------+-----------+----------------+-------------+-----------------+---------------------------+------------------------------+
   | h2.3xlarge.20 | 16    | 256          | 13/13                           | 90                | 8               | 12        | KVM            | 1           | 3.2             | 100 Gbit/s EDR InfiniBand |                              |
   +---------------+-------+--------------+---------------------------------+-------------------+-----------------+-----------+----------------+-------------+-----------------+---------------------------+------------------------------+

.. table:: **Table 2** Hl1 ECS specifications

   +---------------+-------+--------------+---------------------------------+-------------------+-----------------+-----------+----------------+---------------------------+----------------------------------------+
   | Flavor        | vCPUs | Memory (GiB) | Max./Assured Bandwidth (Gbit/s) | Max. PPS (10,000) | Max. NIC Queues | Max. NICs | Virtualization | Network                   | Hardware                               |
   +===============+=======+==============+=================================+===================+=================+===========+================+===========================+========================================+
   | hl1.8xlarge.8 | 32    | 256          | 9/9                             | 90                | 8               | 12        | KVM            | 100 Gbit/s EDR InfiniBand | CPU: Intel® Xeon® Processor E5-2690 v4 |
   +---------------+-------+--------------+---------------------------------+-------------------+-----------------+-----------+----------------+---------------------------+----------------------------------------+

Scenarios
---------

-  Applications

   H2 and Hl1: High-performance computing (HPC), big data, and Artificial Intelligence (AI)

-  Application scenarios

   H2 and Hl1

   -  High-performance hardware: The ratio of memory to vCPU is 8:1, and a large number of multi-thread physical CPUs are available to provide high-performance storage I/O and high-throughput network connections.
   -  Designed for HPC clusters: Multiple Hl1 ECSs can be clustered to install scalable, clustered file system, such as Lustre. HPC applications running on H2 ECSs can read and modify the data stored in the ECSs.
   -  RDMA network connection: Same as H2 ECSs, Hl1 ECSs also offer RDMA network using EDR 100 Gbit/s InfiniBand NICs. Hl1 ECSs can communicate with H2 ECSs with RDMA protocol. In addition, Hl1 ECSs can access EVS disks over the RDMA protocol, which allows up to 56 Gbit/s storage bandwidth.

-  Application scenarios

   H2 and Hl1 ECSs provide computing capabilities for clusters with a large memory, good connectivity between nodes, and high storage I/O. The typical application scenarios include HPC, big data, and AI. In HPC solution, Hl1 ECSs are perfectly suited for the Lustre parallel distributed file system, generally used for large-scale cluster computing.

   For example, in HPC scenario, H2 ECSs can be used as compute nodes, and Hl1 ECSs can be used as storage nodes.

Features
--------

High-performance computing ECSs have the following features:

-  Large memory capacity and more processor cores than other types of ECSs

-  Up to 32 vCPUs

-  H2 and Hl1 ECSs use InfiniBand NICs that provide a bandwidth of 100 Gbit/s.

-  Hl1 ECSs can use the following types of EVS disks as system disk and data disk:

   High I/O (performance-optimized I)

   Ultra-high I/O (latency-optimized)

-  Hl1 ECSs support 56 Gbit shared high I/O storage.

   To support 56 Gbit shared high I/O storage, you only need to attach high I/O (performance-optimized I) or ultra-high I/O (latency-optimized) EVS disks to target Hl1 ECSs.

Notes on Using H2 ECSs
----------------------

-  H2 ECSs do not support OS reinstallation or change.

-  H2 ECSs do not support specifications modification.

-  H2 ECSs do not support cold migration, live migration, or HA.

-  :ref:`Table 3 <en-us_topic_0035470100__table192771727112217>` lists the OSs supported by H2 ECSs.

   .. _en-us_topic_0035470100__table192771727112217:

   .. table:: **Table 3** Supported OS versions

      +-----------------------------------+-----------------------------------------------------+
      | OS                                | Version                                             |
      +===================================+=====================================================+
      | CentOS                            | -  CentOS 7.9 64bit                                 |
      |                                   | -  CentOS 7.7 64bit                                 |
      +-----------------------------------+-----------------------------------------------------+
      | Oracle Linux                      | -  Oracle Linux Server release 8.4 64bit            |
      |                                   | -  Oracle Linux Server release 7.6 64bit            |
      +-----------------------------------+-----------------------------------------------------+
      | Red Hat                           | Red Hat Enterprise Linux 7.9 64bit                  |
      +-----------------------------------+-----------------------------------------------------+
      | SUSE                              | -  Novell SUSE Linux Enterprise Server 15 SP3 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 15 SP2 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 12 SP4 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 12 SP3 64bit |
      +-----------------------------------+-----------------------------------------------------+

-  H2 ECSs use InfiniBand NICs that provide a bandwidth of 100 Gbit/s.

-  Each H2 ECS uses one PCIe 3.2 TB SSD card for temporary local storage.

-  If an H2 ECS is created using a private image, install an InfiniBand NIC driver on the ECS after the ECS creation following the instructions provided by Mellanox. Download the required version (4.2-1.0.0.0) of InfiniBand NIC driver from the official Mellanox website and install the driver by following the instructions provided by Mellanox.

   -  InfiniBand NIC type: **Mellanox Technologies ConnectX-4 Infiniband HBA (MCX455A-ECAT)**
   -  Mellanox official website: http://www.mellanox.com/
   -  NIC driver download path: https://network.nvidia.com/products/infiniband-drivers/linux/mlnx_ofed/

-  For SUSE H2 ECSs, if IP over InfiniBand (IPoIB) is required, you must manually configure an IP address for the InfiniBand NIC after installing the InfiniBand driver. For details, see :ref:`How Can I Manually Configure an IP Address for an InfiniBand NIC? <en-us_topic_0083225171>`

-  After you delete an H2 ECS, the data stored in SSDs is automatically cleared. Therefore, do not store persistence data into SSDs during ECS running.

Notes on Using Hl1 ECSs
-----------------------

-  Hl1 ECSs only support the attachment of high I/O (performance-optimized I) and ultra-high I/O (latency-optimized) EVS disks.

   To support 56 Gbit shared high I/O storage, you only need to attach high I/O (performance-optimized I) or ultra-high I/O (latency-optimized) EVS disks to target Hl1 ECSs.

-  Hl1 ECSs do not support specifications modification.

-  Hl1 ECSs use InfiniBand NICs that provide a bandwidth of 100 Gbit/s.

-  Hl1 ECSs created using a private image must have the InfiniBand NIC driver installed. Download the required version (4.2-1.0.0.0) of InfiniBand NIC driver from the official Mellanox website and install the driver by following the instructions provided by Mellanox.

   -  InfiniBand NIC type: **Mellanox Technologies ConnectX-4 Infiniband HBA (MCX455A-ECAT)**
   -  Mellanox official website: http://www.mellanox.com/

-  For SUSE Hl1 ECSs, if IPoIB is required, you must manually configure an IP address for the InfiniBand NIC after installing the InfiniBand driver. For details, see :ref:`How Can I Manually Configure an IP Address for an InfiniBand NIC? <en-us_topic_0083225171>`

-  :ref:`Table 4 <en-us_topic_0035470100__table204972196287>` lists the OSs supported by Hl1 ECSs.

   .. _en-us_topic_0035470100__table204972196287:

   .. table:: **Table 4** Supported OS versions

      +-----------------------------------+-----------------------------------------------------+
      | OS                                | Version                                             |
      +===================================+=====================================================+
      | CentOS                            | -  CentOS 7.9 64bit                                 |
      |                                   | -  CentOS 7.7 64bit                                 |
      +-----------------------------------+-----------------------------------------------------+
      | Oracle Linux                      | -  Oracle Linux Server release 8.4 64bit            |
      |                                   | -  Oracle Linux Server release 7.6 64bit            |
      +-----------------------------------+-----------------------------------------------------+
      | Red Hat                           | Red Hat Enterprise Linux 7.9 64bit                  |
      +-----------------------------------+-----------------------------------------------------+
      | SUSE                              | -  Novell SUSE Linux Enterprise Server 15 SP3 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 15 SP2 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 12 SP4 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 12 SP3 64bit |
      +-----------------------------------+-----------------------------------------------------+

-  Charging an Hl1 ECS is stopped when it is stopped.

Related Links
-------------

-  :ref:`Enabling NIC Multi-Queue <en-us_topic_0058758453>`
-  :ref:`How Can I Check Whether the Network Communication Is Normal Between Two ECSs Equipped with an InfiniBand NIC Driver? <en-us_topic_0058747426>`
