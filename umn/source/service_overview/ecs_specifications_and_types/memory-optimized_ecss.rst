Memory-optimized ECSs
=====================

Overview
--------

-  M4 ECSs use second-generation Intel® Xeon® Scalable processors with technologies optimized to offer powerful and stable computing performance. Using 25GE high-speed intelligent NICs, M4 ECSs provide a maximum memory size of 512 GiB based on DDR4 for memory-intensive applications with high requirements on network bandwidth and Packets Per Second (PPS).
-  M3 ECSs are developed based on the KVM virtualization platform and designed for processing large-scale data sets in the memory. They use Intel® Xeon® Scalable processors, network acceleration engines, and DPDK rapid packet processing mechanism to provide higher network performance and up to 512 GiB of DDR4 memory for memory-intensive computing applications.
-  M2 ECSs use Intel Xeon E5-2690 v4 CPUs and are designed for memory-optimized applications.

Specifications
--------------



.. _EN-US_TOPIC_0035550301__table285612469463:

.. table:: **Table 1** M4 ECS specifications

   +------------+-------+------------+------------+------------+------------+------------+------------+------------+
   | Flavor     | vCPUs | Memory     | Maxim      | Maximum    | NIC        | Maximum    | Virt       | Hardware   |
   |            |       | (GiB)      | um/Assured | PPS        | M          | NICs       | ualization |            |
   |            |       |            | Bandwidth  | (10,000)   | ulti-Queue |            | Type       |            |
   |            |       |            | (Gbit/s)   |            |            |            |            |            |
   +============+=======+============+============+============+============+============+============+============+
   | m4.large.8 | 2     | 16         | 4/1.2      | 40         | 2          | 2          | KVM        | CPU:       |
   |            |       |            |            |            |            |            |            | Intel®     |
   |            |       |            |            |            |            |            |            | Xeon®      |
   |            |       |            |            |            |            |            |            | Cascade    |
   |            |       |            |            |            |            |            |            | Lake 6266  |
   +------------+-------+------------+------------+------------+------------+------------+------------+------------+
   | m          | 4     | 32         | 8/2.4      | 80         | 2          | 3          | KVM        |            |
   | 4.xlarge.8 |       |            |            |            |            |            |            |            |
   +------------+-------+------------+------------+------------+------------+------------+------------+------------+
   | m4         | 8     | 64         | 15/4.5     | 150        | 4          | 4          | KVM        |            |
   | .2xlarge.8 |       |            |            |            |            |            |            |            |
   +------------+-------+------------+------------+------------+------------+------------+------------+------------+
   | m4         | 12    | 96         | 17/7       | 200        | 4          | 6          | KVM        |            |
   | .3xlarge.8 |       |            |            |            |            |            |            |            |
   +------------+-------+------------+------------+------------+------------+------------+------------+------------+
   | m4         | 16    | 128        | 20/9       | 280        | 8          | 8          | KVM        |            |
   | .4xlarge.8 |       |            |            |            |            |            |            |            |
   +------------+-------+------------+------------+------------+------------+------------+------------+------------+
   | m4         | 24    | 192        | 25/14      | 400        | 8          | 8          | KVM        |            |
   | .6xlarge.8 |       |            |            |            |            |            |            |            |
   +------------+-------+------------+------------+------------+------------+------------+------------+------------+
   | m4         | 32    | 256        | 30/18      | 550        | 16         | 8          | KVM        |            |
   | .8xlarge.8 |       |            |            |            |            |            |            |            |
   +------------+-------+------------+------------+------------+------------+------------+------------+------------+
   | m4.        | 64    | 512        | 40/36      | 1000       | 32         | 8          | KVM        |            |
   | 16xlarge.8 |       |            |            |            |            |            |            |            |
   +------------+-------+------------+------------+------------+------------+------------+------------+------------+



.. _EN-US_TOPIC_0035550301__table10833218224040:

