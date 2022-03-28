NIC Management
==============



.. _ENUSTOPIC0103071513table166711250142311:

+--------------------------------------------------------------+-----------------------------------------------------------------+----------------------------+--------------------------+
| Permission                                                   | API                                                             | Action                     | Dependent Permission     |
+==============================================================+=================================================================+============================+==========================+
| Deleting NICs from an ECS in a Batch                         | POST /v1/{project_id}/cloudservers/{server_id}/nics/delete      | ecs:cloudServerNics:delete | N/A                      |
+--------------------------------------------------------------+-----------------------------------------------------------------+----------------------------+--------------------------+
| Adding NICs to an ECS in a Batch                             | POST /v1/{project_id}/cloudservers/{server_id}/nics             | ecs:cloudServers:addNics   | N/A                      |
+--------------------------------------------------------------+-----------------------------------------------------------------+----------------------------+--------------------------+
| Adding an ECS NIC (Native OpenStack API)                     | POST /v2/{project_id}/servers/{server_id}/os-interface          | ecs:serverInterfaces:use   | ecs:serverInterfaces:get |
|                                                              |                                                                 |                            |                          |
|                                                              | POST /v2.1/{project_id}/servers/{server_id}/os-interface        |                            | vpc:networks:get         |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:networks:update      |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:subnets:get          |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:subnets:update       |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:ports:create         |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:ports:update         |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:ports:get            |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:networks:create      |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:subnets:create       |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:routers:get          |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:routers:update       |
+--------------------------------------------------------------+-----------------------------------------------------------------+----------------------------+--------------------------+
| Deleting an ECS NIC (Native OpenStack API)                   | DELETE /v2/{project_id}/servers/{server_id}/os-interface/{id}   | ecs:serverInterfaces:use   | ecs:serverInterfaces:get |
|                                                              |                                                                 |                            |                          |
|                                                              | DELETE /v2.1/{project_id}/servers/{server_id}/os-interface/{id} |                            | ecs:servers:get          |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:networks:create      |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:subnets:create       |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:networks:get         |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:networks:update      |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:subnets:get          |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:subnets:update       |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:ports:delete         |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:ports:update         |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:ports:get            |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:routers:get          |
|                                                              |                                                                 |                            |                          |
|                                                              |                                                                 |                            | vpc:routers:update       |
+--------------------------------------------------------------+-----------------------------------------------------------------+----------------------------+--------------------------+
| Querying ECS NICs (Native OpenStack API)                     | GET /v2/{project_id}/servers/{server_id}/os-interface           | ecs:serverInterfaces:get   | vpc:ports:get            |
|                                                              |                                                                 |                            |                          |
|                                                              | GET /v2.1/{project_id}/servers/{server_id}/os-interface         |                            |                          |
+--------------------------------------------------------------+-----------------------------------------------------------------+----------------------------+--------------------------+
| Querying NIC Information About an ECS (Native OpenStack API) | GET /v2/{project_id}/servers/{server_id}/os-interface/{id}      | ecs:serverInterfaces:get   | vpc:ports:get            |
|                                                              |                                                                 |                            |                          |
|                                                              | GET /v2.1/{project_id}/servers/{server_id}/os-interface/{id}    |                            |                          |
+--------------------------------------------------------------+-----------------------------------------------------------------+----------------------------+--------------------------+


