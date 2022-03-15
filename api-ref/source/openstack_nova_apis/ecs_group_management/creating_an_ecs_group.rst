Creating an ECS Group
=====================

Function
--------

This API is used to create an ECS group.

Constraints
-----------

Only anti-affinity groups are supported.

URI
---

POST /v2.1/{project_id}/os-server-groups

POST /v2/{project_id}/os-server-groups

`Table 1 <#enustopic0065817720table1334523718138>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817720table1334523718138:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0065817720table173242991418>`__ describes the request parameters.



.. _ENUSTOPIC0065817720table173242991418:

.. table:: **Table 2** Request parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                               |
   +==============+===========+========+===========================================================================================================================+
   | server_group | Yes       | Object | Specifies the ECS group information. For details, see `Table 3 <#enustopic0065817720enustopic0057973153table19917766>`__. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817720enustopic0057973153table19917766:

.. table:: **Table 3** **server_group** field description

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                          |
   +=================+=================+==================+======================================================================================================================================================================================================================+
   | name            | Yes             | String           | Specifies the ECS group name. The value contains 1 to 255 characters.                                                                                                                                                |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | policies        | Yes             | Array of strings | Specifies the policies associated with the ECS group. Options:                                                                                                                                                       |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | -  **anti-affinity**: ECSs in this group must be deployed on different hosts.                                                                                                                                        |
   |                 |                 |                  | -  **affinity**: ECSs in this group must be deployed on the same host.                                                                                                                                               |
   |                 |                 |                  | -  **soft-anti-affinity**: ECSs in this group are deployed on different hosts if possible. If the ECSs cannot be deployed on different hosts, deploy them based on the actual condition for successful ECS creation. |
   |                 |                 |                  | -  **soft-affinity**: ECSs in this group are deployed on the same host if possible. If the ECSs cannot be deployed on the same host, deploy them based on the actual condition for successful ECS creation.          |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | .. note::                                                                                                                                                                                                            |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  |    Only the anti-affinity policy is supported. The other three policies are retained to be compatible with native APIs. However, you are not advised to use the other three policies.                                |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  |    You are suggested to use the policy described in `Creating an ECS Group <../../apis_recommended/ecs_group_management/creating_an_ecs_group.html>`__.                                                              |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

`Table 4 <#enustopic0065817720table14250354151412>`__ describes the response parameters.



.. _ENUSTOPIC0065817720table14250354151412:

.. table:: **Table 4** Response parameters

   +--------------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Type   | Description                                                                                                              |
   +==============+========+==========================================================================================================================+
   | server_group | Object | Specifies the ECS group information. For details, see `Table 5 <#enustopic0065817720enustopic0057973153table7944126>`__. |
   +--------------+--------+--------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817720enustopic0057973153table7944126:

.. table:: **Table 5** **server_group** field description

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                       |
   +=======================+=======================+===================================================================================================================================================================================================================+
   | id                    | String                | Specifies the ECS group UUID.                                                                                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the ECS group name.                                                                                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | policies              | Array of strings      | Specifies the policies associated with the ECS group. Options:                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                   |
   |                       |                       | **anti-affinity**: ECSs in this group must be deployed on different hosts.                                                                                                                                        |
   |                       |                       |                                                                                                                                                                                                                   |
   |                       |                       | **affinity**: ECSs in this group must be deployed on the same host.                                                                                                                                               |
   |                       |                       |                                                                                                                                                                                                                   |
   |                       |                       | **soft-anti-affinity**: ECSs in this group are deployed on different hosts if possible. If the ECSs cannot be deployed on different hosts, deploy them based on the actual condition for successful ECS creation. |
   |                       |                       |                                                                                                                                                                                                                   |
   |                       |                       | **soft-affinity**: ECSs in this group are deployed on the same host if possible. If the ECSs cannot be deployed on the same host, deploy them based on the actual condition for successful ECS creation.          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | members               | Array of strings      | Specifies the ECSs contained in an ECS group.                                                                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata              | Object                | Specifies the ECS group metadata.                                                                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                | Specifies the tenant ID in UUID format for the ECS group.                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                                                   |
   |                       |                       | This parameter is supported in microversion 2.13 and later.                                                                                                                                                       |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_id               | String                | Specifies the user ID in UUID format for the ECS group.                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                   |
   |                       |                       | This parameter is supported in microversion 2.13 and later.                                                                                                                                                       |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/os-server-groups
   POST https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/os-server-groups

.. code-block::

   {
       "server_group": {
           "name": "test",
           "policies": ["anti-affinity"]
       }
   }

Example Response
----------------

.. code-block::

   {
       "server_group": {
           "id": "5bbcc3c4-1da2-4437-a48a-66f15b1b13f9",
           "name": "test",
           "policies": [
               "anti-affinity"
           ],
           "members": [],
           "metadata": {}
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


