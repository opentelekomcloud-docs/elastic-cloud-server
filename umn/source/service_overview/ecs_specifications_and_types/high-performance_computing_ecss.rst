.. _en-us_topic_0035470100:

High-Performance Computing ECSs
===============================



.. _en-us_topic_0035470100__section13984653191338:

Overview
--------

H2 ECSs are designed to meet high-end computational needs, such as molecular modeling and computational fluid dynamics. In addition to the substantial CPU power, the H2 ECSs offer diverse options for low-latency RDMA networking using EDR InfiniBand NICs to support memory-intensive computational requirements.

HL1 ECSs are the second generation of high-computing ECSs, featuring large memory capacity. They are interconnected with each other using 100 Gbit/s RDMA InfiniBand NICs and support 56 Gbit/s shared high I/O storage.



.. _en-us_topic_0035470100__section43299283191352:

Specifications
--------------



.. _en-us_topic_0035470100__table18256889221911:

.. table:: **Table 1** H2 ECS specifications

   +---------------+-------+--------------+------------------------------------+-------------------+-----------------+---------------------+-------------+---------------------------------+---------------------------+------------------------------+
   | Flavor        | vCPUs | Memory (GiB) | Maximum/Assured Bandwidth (Gbit/s) | Max. PPS (10,000) | NIC Multi-Queue | Virtualization Type | Local Disks | Capacity of One Local Disk (TB) | Network Type              | Hardware                     |
   +===============+=======+==============+====================================+===================+=================+=====================+=============+=================================+===========================+==============================+
   | h2.3xlarge.10 | 16    | 128          | 13/13                              | 90                | 8               | KVM                 | 1           | 3.2                             | 100 Gbit/s EDR InfiniBand | CPU: Intel® Xeon® E5-2667 v4 |
   +---------------+-------+--------------+------------------------------------+-------------------+-----------------+---------------------+-------------+---------------------------------+---------------------------+------------------------------+
   | h2.3xlarge.20 | 16    | 256          | 13/13                              | 90                | 8               | KVM                 | 1           | 3.2                             | 100 Gbit/s EDR InfiniBand |                              |
   +---------------+-------+--------------+------------------------------------+-------------------+-----------------+---------------------+-------------+---------------------------------+---------------------------+------------------------------+



.. _en-us_topic_0035470100__table27568023202527:

.. table:: **Table 2** HL1 ECS specifications

   +---------------+-------+--------------+------------------------------------+-------------------+-----------------+---------------------+---------------------------+----------------------------------------+
   | Flavor        | vCPUs | Memory (GiB) | Maximum/Assured Bandwidth (Gbit/s) | Max. PPS (10,000) | NIC Multi-Queue | Virtualization Type | Network Type              | Hardware                               |
   +===============+=======+==============+====================================+===================+=================+=====================+===========================+========================================+
   | hl1.8xlarge.8 | 32    | 256          | 9/9                                | 90                | 8               | KVM                 | 100 Gbit/s EDR InfiniBand | CPU: Intel® Xeon® Processor E5-2690 v4 |
   +---------------+-------+--------------+------------------------------------+-------------------+-----------------+---------------------+---------------------------+----------------------------------------+



.. _en-us_topic_0035470100__section1792295234211:

Scenarios
---------

-  Applications

   H2 and HL1: High-performance computing (HPC), big data, and Artificial Intelligence (AI)

-  Application scenarios

   H2 and HL1

   -  High-performance hardware: The ratio of memory to vCPU is 8:1, and a large number of multi-thread physical CPUs are available to provide high-performance storage I/O and high-throughput network connections.
   -  Designed for HPC clusters: Multiple HL1 ECSs can be clustered to install scalable, clustered file system, such as Lustre. HPC applications running on H2 ECSs can read and modify the data stored in the ECSs.
   -  RDMA network connection: Same as H2 ECSs, HL1 ECSs also offer RDMA network using EDR 100 Gbit/s InfiniBand NICs. HL1 ECSs can communicate with H2 ECSs with RDMA protocol. In addition, HL1 ECSs can access EVS disks over the RDMA protocol, which allows up to 56 Gbit/s storage bandwidth.

-  Application scenarios

   H2 and HL1 ECSs provide computing capabilities for clusters with a large memory, good connectivity between nodes, and high storage I/O. The typical application scenarios include HPC, big data, and AI. In HPC solution, HL1 ECSs are perfectly suited for the Lustre parallel distributed file system, generally used for large-scale cluster computing.

   For example, in HPC scenario, H2 ECSs can be used as compute nodes, and HL1 ECSs can be used as storage nodes.



.. _en-us_topic_0035470100__section3551415510283:

Features
--------

High-performance computing ECSs have the following features:

-  Large memory capacity and more processor cores than other types of ECSs

-  Up to 32 vCPUs

-  H2 and HL1 ECSs use InfiniBand NICs that provide a bandwidth of 100 Gbit/s.

