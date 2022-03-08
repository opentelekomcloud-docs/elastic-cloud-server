Basic ECS Metrics
=================

Description
-----------

This section describes monitoring metrics reported by ECS to Cloud Eye. You can use Cloud Eye to view these metrics and alarms generated for ECSs.

Namespace
---------

SYS.ECS

ECS Metrics
-----------

ECS metrics vary depending on ECS OSs and types. For details, see `Table 1 <#EN-US_TOPIC_0030911465__table1474714113454>`__. Y indicates that the metric is supported, and x indicates that the metric is not supported.



.. _EN-US_TOPIC_0030911465__table1474714113454:

.. table:: **Table 1** ECS metrics

   ===================== ============================ ============================
   Metric                Windows                      Linux
   ===================== ============================ ============================
   CPU Usage             Supported                    Supported
   Memory Usage          Supported                    Not supported
   Disk Usage            Supported                    Not supported
   Disk Read Bandwidth   Supported                    Supported
   Disk Write Bandwidth  Supported                    Supported
   Disk Read IOPS        Supported                    Supported
   Disk Write IOPS       Supported                    Supported
   Inband Incoming Rate  Supported                    Not supported
   Inband Outgoing Rate  Supported                    Not supported
   Outband Incoming Rate Supported                    Supported
   Outband Outgoing Rate Supported                    Supported
   InfiniBand NIC Status Supported (Only for H2 ECSs) Supported (Only for H2 ECSs)
   ===================== ============================ ============================

|image1|

The image based on which the target ECS is created must have OTC Tools installed (OTC Tools has been installed for public images by default). Otherwise, the **Memory Usage** and **Disk Usage** metrics are unavailable. For details about how to install the OTC Tools, visit https://github.com/UVP-Tools/UVP-Tools/.

`Table 2 <#EN-US_TOPIC_0030911465__table64866324222846>`__ describes these ECS metrics.

The monitoring intervals for the following ECSs with raw monitoring metrics are as follows:

-  KVM ECS: 5 minutes



.. _EN-US_TOPIC_0030911465__table64866324222846:

