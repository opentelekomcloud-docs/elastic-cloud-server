:original_name: en-us_topic_0103071515.html

.. _en-us_topic_0103071515:

SSH Key Management
==================

+---------------------------------------------------------------+------------------------------------------------------+---------------------------+----------------------+
| Permission                                                    | API                                                  | Action                    | Dependent Permission |
+===============================================================+======================================================+===========================+======================+
| Creating and Importing an SSH Key Pair (Native OpenStack API) | POST /v2/{project_id}/os-keypairs                    | ecs:serverKeypairs:create | N/A                  |
|                                                               |                                                      |                           |                      |
|                                                               | POST /v2.1/{project_id}/os-keypairs                  |                           |                      |
+---------------------------------------------------------------+------------------------------------------------------+---------------------------+----------------------+
| Querying an SSH Key Pair (Native OpenStack API)               | GET /v2/{project_id}/os-keypairs/{keypair_name}      | ecs:serverKeypairs:get    | N/A                  |
|                                                               |                                                      |                           |                      |
|                                                               | GET /v2.1/{project_id}/os-keypairs/{keypair_name}    |                           |                      |
+---------------------------------------------------------------+------------------------------------------------------+---------------------------+----------------------+
| Querying SSH Key Pairs (Native OpenStack API)                 | GET /v2/{project_id}/os-keypairs                     | ecs:serverKeypairs:list   | N/A                  |
|                                                               |                                                      |                           |                      |
|                                                               | GET /v2.1/{project_id}/os-keypairs                   |                           |                      |
+---------------------------------------------------------------+------------------------------------------------------+---------------------------+----------------------+
| Deleting an SSH Key Pair (Native OpenStack API)               | DELETE /v2/{project_id}/os-keypairs/{keypair_name}   | ecs:serverKeypairs:delete | N/A                  |
|                                                               |                                                      |                           |                      |
|                                                               | DELETE /v2.1/{project_id}/os-keypairs/{keypair_name} |                           |                      |
+---------------------------------------------------------------+------------------------------------------------------+---------------------------+----------------------+
