:original_name: en-us_topic_0103071516.html

.. _en-us_topic_0103071516:

Metadata Management
===================

+----------------------------------------------------------------------+--------------------------------------------------------------+----------------------------------+----------------------+
| Permission                                                           | API                                                          | Action                           | Dependent Permission |
+======================================================================+==============================================================+==================================+======================+
| Querying ECS Metadata (Native OpenStack API)                         | GET /v2/{project_id}/servers/{server_id}/metadata            | ecs:servers:listMetadata         | N/A                  |
|                                                                      |                                                              |                                  |                      |
|                                                                      | GET /v2.1/{project_id}/servers/{server_id}/metadata          |                                  |                      |
+----------------------------------------------------------------------+--------------------------------------------------------------+----------------------------------+----------------------+
| Querying Metadata of an ECS Key (Native OpenStack API)               | GET /v2/{project_id}/servers/{server_id}/metadata/{key}      | ecs:servers:getMetadata          | N/A                  |
|                                                                      |                                                              |                                  |                      |
|                                                                      | GET /v2.1/{project_id}/servers/{server_id}/metadata/{key}    |                                  |                      |
+----------------------------------------------------------------------+--------------------------------------------------------------+----------------------------------+----------------------+
| Deleting Specified ECS Metadata (Native OpenStack API)               | DELETE /v2/{project_id}/servers/{server_id}/metadata/{key}   | ecs:servers:setMetadata          | N/A                  |
|                                                                      |                                                              |                                  |                      |
|                                                                      | DELETE /v2.1/{project_id}/servers/{server_id}/metadata/{key} |                                  |                      |
+----------------------------------------------------------------------+--------------------------------------------------------------+----------------------------------+----------------------+
| Modifying the Key Value in Metadata of an ECS (Native OpenStack API) | PUT /v2/{project_id}/servers/{server_id}/metadata/{key}      | ecs:servers:setMetadata          | N/A                  |
|                                                                      |                                                              |                                  |                      |
|                                                                      | PUT /v2.1/{project_id}/servers/{server_id}/metadata/{key}    |                                  |                      |
+----------------------------------------------------------------------+--------------------------------------------------------------+----------------------------------+----------------------+
| Updating ECS Metadata (Native OpenStack API)                         | POST /v2/{project_id}/servers/{server_id}/metadata           | ecs:servers:setMetadata          | N/A                  |
|                                                                      |                                                              |                                  |                      |
|                                                                      | POST /v2.1/{project_id}/servers/{server_id}/metadata         |                                  |                      |
+----------------------------------------------------------------------+--------------------------------------------------------------+----------------------------------+----------------------+
| Configuring ECS Metadata (Native OpenStack API)                      | PUT /v2/{project_id}/servers/{server_id}/metadata            | ecs:servers:setMetadata          | ecs:servers:get      |
|                                                                      |                                                              |                                  |                      |
|                                                                      | PUT /v2.1/{project_id}/servers/{server_id}/metadata          |                                  |                      |
+----------------------------------------------------------------------+--------------------------------------------------------------+----------------------------------+----------------------+
| Managing Automatic Recovery of an ECS                                | PUT /v1/{project_id}/cloudservers/{server_id}/autorecovery   | ecs:cloudServers:setAutoRecovery | N/A                  |
+----------------------------------------------------------------------+--------------------------------------------------------------+----------------------------------+----------------------+
| Querying Automatic Recovery of an ECS                                | GET /v1/{project_id}/cloudservers/{server_id}/autorecovery   | ecs:cloudServers:getAutoRecovery | N/A                  |
+----------------------------------------------------------------------+--------------------------------------------------------------+----------------------------------+----------------------+
