:original_name: en-us_topic_0103071516.html

.. _en-us_topic_0103071516:

Metadata Management
===================

+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------+---------------------------------+-----------------+
| Permission                                                                                         | API                                                          | Action                          | Dependencies    |
+====================================================================================================+==============================================================+=================================+=================+
| :ref:`Querying ECS metadata (native OpenStack API) <en-us_topic_0065817713>`                       | GET /v2/{project_id}/servers/{server_id}/metadata            | ecs:servers:listMetadata        | ``-``           |
|                                                                                                    |                                                              |                                 |                 |
|                                                                                                    | GET /v2.1/{project_id}/servers/{server_id}/metadata          |                                 |                 |
+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------+---------------------------------+-----------------+
| :ref:`Obtaining ECS metadata with a specified key (native OpenStack API) <en-us_topic_0065817714>` | GET /v2/{project_id}/servers/{server_id}/metadata/{key}      | ecs:servers:getMetadata         | ecs:servers:get |
|                                                                                                    |                                                              |                                 |                 |
|                                                                                                    | GET /v2.1/{project_id}/servers/{server_id}/metadata/{key}    |                                 |                 |
+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------+---------------------------------+-----------------+
| :ref:`Deleting specified ECS metadata (native OpenStack API) <en-us_topic_0025560299>`             | DELETE /v2/{project_id}/servers/{server_id}/metadata/{key}   | ecs:servers:setMetadata         | ecs:servers:get |
|                                                                                                    |                                                              |                                 |                 |
|                                                                                                    | DELETE /v2.1/{project_id}/servers/{server_id}/metadata/{key} |                                 |                 |
+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------+---------------------------------+-----------------+
| :ref:`Modifying ECS metadata with a specified key (native OpenStack API) <en-us_topic_0025567413>` | PUT /v2/{project_id}/servers/{server_id}/metadata/{key}      | ecs:servers:setMetadata         | ecs:servers:get |
|                                                                                                    |                                                              |                                 |                 |
|                                                                                                    | PUT /v2.1/{project_id}/servers/{server_id}/metadata/{key}    |                                 |                 |
+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------+---------------------------------+-----------------+
| :ref:`Updating ECS metadata (native OpenStack API) <en-us_topic_0025560298>`                       | POST /v2/{project_id}/servers/{server_id}/metadata           | ecs:servers:setMetadata         | ecs:servers:get |
|                                                                                                    |                                                              |                                 |                 |
|                                                                                                    | POST /v2.1/{project_id}/servers/{server_id}/metadata         |                                 |                 |
+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------+---------------------------------+-----------------+
| :ref:`Configuring ECS metadata (native OpenStack API) <en-us_topic_0077847902>`                    | PUT /v2/{project_id}/servers/{server_id}/metadata            | ecs:servers:setMetadata         | ecs:servers:get |
|                                                                                                    |                                                              |                                 |                 |
|                                                                                                    | PUT /v2.1/{project_id}/servers/{server_id}/metadata          |                                 |                 |
+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------+---------------------------------+-----------------+
| :ref:`Updating ECS metadata <en-us_topic_0122110044>`                                              | POST /v1/{project_id}/cloudservers/{server_id}/metadata      | ecs:cloudServers:updateMetadata | ``-``           |
+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------+---------------------------------+-----------------+
