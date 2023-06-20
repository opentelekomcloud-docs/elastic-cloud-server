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

Obtaining Specifications When Creating an ECS
---------------------------------------------

Specifications for the ECS being created are located in the specifications list.


.. figure:: /_static/images/en-us_image_0172453607.png
   :alt: **Figure 1** ECS specifications

   **Figure 1** ECS specifications

vCPU
----

The ECS processor uses the hyper-threading technology. The CPU exposes two execution contexts per physical core. This means that one physical core now works like two "logical cores" that can handle different software threads.

For example, a 10-core physical CPU contains 20 vCPUs (threads).

Network QoS
-----------

Network QoS uses basic technologies to improve the quality of network communication. A network with QoS enabled offers predictable network performance and effectively allocates network bandwidth to use network resources.

To obtain the QoS data of an ECS flavor, including the maximum bandwidth, assured bandwidth, maximum intranet PPS, and NIC multi-queue, see :ref:`A Summary List of ECS Specifications <en-us_topic_0177512565>`.

The intranet bandwidth and PPS of an ECS are determined based on ECS flavors.

-  Assured intranet bandwidth: indicates the guaranteed bandwidth allocated to an ECS when network bandwidth contention occurs in the entire network.
-  Maximum intranet bandwidth: indicates the maximum bandwidth that can be allocated to an ECS when the ECS does not compete for network bandwidth (other ECSs on the host do not have high requirements on network bandwidth).
-  Maximum intranet PPS: maximum number of packets that the ECS can transmit and receive per second
-  NIC multi-queues: allocates NIC interrupt requests to multiple vCPUs for higher PPS performance and bandwidth
-  Maximum NICs: maximum number of NICs that can be attached to an ECS.

   .. note::

      -  For instructions about how to test PPS, see :ref:`How Can I Test Network Performance? <en-us_topic_0115820205>`
      -  For instructions about how to enable NIC multi-queue, see :ref:`Enabling NIC Multi-Queue <en-us_topic_0058758453>`.
