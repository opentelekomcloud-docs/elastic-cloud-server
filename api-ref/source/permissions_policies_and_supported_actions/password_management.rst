:original_name: en-us_topic_0161341998.html

.. _en-us_topic_0161341998:

Password Management
===================

+---------------------------------------------------------------------------+------------------------------------------------------------------+----------------------------+----------------------+
| Permission                                                                | API                                                              | Action                     | Dependent Permission |
+===========================================================================+==================================================================+============================+======================+
| Obtaining the Password for Logging In to a Windows ECS (Native OpenStack) | GET /v2/{project_id}/servers/{server_id}/os-server-password      | ecs:serverPasswords:manage | N/A                  |
|                                                                           |                                                                  |                            |                      |
|                                                                           | GET /v2.1/{project_id}/servers/{server_id}/os-server-password    |                            |                      |
+---------------------------------------------------------------------------+------------------------------------------------------------------+----------------------------+----------------------+
| Deleting the Password for Logging In to a Windows ECS (Native OpenStack)  | DELETE /v2/{project_id}/servers/{server_id}/os-server-password   | ecs:serverPasswords:manage | N/A                  |
|                                                                           |                                                                  |                            |                      |
|                                                                           | DELETE /v2.1/{project_id}/servers/{server_id}/os-server-password |                            |                      |
+---------------------------------------------------------------------------+------------------------------------------------------------------+----------------------------+----------------------+