.. table:: **Table 2** M3 ECS specifications

   +------------+-------+------------+------------+------------+------------+------------+------------+------------+
   | Flavor     | vCPUs | Memory     | Maxim      | Maximum    | NIC        | Maximum    | Virt       | Hardware   |
   |            |       | (GiB)      | um/Assured | PPS        | M          | NICs       | ualization |            |
   |            |       |            | Bandwidth  | (10,000)   | ulti-Queue |            | Type       |            |
   |            |       |            | (Gbit/s)   |            |            |            |            |            |
   +============+=======+============+============+============+============+============+============+============+
   | m3.large.8 | 2     | 16         | 1.5/0.6    | 30         | 2          | 12         | KVM        | CPU:       |
   |            |       |            |            |            |            |            |            | Intel®     |
   |            |       |            |            |            |            |            |            | Xeon®      |
   |            |       |            |            |            |            |            |            | Skylake    |
   |            |       |            |            |            |            |            |            | 6151       |
   +------------+-------+------------+------------+------------+------------+------------+------------+------------+
   | m          | 4     | 32         | 3/1.1      | 50         | 2          | 12         | KVM        |            |
   | 3.xlarge.8 |       |            |            |            |            |            |            |            |
   +------------+-------+------------+------------+------------+------------+------------+------------+------------+
   | m3         | 8     | 64         | 5/2        | 90         | 4          | 12         | KVM        |            |
   | .2xlarge.8 |       |            |            |            |            |            |            |            |
   +------------+-------+------------+------------+------------+------------+------------+------------+------------+
   | m3         | 16    | 128        | 10/4.5     | 130        | 4          | 12         | KVM        |            |
   | .4xlarge.8 |       |            |            |            |            |            |            |            |
   +------------+-------+------------+------------+------------+------------+------------+------------+------------+
   | m3         | 32    | 256        | 15/9       | 260        | 8          | 12         | KVM        |            |
   | .8xlarge.8 |       |            |            |            |            |            |            |            |
   +------------+-------+------------+------------+------------+------------+------------+------------+------------+
   | m3.        | 60    | 512        | 17/17      | 500        | 16         | 12         | KVM        |            |
   | 15xlarge.8 |       |            |            |            |            |            |            |            |
   +------------+-------+------------+------------+------------+------------+------------+------------+------------+



.. _EN-US_TOPIC_0035550301__table38605135203957:

.. table:: **Table 3** M2 ECS specifications

   +-------------+-------+-------------+-------------+-------------+-------------+-------------+-------------+
   | Flavor      | vCPUs | Memory      | Maxi        | Maximum PPS | NIC         | Vir         | Hardware    |
   |             |       | (GiB)       | mum/Assured | (10,000)    | Multi-Queue | tualization |             |
   |             |       |             | Bandwidth   |             |             | Type        |             |
   |             |       |             | (Gbit/s)    |             |             |             |             |
   +=============+=======+=============+=============+=============+=============+=============+=============+
   | m           | 16    | 128         | 8/5         | 40          | 4           | KVM         | CPU: Intel® |
   | 2.4xlarge.8 |       |             |             |             |             |             | Xeon®       |
   |             |       |             |             |             |             |             | Processor   |
   |             |       |             |             |             |             |             | E5-2690 v4  |
   +-------------+-------+-------------+-------------+-------------+-------------+-------------+-------------+
   | m           | 32    | 256         | 13/8        | 60          | 8           | KVM         |             |
   | 2.8xlarge.8 |       |             |             |             |             |             |             |
   +-------------+-------+-------------+-------------+-------------+-------------+-------------+-------------+

Scenarios
---------

-  High-performance relational (MySQL) and NoSQL (MongoDB and Cassandra) databases
-  Distributed web scale cache stores that provide in-memory caching of key-value type data (Memcached and Redis)
-  Applications processing big unstructured data in real time (financial services, Hadoop/Spark clusters)
-  High-performance computing (HPC) and electronic design automation (EDA)

