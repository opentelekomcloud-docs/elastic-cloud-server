:original_name: en-us_topic_0103072347.html

.. _en-us_topic_0103072347:

Security Group Management
=========================

+-------------------------------------------------------------------------+----------------------------------------------------------------------------+------------------------+-------------------------------+
| Permission                                                              | API                                                                        | Action                 | Dependent Permission          |
+=========================================================================+============================================================================+========================+===============================+
| Creating a Security Group (Native OpenStack API)                        | POST /v2/{project_id}/os-security-groups                                   | ecs:securityGroups:use | vpc:securityGroups:get        |
|                                                                         |                                                                            |                        |                               |
|                                                                         | POST /v2.1/{project_id}/os-security-groups                                 |                        | vpc:securityGroups:create     |
|                                                                         |                                                                            |                        |                               |
|                                                                         |                                                                            |                        | vpc:securityGroups:update     |
+-------------------------------------------------------------------------+----------------------------------------------------------------------------+------------------------+-------------------------------+
| Deleting a Security Group (Native OpenStack API)                        | DELETE /v2/{project_id}/os-security-groups/{security_group_id}             | ecs:securityGroups:use | vpc:securityGroups:get        |
|                                                                         |                                                                            |                        |                               |
|                                                                         | DELETE /v2.1/{project_id}/os-security-groups/{security_group_id}           |                        | vpc:securityGroups:delete     |
|                                                                         |                                                                            |                        |                               |
|                                                                         |                                                                            |                        | vpc:securityGroups:update     |
+-------------------------------------------------------------------------+----------------------------------------------------------------------------+------------------------+-------------------------------+
| Querying Details About a Security Group (Native OpenStack API)          | GET /v2/{project_id}/os-security-groups/{security_group_id}                | ecs:securityGroups:use | vpc:securityGroups:get        |
|                                                                         |                                                                            |                        |                               |
|                                                                         | GET /v2.1/{project_id}/os-security-groups/{security_group_id}              |                        |                               |
+-------------------------------------------------------------------------+----------------------------------------------------------------------------+------------------------+-------------------------------+
| Querying Security Groups (Native OpenStack API)                         | GET /v2/{project_id}/os-security-groups                                    | ecs:securityGroups:use | vpc:securityGroups:get        |
|                                                                         |                                                                            |                        |                               |
|                                                                         | GET /v2.1/{project_id}/os-security-groups                                  |                        |                               |
+-------------------------------------------------------------------------+----------------------------------------------------------------------------+------------------------+-------------------------------+
| Creating a Security Group Rule (Native OpenStack API)                   | POST /v2/{project_id}/os-security-group-rules                              | ecs:securityGroups:use | vpc:securityGroups:get        |
|                                                                         |                                                                            |                        |                               |
|                                                                         | POST /v2.1/{project_id}/os-security-group-rules                            |                        | vpc:securityGroups:update     |
|                                                                         |                                                                            |                        |                               |
|                                                                         |                                                                            |                        | vpc:securityGroupRules:get    |
|                                                                         |                                                                            |                        |                               |
|                                                                         |                                                                            |                        | vpc:securityGroupRules:create |
+-------------------------------------------------------------------------+----------------------------------------------------------------------------+------------------------+-------------------------------+
| Deleting a Security Group Rule (Native OpenStack API)                   | DELETE /v2/{project_id}/os-security-group-rules/{security_group_rule_id}   | ecs:securityGroups:use | vpc:securityGroups:get        |
|                                                                         |                                                                            |                        |                               |
|                                                                         | DELETE /v2.1/{project_id}/os-security-group-rules/{security_group_rule_id} |                        | vpc:securityGroups:update     |
|                                                                         |                                                                            |                        |                               |
|                                                                         |                                                                            |                        | vpc:securityGroupRules:get    |
|                                                                         |                                                                            |                        |                               |
|                                                                         |                                                                            |                        | vpc:securityGroupRules:delete |
+-------------------------------------------------------------------------+----------------------------------------------------------------------------+------------------------+-------------------------------+
| Updating Information About a Security Group (Native OpenStack API)      | PUT /v2/{project_id}/os-security-groups/{security_group_id}                | ecs:securityGroups:use | vpc:securityGroups:get        |
|                                                                         |                                                                            |                        |                               |
|                                                                         | PUT /v2.1/{project_id}/os-security-groups/{security_group_id}              |                        | vpc:securityGroups:update     |
+-------------------------------------------------------------------------+----------------------------------------------------------------------------+------------------------+-------------------------------+
| Querying Security Groups to Which an ECS Belongs (Native OpenStack API) | GET /v2/{project_id}/servers/{server_id}/os-security-groups                | ecs:securityGroups:use | vpc:securityGroups:get        |
|                                                                         |                                                                            |                        |                               |
|                                                                         | GET /v2.1/{project_id}/servers/{server_id}/os-security-groups              |                        |                               |
+-------------------------------------------------------------------------+----------------------------------------------------------------------------+------------------------+-------------------------------+
| Adding a Security Group (Native OpenStack API)                          | POST /v2/{project_id}/servers/{server_id}/action                           | ecs:securityGroups:use | ecs:servers:get               |
|                                                                         |                                                                            |                        |                               |
|                                                                         | POST /v2.1/{project_id}/servers/{server_id}/action                         |                        | vpc:securityGroups:get        |
|                                                                         |                                                                            |                        |                               |
|                                                                         |                                                                            |                        | vpc:securityGroups:create     |
|                                                                         |                                                                            |                        |                               |
|                                                                         |                                                                            |                        | vpc:securityGroups:update     |
|                                                                         |                                                                            |                        |                               |
|                                                                         |                                                                            |                        | vpc:ports:get                 |
|                                                                         |                                                                            |                        |                               |
|                                                                         |                                                                            |                        | vpc:ports:update              |
+-------------------------------------------------------------------------+----------------------------------------------------------------------------+------------------------+-------------------------------+
| Removing a Security Group (Native OpenStack API)                        | POST /v2/{project_id}/servers/{server_id}/action                           | ecs:securityGroups:use | ecs:servers:get               |
|                                                                         |                                                                            |                        |                               |
|                                                                         | POST /v2.1/{project_id}/servers/{server_id}/action                         |                        | vpc:securityGroups:get        |
|                                                                         |                                                                            |                        |                               |
|                                                                         |                                                                            |                        | vpc:securityGroups:delete     |
|                                                                         |                                                                            |                        |                               |
|                                                                         |                                                                            |                        | vpc:securityGroups:update     |
|                                                                         |                                                                            |                        |                               |
|                                                                         |                                                                            |                        | vpc:ports:get                 |
|                                                                         |                                                                            |                        |                               |
|                                                                         |                                                                            |                        | vpc:ports:update              |
+-------------------------------------------------------------------------+----------------------------------------------------------------------------+------------------------+-------------------------------+
