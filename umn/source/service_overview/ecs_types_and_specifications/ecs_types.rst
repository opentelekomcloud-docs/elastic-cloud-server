:original_name: en-us_topic_0035470096.html

.. _en-us_topic_0035470096:

ECS Types
=========

The cloud platform provides the following ECS types for different application scenarios:

-  General-purpose
-  Dedicated general-purpose
-  Memory-optimized
-  Large-memory
-  Disk-intensive
-  Ultra-high I/O
-  High-performance computing
-  GPU-accelerated

ECS Flavor Naming Rules
-----------------------

ECS flavors are named in the "AB.C.D" format.

Example: s2.medium.4

The format is defined as follows:

-  **A** specifies the ECS type. For example, **s** indicates a general-purpose ECS, **c** a general computing-plus ECS, and **m** a memory-optimized ECS.
-  **B** specifies the type ID. For example, **3** in **s3** indicates the third-generation general-purpose ECS.
-  **C** specifies the flavor size, such as medium, large, xlarge, 2xlarge, 4xlarge, or 8xlarge.
-  **D** specifies the ratio of memory to vCPUs expressed in a digit. For example, value **4** indicates that the ratio of memory to vCPUs is 4.

How Do I Know My ECS Flavor?
----------------------------

When creating an ECS, you can view the flavors in the flavor list.


.. figure:: /_static/images/en-us_image_0172453607.png
   :alt: **Figure 1** ECS flavors

   **Figure 1** ECS flavors

vCPU
----

ECS supports hyper-threading, which enables two threads to run concurrently on a single CPU core. Each thread is represented as a virtual CPU (vCPU) and a CPU core contains two vCPUs (logical cores).

Hyper-threading is enabled for most ECS flavors by default. If hyper-threading is disabled during the ECS creation or flavor change, the number of vCPUs queried from the ECS is half of the number of vCPUs defined by the ECS flavor.

For example, a 2-core physical CPU contains 4 vCPUs (threads).

Network QoS
-----------

Network QoS uses basic technologies to improve the quality of network communication. A network with QoS enabled offers predictable network performance and effectively allocates network bandwidth to use network resources.

To obtain the QoS data of an ECS flavor, including the maximum bandwidth, assured bandwidth, maximum intranet PPS, and NIC multi-queue, see :ref:`A Summary List of ECS Specifications <en-us_topic_0177512565>`.

The intranet bandwidth and PPS of an ECS are determined by the ECS flavor.

-  Assured intranet bandwidth: indicates the guaranteed bandwidth allocated to an ECS when there is a network bandwidth contention in the entire network.

-  Maximum intranet bandwidth: indicates the maximum bandwidth that can be allocated to an ECS when the ECS does not compete for network bandwidth (other ECSs on the host do not have high requirements on network bandwidth).

-  Maximum intranet PPS: indicates the maximum ECS capability in sending and receiving packets.

   PPS: packets per second, indicates the number of packets received and sent per second. It is usually used to measure the network performance.

-  NIC multi-queues: allocates NIC interrupt requests to multiple vCPUs for higher PPS performance and bandwidth

-  Maximum NICs: indicates the maximum number of NICs that can be attached to an ECS.

-  Maximum supplementary NICs: indicates the maximum number of supplementary NICs that can be attached to an ECS.

.. note::

   -  For instructions about how to test PPS, see :ref:`How Can I Test the Network Performance of Linux ECSs? <en-us_topic_0115820205>`.
   -  For instructions about how to enable NIC multi-queue, see :ref:`Enabling NIC Multi-Queue <en-us_topic_0058758453>`.
   -  The maximum bandwidth is the total bandwidth allocated to an ECS. If an ECS has multiple NICs, the sum of the maximum bandwidths allocated to all NICs cannot exceed the maximum bandwidth allocated to the ECS.