-  HL1 ECSs can use the following types of EVS disks as system disk and data disk:

   High I/O (performance-optimized I)

   Ultra-high I/O (latency-optimized)

-  HL1 ECSs support 56 Gbit/s shared high I/O storage.

   To support 56 Gbit/s shared high I/O storage, you only need to attach high I/O (performance-optimized I) or ultra-high I/O (latency-optimized) EVS disks to target HL1 ECSs.



.. _en-us_topic_0035470100__section11683564103115:

Notes on Using H2 ECSs
----------------------

-  H2 ECSs do not support OS reinstallation or change.
-  H2 ECSs do not support specifications modification.
-  H2 ECSs do not support cold migration, live migration, or HA.
-  H2 ECSs support the following OSs:

   -  For public images:

      -  CentOS 7.3 64bit
      -  SUSE Linux Enterprise Server 11 SP4 64bit
      -  SUSE Linux Enterprise Server 12 SP2 64bit

   -  For private images:

      -  CentOS 6.5 64bit
      -  CentOS 7.2 64bit
      -  CentOS 7.3 64bit
      -  SUSE Linux Enterprise Server 11 SP4 64bit
      -  SUSE Linux Enterprise Server 12 SP2 64bit
      -  Red Hat Enterprise Linux 7.2 64bit
      -  Red Hat Enterprise Linux 7.3 64bit

-  H2 ECSs use InfiniBand NICs that provide a bandwidth of 100 Gbit/s.
-  Each H2 ECS uses one PCIe 3.2 TB SSD card for temporary local storage.
-  If an H2 ECS is created using a private image, install an InfiniBand NIC driver on the ECS after the ECS creation following the instructions provided by Mellanox. Download the required version (4.2-1.0.0.0) of InfiniBand NIC driver from the official Mellanox website and install the driver by following the instructions provided by Mellanox.

   -  InfiniBand NIC type: **Mellanox Technologies ConnectX-4 Infiniband HBA (MCX455A-ECAT)**
   -  Mellanox official website: http://www.mellanox.com/
   -  NIC driver download path: http://www.mellanox.com/page/products_dyn?product_family=26&mtag=linux_sw_drivers

-  For SUSE H2 ECSs, if IP over InfiniBand (IPoIB) is required, you must manually configure an IP address for the InfiniBand NIC after installing the InfiniBand driver. For details, see :ref:`How Can I Manually Configure an IP Address for an InfiniBand NIC? <en-us_topic_0083225171>`
-  After you delete an H2 ECS, the data stored in SSDs is automatically cleared. Therefore, do not store persistence data into SSDs during ECS running.



.. _en-us_topic_0035470100__section10721258203459:

Notes on Using HL1 ECSs
-----------------------

-  HL1 ECSs only support the attachment of high I/O (performance-optimized I) and ultra-high I/O (latency-optimized) EVS disks.

   To support 56 Gbit/s shared high I/O storage, you only need to attach high I/O (performance-optimized I) or ultra-high I/O (latency-optimized) EVS disks to target HL1 ECSs.

-  HL1 ECSs do not support specifications modification.

-  HL1 ECSs use InfiniBand NICs that provide a bandwidth of 100 Gbit/s.

-  HL1 ECSs created using a private image must have the InfiniBand NIC driver installed. Download the required version (4.2-1.0.0.0) of InfiniBand NIC driver from the official Mellanox website and install the driver by following the instructions provided by Mellanox.

   -  InfiniBand NIC type: **Mellanox Technologies ConnectX-4 Infiniband HBA (MCX455A-ECAT)**
   -  Mellanox official website: http://www.mellanox.com/

-  For SUSE HL1 ECSs, if IPoIB is required, you must manually configure an IP address for the InfiniBand NIC after installing the InfiniBand driver. For details, see :ref:`How Can I Manually Configure an IP Address for an InfiniBand NIC? <en-us_topic_0083225171>`

-  HL1 ECSs support the following OSs:

   -  For public images:

      -  CentOS 7.3 64bit
      -  SUSE Linux Enterprise Server 11 SP4 64bit
      -  SUSE Linux Enterprise Server 12 SP2 64bit

   -  For private images:

      -  CentOS 6.5 64bit
      -  CentOS 7.2 64bit
      -  CentOS 7.3 64bit
      -  SUSE Linux Enterprise Server 11 SP4 64bit
      -  SUSE Linux Enterprise Server 12 SP2 64bit
      -  Red Hat Enterprise Linux 7.2 64bit
      -  Red Hat Enterprise Linux 7.3 64bit

-  Charging an HL1 ECS is stopped when it is stopped.



.. _en-us_topic_0035470100__section26607449225539:

Related Links
-------------

-  :ref:`Enabling NIC Multi-Queue <en-us_topic_0058758453>`
-  :ref:`How Can I Check Whether the Network Communication Is Normal Between Two ECSs Equipped with an InfiniBand NIC Driver? <en-us_topic_0058747426>`
