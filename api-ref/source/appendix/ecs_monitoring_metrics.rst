ECS Monitoring Metrics
======================

Function
--------

This section describes metrics reported by ECS to Cloud Eye as well as their namespaces and dimensions. You can use APIs provided by Cloud Eye to query the metrics of the monitored object and alarms generated for ECS.

Namespace
---------

SYS.ECS

Metrics
-------



.. _ENUSTOPIC0022067719table13636366112133:

+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| Metric                                  | Name                  | Description                                                                                                                                | Value Range | Remarks                                                                |
+=========================================+=======================+============================================================================================================================================+=============+========================================================================+
| cpu_util                                | CPU Usage             | This metric is used to show CPU usages (%) of monitored objects.                                                                           | 0% to 100%  | ECS monitored                                                          |
|                                         |                       |                                                                                                                                            |             |                                                                        |
|                                         |                       |                                                                                                                                            |             | .. note::                                                              |
|                                         |                       |                                                                                                                                            |             |                                                                        |
|                                         |                       |                                                                                                                                            |             |    The metrics collected using OTC Tools are accurate.                 |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| mem_util                                | Memory Usage          | This metric is used to show memory usages (%) of monitored objects.                                                                        | 0% to 100%  | ECS monitored                                                          |
|                                         |                       |                                                                                                                                            |             |                                                                        |
|                                         |                       |                                                                                                                                            |             | .. note::                                                              |
|                                         |                       |                                                                                                                                            |             |                                                                        |
|                                         |                       |                                                                                                                                            |             |    This metric is unavailable if the image has no OTC Tools installed. |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| disk_util_inband                        | Disks Usage           | This metric is used to show disk usages (%) of monitored objects.                                                                          | 0% to 100%  | ECS monitored                                                          |
|                                         |                       |                                                                                                                                            |             |                                                                        |
|                                         |                       |                                                                                                                                            |             | .. note::                                                              |
|                                         |                       |                                                                                                                                            |             |                                                                        |
|                                         |                       |                                                                                                                                            |             |    This metric is unavailable if the image has no OTC Tools installed. |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| disk_read_bytes_rate                    | Disk Read Bandwidth   | This metric is used to show the number of bytes read from the monitored object per second (byte/s).                                        | ≥ 0         | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| disk_write_bytes_rate                   | Disk Write Bandwidth  | This metric is used to show the number of bytes written to the monitored object per second (byte/s).                                       | ≥ 0         | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| disk_read_requests_rate                 | Disk Read IOPS        | This metric is used to show the number of read requests sent to the monitored object per second (requests/second).                         | ≥ 0         | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| disk_write_requests_rate                | Disk Write IOPS       | This metric is used to show the number of write requests sent to the monitored object per second (requests/second).                        | ≥ 0         | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| network_incoming_bytes_rate_inband      | Inband Incoming Rate  | This metric is used to show the number of incoming bytes received by the monitored object per second (byte/s).                             | ≥ 0         | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| network_outgoing_bytes_rate_inband      | Inband Outgoing Rate  | This metric is used to show the number of outgoing bytes sent by the monitored object per second (byte/s).                                 | ≥ 0         | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| network_incoming_bytes_aggregate_rate   | Outband Incoming Rate | This metric is used to show the number of incoming bytes received by the monitored object per second (byte/s) at the virtualization layer. | ≥ 0         | ECS monitored                                                          |
|                                         |                       |                                                                                                                                            |             |                                                                        |
|                                         |                       |                                                                                                                                            |             | .. note::                                                              |
|                                         |                       |                                                                                                                                            |             |                                                                        |
|                                         |                       |                                                                                                                                            |             |    This metric is unavailable if SR-IOV is enabled.                    |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| network_outgoing_bytes\_ aggregate_rate | Outband Outgoing Rate | This metric is used to show the number of outgoing bytes sent by the monitored object per second (byte/s) at the virtualization layer.     | ≥ 0         | ECS monitored                                                          |
|                                         |                       |                                                                                                                                            |             |                                                                        |
|                                         |                       |                                                                                                                                            |             | .. note::                                                              |
|                                         |                       |                                                                                                                                            |             |                                                                        |
|                                         |                       |                                                                                                                                            |             |    This metric is unavailable if SR-IOV is enabled.                    |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| ib_card_state                           | InfiniBand NIC status | This metric is used to monitor the status of an InfiniBand NIC on a high-performance h2 ECS to ensure proper InfiniBand NIC running.       | 0 or 1      | ECS monitored                                                          |
|                                         |                       |                                                                                                                                            |             |                                                                        |
|                                         |                       | The system periodically checks the NIC status and returns check results using value **0** or **1**.                                        |             | .. note::                                                              |
|                                         |                       |                                                                                                                                            |             |                                                                        |
|                                         |                       | -  **0**: The system is running properly. That is, the InfiniBand NIC is functional.                                                       |             |    Only Mellanox EDR 100 GB single-port InfiniBand NICs are supported. |
|                                         |                       | -  **1**: The system is not running properly. That is, the InfiniBand NIC malfunctions.                                                    |             |                                                                        |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+

.. note::

   The image based on which the target ECS is created must have OTC Tools installed. Otherwise, the **Memory Usage** and **Disk Usage** metrics are unavailable. For details about how to install the OTC Tools, visit https://github.com/UVP-Tools/UVP-Tools/.

Dimension
---------



.. _ENUSTOPIC0022067719table41237041112133:

=========== =====================
Key         Value
=========== =====================
instance_id Specifies the ECS ID.
=========== =====================


