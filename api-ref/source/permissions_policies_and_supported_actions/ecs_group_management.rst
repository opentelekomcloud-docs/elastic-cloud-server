:original_name: en-us_topic_0103071520.html

.. _en-us_topic_0103071520:

ECS Group Management
====================

+------------------------------------------------------------+------------------------------------------------------------------------------+-------------------------+----------------------+
| Permission                                                 | API                                                                          | Action                  | Dependent Permission |
+============================================================+==============================================================================+=========================+======================+
| Deleting an ECS Group                                      | DELETE /v1/{project_id}/cloudservers/os-server-groups/{server_group_id}      | ecs:cloudServers:delete | N/A                  |
+------------------------------------------------------------+------------------------------------------------------------------------------+-------------------------+----------------------+
| Creating an ECS Group                                      | POST /v1{project_id}/cloudservers/os-server-groups                           | ecs:cloudServers:create | N/A                  |
+------------------------------------------------------------+------------------------------------------------------------------------------+-------------------------+----------------------+
| Adding an ECS to an ECS Group                              | POST /v1/{project_id}/cloudservers/os-server-groups/{server_group_id}/action | ecs:cloudServers:create | N/A                  |
+------------------------------------------------------------+------------------------------------------------------------------------------+-------------------------+----------------------+
| Removing an ECS from an ECS Group                          | POST /v1/{project_id}/cloudservers/os-server-groups/{server_group_id}/action | ecs:cloudServers:delete | N/A                  |
+------------------------------------------------------------+------------------------------------------------------------------------------+-------------------------+----------------------+
| Querying ECS Groups                                        | GET /v1/{project_id}/cloudservers/os-server-groups                           | ecs:cloudServers:list   | N/A                  |
+------------------------------------------------------------+------------------------------------------------------------------------------+-------------------------+----------------------+
| Querying Details About an ECS Group                        | GET /v1/{project_id}/cloudservers/os-server-groups/{server_group_id}         | ecs:cloudServers:get    | N/A                  |
+------------------------------------------------------------+------------------------------------------------------------------------------+-------------------------+----------------------+
| Creating an ECS Group (Native OpenStack API)               | POST /v2/{project_id}/os-server-groups                                       | ecs:serverGroups:manage | N/A                  |
|                                                            |                                                                              |                         |                      |
|                                                            | POST /v2.1/{project_id}/os-server-groups                                     |                         |                      |
+------------------------------------------------------------+------------------------------------------------------------------------------+-------------------------+----------------------+
| Querying ECS Groups (Native OpenStack API)                 | GET /v2/{project_id}/os-server-groups                                        | ecs:serverGroups:manage | N/A                  |
|                                                            |                                                                              |                         |                      |
|                                                            | GET /v2.1/{project_id}/os-server-groups                                      |                         |                      |
+------------------------------------------------------------+------------------------------------------------------------------------------+-------------------------+----------------------+
| Querying Details About an ECS Group (Native OpenStack API) | GET /v2/{project_id}/os-server-groups/{server_group_id}                      | ecs:serverGroups:manage | N/A                  |
|                                                            |                                                                              |                         |                      |
|                                                            | GET /v2.1/{project_id}/os-server-groups/{server_group_id}                    |                         |                      |
+------------------------------------------------------------+------------------------------------------------------------------------------+-------------------------+----------------------+
| Deleting an ECS Group (Native OpenStack API)               | DELETE /v2/{project_id}/os-server-groups/{server_group_id}                   | ecs:serverGroups:manage | N/A                  |
|                                                            |                                                                              |                         |                      |
|                                                            | DELETE /v2.1/{project_id}/os-server-groups/{server_group_id}                 |                         |                      |
+------------------------------------------------------------+------------------------------------------------------------------------------+-------------------------+----------------------+
