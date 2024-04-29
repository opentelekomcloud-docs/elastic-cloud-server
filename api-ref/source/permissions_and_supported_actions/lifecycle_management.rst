:original_name: en-us_topic_0103071510.html

.. _en-us_topic_0103071510:

Lifecycle Management
====================

+----------------------------------------------------------------------------------------------+-----------------------------------------------+-----------------------------------+----------------------------+
| Permission                                                                                   | API                                           | Action                            | Dependencies               |
+==============================================================================================+===============================================+===================================+============================+
| :ref:`Creating ECSs (pay-per-use) <en-us_topic_0020212668>`                                  | POST /v1/{project_id}/cloudservers            | -  Assigning a New EIP            | -  Assigning a New EIP     |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |    ecs:cloudServers:createServers |    vpc:publicIps:create    |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               | -  Using an Existing EIP          | -  Using an Existing EIP   |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |    ecs:cloudServers:createServers |    vpc:publicIps:update    |
+----------------------------------------------------------------------------------------------+-----------------------------------------------+-----------------------------------+----------------------------+
| :ref:`Deleting ECSs <en-us_topic_0020212679>`                                                | POST /v1/{project_id}/cloudservers/delete     | ecs:cloudServers:deleteServers    | ``-``                      |
+----------------------------------------------------------------------------------------------+-----------------------------------------------+-----------------------------------+----------------------------+
| :ref:`Querying details about ECSs <en-us_topic_0094148850>`                                  | GET /v1/{project_id}/cloudservers/detail      | ecs:cloudServers:list             | ``-``                      |
+----------------------------------------------------------------------------------------------+-----------------------------------------------+-----------------------------------+----------------------------+
| :ref:`Querying details about a specific ECS <en-us_topic_0094148849>`                        | GET /v1/{project_id}/cloudservers/{server_id} | ecs:cloudServers:showServer       | ``-``                      |
+----------------------------------------------------------------------------------------------+-----------------------------------------------+-----------------------------------+----------------------------+
| :ref:`Modifying ECS details <en-us_topic_0118308527>`                                        | PUT /v1/{project_id}/cloudservers/{server_id} | ecs:cloudServers:updateServer     | ``-``                      |
+----------------------------------------------------------------------------------------------+-----------------------------------------------+-----------------------------------+----------------------------+
| :ref:`Querying details about ECSs (native OpenStack API) <en-us_topic_0020212689>`           | GET /v2/{project_id}/servers/detail           | ecs:servers:list                  | ecs:servers:get            |
|                                                                                              |                                               |                                   |                            |
|                                                                                              | GET /v2.1/{project_id}/servers/detail         |                                   | ecs:serverVolumes:use      |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | ecs:diskConfigs:use        |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | ecs:securityGroups:use     |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | ecs:serverKeypairs:get     |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:securityGroups:get     |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:securityGroupRules:get |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:networks:get           |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:subnets:get            |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:ports:get              |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:routers:get            |
+----------------------------------------------------------------------------------------------+-----------------------------------------------+-----------------------------------+----------------------------+
| :ref:`Querying a list of ECSs (native OpenStack API) <en-us_topic_0020212688>`               | GET /v2/{project_id}/servers                  | ecs:servers:list                  | ``-``                      |
|                                                                                              |                                               |                                   |                            |
|                                                                                              | GET /v2.1/{project_id}/servers                |                                   |                            |
+----------------------------------------------------------------------------------------------+-----------------------------------------------+-----------------------------------+----------------------------+
| :ref:`Querying details about a specific ECS (native OpenStack API) <en-us_topic_0020212690>` | GET /v2/{project_id}/servers/{server_id}      | ecs:servers:get                   | ecs:serverVolumes:use      |
|                                                                                              |                                               |                                   |                            |
|                                                                                              | GET /v2.1/{project_id}/servers/{server_id}    |                                   | ecs:diskConfigs:use        |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | ecs:securityGroups:use     |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | ecs:serverKeypairs:get     |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:securityGroups:get     |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:securityGroupRules:get |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:networks:get           |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:subnets:get            |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:ports:get              |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:routers:get            |
+----------------------------------------------------------------------------------------------+-----------------------------------------------+-----------------------------------+----------------------------+
| :ref:`Creating an ECS (native OpenStack API) <en-us_topic_0068473331>`                       | POST /v2/{project_id}/servers                 | ecs:servers:create                | ecs:servers:get            |
|                                                                                              |                                               |                                   |                            |
|                                                                                              | POST /v2/{project_id}/os-volumes_boot         |                                   | ecs:serverInterfaces:use   |
|                                                                                              |                                               |                                   |                            |
|                                                                                              | POST /v2.1/{project_id}/servers               |                                   | ecs:serverInterfaces:get   |
|                                                                                              |                                               |                                   |                            |
|                                                                                              | POST /v2.1/{project_id}/os-volumes_boot       |                                   | ecs:flavors:get            |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | ecs:securityGroups:use     |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | evs:volumes:list           |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | evs:volumes:get            |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | evs:volumes:create         |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | evs:volumes:attach         |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | evs:volumes:manage         |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:securityGroups:get     |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:networks:get           |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:networks:update        |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:subnets:get            |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:subnets:update         |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:ports:create           |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:ports:update           |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:ports:get              |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:ports:delete           |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:networks:create        |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:subnets:create         |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:routers:get            |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | vpc:routers:update         |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | ims:images:list            |
|                                                                                              |                                               |                                   |                            |
|                                                                                              |                                               |                                   | ims:images:get             |
+----------------------------------------------------------------------------------------------+-----------------------------------------------+-----------------------------------+----------------------------+
| :ref:`Deleting an ECS (native OpenStack API) <en-us_topic_0025560296>`                       | DELETE /v2/{project_id}/servers/{server_id}   | ecs:servers:delete                | ``-``                      |
|                                                                                              |                                               |                                   |                            |
|                                                                                              | DELETE /v2.1/{project_id}/servers/{server_id} |                                   |                            |
+----------------------------------------------------------------------------------------------+-----------------------------------------------+-----------------------------------+----------------------------+
| :ref:`Modifying ECS details (native OpenStack API) <en-us_topic_0020212692>`                 | PUT /v2/{project_id}/servers/{server_id}      | ecs:servers:update                | ecs:servers:get            |
|                                                                                              |                                               |                                   |                            |
|                                                                                              | PUT /v2.1/{project_id}/servers/{server_id}    |                                   |                            |
+----------------------------------------------------------------------------------------------+-----------------------------------------------+-----------------------------------+----------------------------+
