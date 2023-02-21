:original_name: en-us_topic_0022067719.html

.. _en-us_topic_0022067719:

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

+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| Metric                                  | Name                  | Description                                                                                                                                | Value Range | Remarks                                                                |
+=========================================+=======================+============================================================================================================================================+=============+========================================================================+
| cpu_util                                | CPU Usage             | This metric is used to show CPU usages (%) of monitored objects.                                                                           | 0% to 100%  | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| mem_util                                | Memory Usage          | This metric is used to show memory usages (%) of monitored objects.                                                                        | 0% to 100%  | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| disk_util_inband                        | Disks Usage           | This metric is used to show disk usages (%) of monitored objects.                                                                          | 0% to 100%  | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| disk_read_bytes_rate                    | Disk Read Bandwidth   | This metric is used to show the number of bytes read from the monitored object per second (byte/s).                                        | >= 0        | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| disk_write_bytes_rate                   | Disk Write Bandwidth  | This metric is used to show the number of bytes written to the monitored object per second (byte/s).                                       | >= 0        | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| disk_read_requests_rate                 | Disk Read IOPS        | This metric is used to show the number of read requests sent to the monitored object per second (requests/second).                         | >= 0        | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| disk_write_requests_rate                | Disk Write IOPS       | This metric is used to show the number of write requests sent to the monitored object per second (requests/second).                        | >= 0        | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| network_incoming_bytes_rate_inband      | Inband Incoming Rate  | This metric is used to show the number of incoming bytes received by the monitored object per second (byte/s).                             | >= 0        | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| network_outgoing_bytes_rate_inband      | Inband Outgoing Rate  | This metric is used to show the number of outgoing bytes sent by the monitored object per second (byte/s).                                 | >= 0        | ECS monitored                                                          |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| network_incoming_bytes_aggregate_rate   | Outband Incoming Rate | This metric is used to show the number of incoming bytes received by the monitored object per second (byte/s) at the virtualization layer. | >= 0        | ECS monitored                                                          |
|                                         |                       |                                                                                                                                            |             |                                                                        |
|                                         |                       |                                                                                                                                            |             | .. note::                                                              |
|                                         |                       |                                                                                                                                            |             |                                                                        |
|                                         |                       |                                                                                                                                            |             |    This metric is unavailable if SR-IOV is enabled.                    |
+-----------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------+------------------------------------------------------------------------+
| network_outgoing_bytes\_ aggregate_rate | Outband Outgoing Rate | This metric is used to show the number of outgoing bytes sent by the monitored object per second (byte/s) at the virtualization layer.     | >= 0        | ECS monitored                                                          |
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

   To monitor the memory usage and disk usage, you need to install the agent on your ECS.

   -  For details about how to install the agent on a Windows ECS, see `Installing and Configuring the Agent on a Windows Server <https://docs.otc.t-systems.com/cloud-eye/umn/server_monitoring/installing_and_configuring_the_agent_on_a_windows_ecs/installing_and_configuring_the_agent_on_a_windows_server.html>`__.
   -  For details about how to install the agent on a Linux ECS, see `Installing the Agent on a Linux Server <https://docs.otc.t-systems.com/cloud-eye/umn/server_monitoring/installing_and_configuring_the_agent_on_a_linux_ecs_or_bms/installing_the_agent_on_a_linux_server.html#ces-01-0029>`__.

Dimension
---------

=========== =====================
Key         Value
=========== =====================
instance_id Specifies the ECS ID.
=========== =====================
