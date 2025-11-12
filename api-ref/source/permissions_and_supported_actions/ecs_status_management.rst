:original_name: en-us_topic_0103071511.html

.. _en-us_topic_0103071511:

ECS Status Management
=====================

+-------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+--------------------+
| Permission                                                                          | API                                                        | Action                    | Dependencies       |
+=====================================================================================+============================================================+===========================+====================+
| :ref:`Changing an ECS OS <en-us_topic_0067876971>`                                  | POST /v2/{project_id}/cloudservers/{server_id}/changeos    | ecs:cloudServers:changeOS | ``-``              |
+-------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+--------------------+
| :ref:`Reinstalling an ECS OS <en-us_topic_0067876349>`                              | POST /v2/{project_id}/cloudservers/{server_id}/reinstallos | ecs:cloudServers:rebuild  | ``-``              |
+-------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+--------------------+
| :ref:`Modifying ECS specifications (pay-per-use) <en-us_topic_0020212653>`          | POST /v1/{project_id}/cloudservers/{server_id}/resize      | ecs:cloudServers:resize   | ``-``              |
+-------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+--------------------+
| :ref:`Cold migrating an ECS <en-us_topic_0132905656>`                               | POST /v1/{project_id}/cloudservers/{server_id}/migrate     | ecs:cloudServers:migrate  | ``-``              |
+-------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+--------------------+
| :ref:`Starting an ECS (native OpenStack API) <en-us_topic_0020212648>`              | POST /v2/{project_id}/servers/{server_id}/action           | ecs:servers:start         | ecs:servers:list   |
|                                                                                     |                                                            |                           |                    |
|                                                                                     | POST /v2.1/{project_id}/servers/{server_id}/action         |                           |                    |
+-------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+--------------------+
| :ref:`Stopping an ECS (native OpenStack API) <en-us_topic_0020212652>`              | POST /v2/{project_id}/servers/{server_id}/action           | ecs:servers:stop          | ecs:servers:list   |
|                                                                                     |                                                            |                           |                    |
|                                                                                     | POST /v2.1/{project_id}/servers/{server_id}/action         |                           | ecs:servers:get    |
+-------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+--------------------+
| :ref:`Restarting an ECS (native OpenStack API) <en-us_topic_0020212650>`            | POST /v2/{project_id}/servers/{server_id}/action           | ecs:servers:reboot        | ecs:servers:list   |
|                                                                                     |                                                            |                           |                    |
|                                                                                     | POST /v2.1/{project_id}/servers/{server_id}/action         |                           | ecs:servers:get    |
+-------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+--------------------+
| :ref:`Modifying ECS specifications (native OpenStack API) <en-us_topic_0028714261>` | POST /v2.1/{project_id}/servers/{server_id}/action         | ecs:servers:resize        | ecs:servers:list   |
|                                                                                     |                                                            |                           |                    |
|                                                                                     | POST /v2.1/{project_id}/servers/{server_id}/action         |                           | ecs:servers:get    |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | ecs:flavors:get    |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | ims:images:get     |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | evs:volumes:list   |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | evs:volumes:create |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | evs:volumes:get    |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | evs:volumes:attach |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | evs:volumes:detach |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | evs:volumes:manage |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | vpc:ports:get      |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | vpc:ports:update   |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | vpc:ports:create   |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | vpc:ports:delete   |
+-------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+--------------------+
| :ref:`Rebuilding an ECS (native OpenStack API) <en-us_topic_0065817688>`            | POST /v2/{project_id}/servers/{server_id}/action           | ecs:servers:rebuild       | ecs:servers:list   |
|                                                                                     |                                                            |                           |                    |
|                                                                                     | POST /v2.1/{project_id}/servers/{server_id}/action         |                           | ecs:servers:update |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | ims:images:get     |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | ims:images:list    |
|                                                                                     |                                                            |                           |                    |
|                                                                                     |                                                            |                           | ims:images:update  |
+-------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+--------------------+
| :ref:`Locking an ECS (native OpenStack API) <en-us_topic_0065817690>`               | POST /v2/{project_id}/servers/{server_id}/action           | ecs:servers:lock          | ecs:servers:list   |
|                                                                                     |                                                            |                           |                    |
|                                                                                     | POST /v2.1/{project_id}/servers/{server_id}/action         |                           | ecs:servers:get    |
+-------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+--------------------+
| :ref:`Unlocking an ECS (native OpenStack API) <en-us_topic_0065817691>`             | POST /v2/{project_id}/servers/{server_id}/action           | ecs:servers:unlock        | ecs:servers:list   |
|                                                                                     |                                                            |                           |                    |
|                                                                                     | POST /v2.1/{project_id}/servers/{server_id}/action         |                           | ecs:servers:get    |
+-------------------------------------------------------------------------------------+------------------------------------------------------------+---------------------------+--------------------+
