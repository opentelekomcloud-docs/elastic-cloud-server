:original_name: en-us_topic_0103072349.html

.. _en-us_topic_0103072349:

Floating IP Address Management
==============================

+-----------------------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+------------------------+
| Permission                                                                                          | API                                                        | Action                    | Dependencies           |
+=====================================================================================================+============================================================+===========================+========================+
| :ref:`Allocating a floating IP address (native OpenStack API) <en-us_topic_0065820816>`             | POST /v2/{project_id}/os-floating-ips                      | ecs:serverFloatingIps:use | vpc:floatingIps:get    |
|                                                                                                     |                                                            |                           |                        |
|                                                                                                     | POST /v2.1/{project_id}/os-floating-ips                    |                           | vpc:floatingIps:create |
|                                                                                                     |                                                            |                           |                        |
|                                                                                                     |                                                            |                           | vpc:floatingIps:update |
|                                                                                                     |                                                            |                           |                        |
|                                                                                                     |                                                            |                           | vpc:ports:get          |
+-----------------------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+------------------------+
| :ref:`Querying floating IP addresses (native OpenStack API) <en-us_topic_0065820817>`               | GET /v2/{project_id}/os-floating-ips                       | ecs:serverFloatingIps:use | vpc:floatingIps:get    |
|                                                                                                     |                                                            |                           |                        |
|                                                                                                     | GET /v2.1/{project_id}/os-floating-ips                     |                           | vpc:ports:get          |
+-----------------------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+------------------------+
| :ref:`Querying details about a floating IP address (native OpenStack API) <en-us_topic_0065820818>` | GET /v2/{project_id}/os-floating-ips/{floating_ip_id}      | ecs:serverFloatingIps:use | vpc:floatingIps:get    |
|                                                                                                     |                                                            |                           |                        |
|                                                                                                     | GET /v2.1/{project_id}/os-floating-ips/{floating_ip_id}    |                           | vpc:ports:get          |
+-----------------------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+------------------------+
| :ref:`Releasing a floating IP address (native OpenStack API) <en-us_topic_0065820819>`              | DELETE /v2/{project_id}/os-floating-ips/{floating_ip_id}   | ecs:serverFloatingIps:use | vpc:floatingIps:get    |
|                                                                                                     |                                                            |                           |                        |
|                                                                                                     | DELETE /v2.1/{project_id}/os-floating-ips/{floating_ip_id} |                           | vpc:floatingIps:delete |
|                                                                                                     |                                                            |                           |                        |
|                                                                                                     |                                                            |                           | vpc:floatingIps:update |
|                                                                                                     |                                                            |                           |                        |
|                                                                                                     |                                                            |                           | vpc:ports:get          |
+-----------------------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+------------------------+
