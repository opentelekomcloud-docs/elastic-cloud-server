Floating IP Address Management
==============================



.. _ENUSTOPIC0103072349table597722943219:

+---------------------------------------------------------------------+------------------------------------------------------------+---------------------------+------------------------+
| Permission                                                          | API                                                        | Action                    | Dependent Permission   |
+=====================================================================+============================================================+===========================+========================+
| Allocating a Floating IP Address (Native OpenStack API)             | POST /v2/{project_id}/os-floating-ips                      | ecs:serverFloatingIps:use | vpc:floatingIps:get    |
|                                                                     |                                                            |                           |                        |
|                                                                     | POST /v2.1/{project_id}/os-floating-ips                    |                           | vpc:floatingIps:create |
|                                                                     |                                                            |                           |                        |
|                                                                     |                                                            |                           | vpc:floatingIps:update |
|                                                                     |                                                            |                           |                        |
|                                                                     |                                                            |                           | vpc:ports:get          |
+---------------------------------------------------------------------+------------------------------------------------------------+---------------------------+------------------------+
| Querying Floating IP Addresses (Native OpenStack API)               | GET /v2/{project_id}/os-floating-ips                       | ecs:serverFloatingIps:use | vpc:floatingIps:get    |
|                                                                     |                                                            |                           |                        |
|                                                                     | GET /v2.1/{project_id}/os-floating-ips                     |                           | vpc:ports:get          |
+---------------------------------------------------------------------+------------------------------------------------------------+---------------------------+------------------------+
| Querying Details About Floating IP Addresses (Native OpenStack API) | GET /v2/{project_id}/os-floating-ips/{floating_ip_id}      | ecs:serverFloatingIps:use | vpc:floatingIps:get    |
|                                                                     |                                                            |                           |                        |
|                                                                     | GET /v2.1/{project_id}/os-floating-ips/{floating_ip_id}    |                           | vpc:ports:get          |
+---------------------------------------------------------------------+------------------------------------------------------------+---------------------------+------------------------+
| Releasing a Floating IP Address (Native OpenStack API)              | DELETE /v2/{project_id}/os-floating-ips/{floating_ip_id}   | ecs:serverFloatingIps:use | vpc:floatingIps:get    |
|                                                                     |                                                            |                           |                        |
|                                                                     | DELETE /v2.1/{project_id}/os-floating-ips/{floating_ip_id} |                           | vpc:floatingIps:delete |
|                                                                     |                                                            |                           |                        |
|                                                                     |                                                            |                           | vpc:floatingIps:update |
|                                                                     |                                                            |                           |                        |
|                                                                     |                                                            |                           | vpc:ports:get          |
+---------------------------------------------------------------------+------------------------------------------------------------+---------------------------+------------------------+