.. table:: **Table 2** Metric description

   +---------------------------------------+------------------+-------------------+----------------+------------------+-----------------+
   | Metric                                | Parameter        | Description       | Value Range    | Monitored Object | Monitoring      |
   |                                       |                  |                   |                |                  | Interval (Raw   |
   |                                       |                  |                   |                |                  | Metrics and KVM |
   |                                       |                  |                   |                |                  | Only)           |
   +=======================================+==================+===================+================+==================+=================+
   | cpu_util                              | CPU Usage        | CPU usage of an   | ≥ 0            | ECS              | 5 minutes       |
   |                                       |                  | ECS               |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Unit: Percent     |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Formula: CPU      |                |                  |                 |
   |                                       |                  | usage of an       |                |                  |                 |
   |                                       |                  | ECS/Number of     |                |                  |                 |
   |                                       |                  | vCPUs in the ECS  |                |                  |                 |
   +---------------------------------------+------------------+-------------------+----------------+------------------+-----------------+
   | mem_util                              | Memory Usage     | Memory usage of   | ≥ 0            | ECS              | 5 minutes       |
   |                                       |                  | an ECS            |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | This metric is    |                |                  |                 |
   |                                       |                  | unavailable if    |                |                  |                 |
   |                                       |                  | the image has no  |                |                  |                 |
   |                                       |                  | OTC Tools         |                |                  |                 |
   |                                       |                  | installed.        |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Unit: Percent     |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Formula: Used     |                |                  |                 |
   |                                       |                  | memory of an      |                |                  |                 |
   |                                       |                  | ECS/Total memory  |                |                  |                 |
   |                                       |                  | of the ECS        |                |                  |                 |
   +---------------------------------------+------------------+-------------------+----------------+------------------+-----------------+
   | disk_util_inband                      | Disk Usage       | Disk usage of an  | ≥ 0            | ECS              | 5 minutes       |
   |                                       |                  | ECS               |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | This metric is    |                |                  |                 |
   |                                       |                  | unavailable if    |                |                  |                 |
   |                                       |                  | the image has no  |                |                  |                 |
   |                                       |                  | OTC Tools         |                |                  |                 |
   |                                       |                  | installed.        |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Unit: Percent     |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Formula: Used     |                |                  |                 |
   |                                       |                  | capacity of an    |                |                  |                 |
   |                                       |                  | ECS disk/Total    |                |                  |                 |
   |                                       |                  | capacity of the   |                |                  |                 |
   |                                       |                  | ECS disk          |                |                  |                 |
   +---------------------------------------+------------------+-------------------+----------------+------------------+-----------------+
   | disk_read_bytes_rate                  | Disk Read        | Number of bytes   | ≥ 0            | ECS              | 5 minutes       |
   |                                       | Bandwidth        | read from an ECS  |                |                  |                 |
   |                                       |                  | disk per second   |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Unit: byte/s      |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Formula: Total    |                |                  |                 |
   |                                       |                  | number of bytes   |                |                  |                 |
   |                                       |                  | read from an ECS  |                |                  |                 |
   |                                       |                  | disk/Monitoring   |                |                  |                 |
   |                                       |                  | interval          |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | byte_out =        |                |                  |                 |
   |                                       |                  | (rd_bytes -       |                |                  |                 |
   |                                       |                  | la                |                |                  |                 |
   |                                       |                  | st_rd_bytes)/Time |                |                  |                 |
   |                                       |                  | difference        |                |                  |                 |
   +---------------------------------------+------------------+-------------------+----------------+------------------+-----------------+
   | disk_write_bytes_rate                 | Disk Write       | Number of bytes   | ≥ 0            | ECS              | 5 minutes       |
   |                                       | Bandwidth        | written to an ECS |                |                  |                 |
   |                                       |                  | disk per second   |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Unit: byte/s      |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Formula: Total    |                |                  |                 |
   |                                       |                  | number of bytes   |                |                  |                 |
   |                                       |                  | written to an ECS |                |                  |                 |
   |                                       |                  | disk/Monitoring   |                |                  |                 |
   |                                       |                  | interval          |                |                  |                 |
   +---------------------------------------+------------------+-------------------+----------------+------------------+-----------------+
   | disk_read_requests_rate               | Disk Read IOPS   | Number of read    | ≥ 0            | ECS              | 5 minutes       |
   |                                       |                  | requests sent to  |                |                  |                 |
   |                                       |                  | an ECS disk per   |                |                  |                 |
   |                                       |                  | second            |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Unit: request/s   |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Formula: Total    |                |                  |                 |
   |                                       |                  | number of read    |                |                  |                 |
   |                                       |                  | requests sent to  |                |                  |                 |
   |                                       |                  | an ECS            |                |                  |                 |
   |                                       |                  | disk/Monitoring   |                |                  |                 |
   |                                       |                  | interval          |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | req_out = (rd_req |                |                  |                 |
   |                                       |                  | -                 |                |                  |                 |
   |                                       |                  | last_rd_req)/Time |                |                  |                 |
   |                                       |                  | difference        |                |                  |                 |
   +---------------------------------------+------------------+-------------------+----------------+------------------+-----------------+
   | disk_write_requests_rate              | Disk Write IOPS  | Number of write   | ≥ 0            | ECS              | 5 minutes       |
   |                                       |                  | requests sent to  |                |                  |                 |
   |                                       |                  | an ECS disk per   |                |                  |                 |
   |                                       |                  | second            |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Unit: request/s   |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Formula: Total    |                |                  |                 |
   |                                       |                  | number of write   |                |                  |                 |
   |                                       |                  | requests sent to  |                |                  |                 |
   |                                       |                  | an ECS            |                |                  |                 |
   |                                       |                  | disk/Monitoring   |                |                  |                 |
   |                                       |                  | interval          |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | req_in = (wr_req  |                |                  |                 |
   |                                       |                  | -                 |                |                  |                 |
   |                                       |                  | last_wr_req)/Time |                |                  |                 |
   |                                       |                  | difference        |                |                  |                 |
   +---------------------------------------+------------------+-------------------+----------------+------------------+-----------------+
   | network_incoming_bytes_rate_inband    | Inband Incoming  | Number of         | ≥ 0            | ECS              | 5 minutes       |
   |                                       | Rate             | incoming bytes on |                |                  |                 |
   |                                       |                  | an ECS per second |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Unit: byte/s      |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Formula: Total    |                |                  |                 |
   |                                       |                  | number of inband  |                |                  |                 |
   |                                       |                  | incoming bytes on |                |                  |                 |
   |                                       |                  | an ECS/Monitoring |                |                  |                 |
   |                                       |                  | interval          |                |                  |                 |
   +---------------------------------------+------------------+-------------------+----------------+------------------+-----------------+
   | network_outgoing_bytes_rate_inband    | Inband Outgoing  | Number of         | ≥ 0            | ECS              | 5 minutes       |
   |                                       | Rate             | outgoing bytes on |                |                  |                 |
   |                                       |                  | an ECS per second |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Unit: byte/s      |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Formula: Total    |                |                  |                 |
   |                                       |                  | number of inband  |                |                  |                 |
   |                                       |                  | outgoing bytes on |                |                  |                 |
   |                                       |                  | an ECS/Monitoring |                |                  |                 |
   |                                       |                  | interval          |                |                  |                 |
   +---------------------------------------+------------------+-------------------+----------------+------------------+-----------------+
   | network_incoming_bytes_aggregate_rate | Outband Incoming | Number of         | ≥ 0            | ECS              | 5 minutes       |
   |                                       | Rate             | incoming bytes on |                |                  |                 |
   |                                       |                  | an ECS per second |                |                  |                 |
   |                                       |                  | on the hypervisor |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Unit: byte/s      |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Formula: Total    |                |                  |                 |
   |                                       |                  | number of outband |                |                  |                 |
   |                                       |                  | incoming bytes on |                |                  |                 |
   |                                       |                  | an ECS/Monitoring |                |                  |                 |
   |                                       |                  | interval          |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | This metric is    |                |                  |                 |
   |                                       |                  | unavailable if    |                |                  |                 |
   |                                       |                  | SR-IOV is         |                |                  |                 |
   |                                       |                  | enabled.          |                |                  |                 |
   +---------------------------------------+------------------+-------------------+----------------+------------------+-----------------+
   | network_outgoing_bytes_aggregate_rate | Outband Outgoing | Number of         | ≥ 0            | ECS              | 5 minutes       |
   |                                       | Rate             | outgoing bytes on |                |                  |                 |
   |                                       |                  | an ECS per second |                |                  |                 |
   |                                       |                  | on the hypervisor |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Unit: byte/s      |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | Formula: Total    |                |                  |                 |
   |                                       |                  | number of outband |                |                  |                 |
   |                                       |                  | outgoing bytes on |                |                  |                 |
   |                                       |                  | an ECS/Monitoring |                |                  |                 |
   |                                       |                  | interval          |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | This metric is    |                |                  |                 |
   |                                       |                  | unavailable if    |                |                  |                 |
   |                                       |                  | SR-IOV is         |                |                  |                 |
   |                                       |                  | enabled.          |                |                  |                 |
   +---------------------------------------+------------------+-------------------+----------------+------------------+-----------------+
   | ib_card_state                         | InfiniBand NIC   | Status of an      | **0** or **1** | ECS              | 5 minutes       |
   |                                       | status           | InfiniBand NIC on |                |                  |                 |
   |                                       |                  | an H2 ECS         |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | The system        |                |                  |                 |
   |                                       |                  | periodically      |                |                  |                 |
   |                                       |                  | checks the status |                |                  |                 |
   |                                       |                  | and returns check |                |                  |                 |
   |                                       |                  | results using     |                |                  |                 |
   |                                       |                  | value **0** or    |                |                  |                 |
   |                                       |                  | **1**.            |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | -  **0**: The     |                |                  |                 |
   |                                       |                  |    system is      |                |                  |                 |
   |                                       |                  |    running        |                |                  |                 |
   |                                       |                  |    properly. That |                |                  |                 |
   |                                       |                  |    is, the        |                |                  |                 |
   |                                       |                  |    InfiniBand NIC |                |                  |                 |
   |                                       |                  |    is functional. |                |                  |                 |
   |                                       |                  | -  **1**: The     |                |                  |                 |
   |                                       |                  |    system is not  |                |                  |                 |
   |                                       |                  |    running        |                |                  |                 |
   |                                       |                  |    properly. That |                |                  |                 |
   |                                       |                  |    is, the        |                |                  |                 |
   |                                       |                  |    InfiniBand NIC |                |                  |                 |
   |                                       |                  |    malfunctions.  |                |                  |                 |
   |                                       |                  |    When the       |                |                  |                 |
   |                                       |                  |    physical NIC   |                |                  |                 |
   |                                       |                  |    corresponding  |                |                  |                 |
   |                                       |                  |    to a virtual   |                |                  |                 |
   |                                       |                  |    NIC becomes    |                |                  |                 |
   |                                       |                  |    faulty, for    |                |                  |                 |
   |                                       |                  |    example, the   |                |                  |                 |
   |                                       |                  |    network cable  |                |                  |                 |
   |                                       |                  |    is not         |                |                  |                 |
   |                                       |                  |    securely       |                |                  |                 |
   |                                       |                  |    connected to   |                |                  |                 |
   |                                       |                  |    the NIC, the   |                |                  |                 |
   |                                       |                  |    switch or      |                |                  |                 |
   |                                       |                  |    adapter is     |                |                  |                 |
   |                                       |                  |    incompatible   |                |                  |                 |
   |                                       |                  |    with the       |                |                  |                 |
   |                                       |                  |    InfiniBand     |                |                  |                 |
   |                                       |                  |    NIC, or the    |                |                  |                 |
   |                                       |                  |    NIC is         |                |                  |                 |
   |                                       |                  |    disabled, the  |                |                  |                 |
   |                                       |                  |    returned value |                |                  |                 |
   |                                       |                  |    is **1**.      |                |                  |                 |
   |                                       |                  |                   |                |                  |                 |
   |                                       |                  | NOTE:             |                |                  |                 |
   |                                       |                  | Only Mellanox EDR |                |                  |                 |
   |                                       |                  | 100 GB            |                |                  |                 |
   |                                       |                  | single-port       |                |                  |                 |
   |                                       |                  | InfiniBand NICs   |                |                  |                 |
   |                                       |                  | are supported.    |                |                  |                 |
   +---------------------------------------+------------------+-------------------+----------------+------------------+-----------------+

Dimensions
----------



.. _EN-US_TOPIC_0030911465__table41237041112133:

=========== =====================
Key         Value
=========== =====================
instance_id Specifies the ECS ID.
=========== =====================

.. |image1| image:: /_static/images/note_3.0-en-us.png
