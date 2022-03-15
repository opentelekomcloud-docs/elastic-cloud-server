Tag Management
==============



.. _ENUSTOPIC0103071521table4509123112811:

+-------------------------------------------------------------+------------------------------------------------------------+-----------------------+----------------------+
| Permission                                                  | API                                                        | Action                | Dependent Permission |
+=============================================================+============================================================+=======================+======================+
| Adding or Deleting Tags to or from an ECS in a Batch        | POST /v1/{project_id}/cloudservers/{server_id}/tags/action | ecs:cloudServers:put  | N/A                  |
+-------------------------------------------------------------+------------------------------------------------------------+-----------------------+----------------------+
| Querying Project Tags                                       | GET /v1/{project_id}/cloudservers/tags                     | ecs:cloudServers:list | N/A                  |
+-------------------------------------------------------------+------------------------------------------------------------+-----------------------+----------------------+
| Adding Tags in a Batch                                      | POST /v1/{project_id}/servers/{server_id}/tags/action      | ecs:servers:setTags   | N/A                  |
|                                                             |                                                            |                       |                      |
| Deleting Tags in a Batch                                    |                                                            |                       |                      |
+-------------------------------------------------------------+------------------------------------------------------------+-----------------------+----------------------+
| Querying ECSs by Tag                                        | POST /v1/{project_id}/servers/resource_instances/action    | ecs:servers:getTags   | N/A                  |
+-------------------------------------------------------------+------------------------------------------------------------+-----------------------+----------------------+
| Querying Project Tags                                       | GET /v1/{project_id}/servers/tags                          | ecs:servers:getTags   | N/A                  |
+-------------------------------------------------------------+------------------------------------------------------------+-----------------------+----------------------+
| Querying Tags of an ECS                                     | GET /v1/{project_id}/servers/{server_id}/tags              | ecs:servers:getTags   | N/A                  |
+-------------------------------------------------------------+------------------------------------------------------------+-----------------------+----------------------+
| Querying Tags of a Specified ECS (Native OpenStack API)     | GET /v2/{project_id}/servers/{server_id}/tags              | ecs:servers:getTags   | ecs:servers:get      |
|                                                             |                                                            |                       |                      |
|                                                             | GET /v2.1/{project_id}/servers/{server_id}/tags            |                       |                      |
+-------------------------------------------------------------+------------------------------------------------------------+-----------------------+----------------------+
| Adding a Tag to an ECS (Native OpenStack API)               | PUT /v2/{project_id}/servers/{server_id}/tags/{tag}        | ecs:servers:setTags   | ecs:servers:get      |
|                                                             |                                                            |                       |                      |
|                                                             | PUT /v2.1/{project_id}/servers/{server_id}/tags/{tag}      |                       |                      |
+-------------------------------------------------------------+------------------------------------------------------------+-----------------------+----------------------+
| Creating an ECS Tag (Native OpenStack API)                  | PUT /v2/{project_id}/servers/{server_id}/tags              | ecs:servers:setTags   | ecs:servers:get      |
|                                                             |                                                            |                       |                      |
|                                                             | PUT /v2.1/{project_id}/servers/{server_id}/tags            |                       |                      |
+-------------------------------------------------------------+------------------------------------------------------------+-----------------------+----------------------+
| Deleting a Specified Tag from an ECS (Native OpenStack API) | DELETE /v2/{project_id}/servers/{server_id}/tags/{tag}     | ecs:servers:setTags   | ecs:servers:get      |
|                                                             |                                                            |                       |                      |
|                                                             | DELETE /v2.1/{project_id}/servers/{server_id}/tags/{tag}   |                       |                      |
+-------------------------------------------------------------+------------------------------------------------------------+-----------------------+----------------------+
| Querying an ECS Tag (Native OpenStack API)                  | GET /v2/{project_id}/servers/{server_id}/tags/{tag}        | ecs:servers:getTags   | ecs:servers:get      |
|                                                             |                                                            |                       |                      |
|                                                             | GET /v2.1/{project_id}/servers/{server_id}/tags/{tag}      |                       |                      |
+-------------------------------------------------------------+------------------------------------------------------------+-----------------------+----------------------+
| Deleting All ECS Tags (Native OpenStack API)                | DELETE /v2/{project_id}/servers/{server_id}/tags           | ecs:servers:setTags   | ecs:servers:get      |
|                                                             |                                                            |                       |                      |
|                                                             | DELETE /v2.1/{project_id}/servers/{server_id}/tags         |                       |                      |
+-------------------------------------------------------------+------------------------------------------------------------+-----------------------+----------------------+


