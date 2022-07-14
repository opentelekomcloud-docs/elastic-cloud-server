:original_name: en-us_topic_0103071511.html

.. _en-us_topic_0103071511:

ECS Status Management
=====================

+---------------------------------------------------------------+------------------------------------------------------------+---------------------------+----------------------+
| Permission                                                    | API                                                        | Action                    | Dependent Permission |
+===============================================================+============================================================+===========================+======================+
| Changing an ECS OS                                            | POST /v2/{project_id}/cloudservers/{server_id}/changeos    | ecs:cloudServers:changeOS | N/A                  |
+---------------------------------------------------------------+------------------------------------------------------------+---------------------------+----------------------+
| Reinstalling an ECS OS                                        | POST /v2/{project_id}/cloudservers/{server_id}/reinstallos | ecs:cloudServers:rebuild  | N/A                  |
+---------------------------------------------------------------+------------------------------------------------------------+---------------------------+----------------------+
| Modifying the Specifications of an ECS                        | POST /v1/{project_id}/cloudservers/{server_id}/resize      | ecs:cloudServers:resize   | N/A                  |
+---------------------------------------------------------------+------------------------------------------------------------+---------------------------+----------------------+
| Cold Migrating an ECS                                         | POST /v1/{project_id}/cloudservers/{server_id}/migrate     | ecs:cloudServers:migrate  | N/A                  |
+---------------------------------------------------------------+------------------------------------------------------------+---------------------------+----------------------+
| Stopping an ECS (Native OpenStack API)                        | POST /v2/{project_id}/servers/{server_id}/action           | ecs:servers:stop          | ecs:servers:list     |
|                                                               |                                                            |                           |                      |
|                                                               | POST /v2.1/{project_id}/servers/{server_id}/action         |                           |                      |
+---------------------------------------------------------------+------------------------------------------------------------+---------------------------+----------------------+
| Restarting an ECS (Native OpenStack API)                      | POST /v2/{project_id}/servers/{server_id}/action           | ecs:servers:reboot        | ecs:servers:list     |
|                                                               |                                                            |                           |                      |
|                                                               | POST /v2.1/{project_id}/servers/{server_id}/action         |                           |                      |
+---------------------------------------------------------------+------------------------------------------------------------+---------------------------+----------------------+
| Modifying the Specifications of an ECS (Native OpenStack API) | POST /v2.1/{project_id}/servers/{server_id}/action         | ecs:servers:resize        | ecs:servers:list     |
|                                                               |                                                            |                           |                      |
|                                                               | POST /v2.1/{project_id}/servers/{server_id}/action         |                           | ecs:flavors:get      |
|                                                               |                                                            |                           |                      |
|                                                               |                                                            |                           | evs:volumes:list     |
|                                                               |                                                            |                           |                      |
|                                                               |                                                            |                           | evs:volumes:create   |
|                                                               |                                                            |                           |                      |
|                                                               |                                                            |                           | evs:volumes:get      |
|                                                               |                                                            |                           |                      |
|                                                               |                                                            |                           | evs:volumes:attach   |
|                                                               |                                                            |                           |                      |
|                                                               |                                                            |                           | evs:volumes:detach   |
|                                                               |                                                            |                           |                      |
|                                                               |                                                            |                           | evs:volumes:manage   |
|                                                               |                                                            |                           |                      |
|                                                               |                                                            |                           | vpc:ports:get        |
|                                                               |                                                            |                           |                      |
|                                                               |                                                            |                           | vpc:ports:update     |
|                                                               |                                                            |                           |                      |
|                                                               |                                                            |                           | vpc:ports:create     |
|                                                               |                                                            |                           |                      |
|                                                               |                                                            |                           | vpc:ports:delete     |
+---------------------------------------------------------------+------------------------------------------------------------+---------------------------+----------------------+
| Rebuilding an ECS (Native OpenStack API)                      | POST /v2/{project_id}/servers/{server_id}/action           | ecs:servers:rebuild       | ecs:servers:list     |
|                                                               |                                                            |                           |                      |
|                                                               | POST /v2.1/{project_id}/servers/{server_id}/action         |                           | ecs:servers:update   |
|                                                               |                                                            |                           |                      |
|                                                               |                                                            |                           | ims:images:get       |
|                                                               |                                                            |                           |                      |
|                                                               |                                                            |                           | ims:images:list      |
|                                                               |                                                            |                           |                      |
|                                                               |                                                            |                           | ims:images:update    |
+---------------------------------------------------------------+------------------------------------------------------------+---------------------------+----------------------+
| Locking an ECS (Native OpenStack API)                         | POST /v2/{project_id}/servers/{server_id}/action           | ecs:servers:lock          | ecs:servers:list     |
|                                                               |                                                            |                           |                      |
|                                                               | POST /v2.1/{project_id}/servers/{server_id}/action         |                           |                      |
+---------------------------------------------------------------+------------------------------------------------------------+---------------------------+----------------------+
| Unlocking an ECS (Native OpenStack API)                       | POST /v2/{project_id}/servers/{server_id}/action           | ecs:servers:unlock        | ecs:servers:list     |
|                                                               |                                                            |                           |                      |
|                                                               | POST /v2.1/{project_id}/servers/{server_id}/action         |                           |                      |
+---------------------------------------------------------------+------------------------------------------------------------+---------------------------+----------------------+
