Password Management
===================



.. _ENUSTOPIC0161341998table1642432772714:

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


