Lifecycle Management
====================



.. _ENUSTOPIC0103071510table1587111571724:

+------------------------------------------------------+-----------------------------------------------+----------------------------+----------------------------+
| Permission                                           | API                                           | Action                     | Dependent Permission       |
+======================================================+===============================================+============================+============================+
| Creating an ECS                                      | POST /v1/{project_id}/cloudservers            | -  Assigning a New EIP     | -  Assigning a New EIP     |
|                                                      |                                               |                            |                            |
|                                                      |                                               |    ecs:cloudServers:create |    vpc:publicIps:create    |
|                                                      |                                               |                            |                            |
|                                                      |                                               | -  Using an Existing EIP   | -  Using an Existing EIP   |
|                                                      |                                               |                            |                            |
|                                                      |                                               |    ecs:cloudServers:create |    vpc:publicIps:update    |
+------------------------------------------------------+-----------------------------------------------+----------------------------+----------------------------+
| Deleting ECSs                                        | POST /v1/{project_id}/cloudservers/delete     | ecs:cloudServers:delete    | N/A                        |
+------------------------------------------------------+-----------------------------------------------+----------------------------+----------------------------+
| Querying Details About ECSs (Native OpenStack API)   | GET /v2/{project_id}/servers/detail           | ecs:servers:list           | ecs:servers:get            |
|                                                      |                                               |                            |                            |
|                                                      | GET /v2.1/{project_id}/servers/detail         |                            | ecs:serverVolumes:use      |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | ecs:diskConfigs:use        |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | ecs:securityGroups:use     |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | ecs:serverKeypairs:get     |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:securityGroups:get     |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:securityGroupRules:get |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:networks:get           |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:subnets:get            |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:ports:get              |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:routers:get            |
+------------------------------------------------------+-----------------------------------------------+----------------------------+----------------------------+
| Querying ECSs (Native OpenStack API)                 | GET /v2/{project_id}/servers                  | ecs:servers:list           | N/A                        |
|                                                      |                                               |                            |                            |
|                                                      | GET /v2.1/{project_id}/servers                |                            |                            |
+------------------------------------------------------+-----------------------------------------------+----------------------------+----------------------------+
| Querying Details About an ECS (Native OpenStack API) | GET /v2/{project_id}/servers/{server_id}      | ecs:servers:get            | ecs:serverVolumes:use      |
|                                                      |                                               |                            |                            |
|                                                      | GET /v2.1/{project_id}/servers/{server_id}    |                            | ecs:diskConfigs:use        |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | ecs:securityGroups:use     |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | ecs:serverKeypairs:get     |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:securityGroups:get     |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:securityGroupRules:get |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:networks:get           |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:subnets:get            |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:ports:get              |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:routers:get            |
+------------------------------------------------------+-----------------------------------------------+----------------------------+----------------------------+
| Creating an ECS (Native OpenStack API)               | POST /v2/{project_id}/servers                 | ecs:servers:create         | ecs:servers:get            |
|                                                      |                                               |                            |                            |
|                                                      | POST /v2/{project_id}/os-volumes_boot         |                            | ecs:serverInterfaces:use   |
|                                                      |                                               |                            |                            |
|                                                      | POST /v2.1/{project_id}/servers               |                            | ecs:serverInterfaces:get   |
|                                                      |                                               |                            |                            |
|                                                      | POST /v2.1/{project_id}/os-volumes_boot       |                            | ecs:flavors:get            |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | ecs:securityGroups:use     |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | evs:volumes:list           |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | evs:volumes:get            |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | evs:volumes:create         |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | evs:volumes:attach         |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | evs:volumes:manage         |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:securityGroups:get     |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:networks:get           |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:networks:update        |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:subnets:get            |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:subnets:update         |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:ports:create           |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:ports:update           |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:ports:get              |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:ports:delete           |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:networks:create        |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:subnets:create         |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:routers:get            |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | vpc:routers:update         |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | ims:images:list            |
|                                                      |                                               |                            |                            |
|                                                      |                                               |                            | ims:images:get             |
+------------------------------------------------------+-----------------------------------------------+----------------------------+----------------------------+
| Deleting an ECS (Native OpenStack API)               | DELETE /v2/{project_id}/servers/{server_id}   | ecs:servers:delete         | N/A                        |
|                                                      |                                               |                            |                            |
|                                                      | DELETE /v2.1/{project_id}/servers/{server_id} |                            |                            |
+------------------------------------------------------+-----------------------------------------------+----------------------------+----------------------------+
| Modifying an ECS (Native OpenStack API)              | PUT /v2/{project_id}/servers/{server_id}      | ecs:servers:update         | ecs:servers:get            |
|                                                      |                                               |                            |                            |
|                                                      | PUT /v2.1/{project_id}/servers/{server_id}    |                            |                            |
+------------------------------------------------------+-----------------------------------------------+----------------------------+----------------------------+


