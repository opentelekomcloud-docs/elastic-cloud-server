Creating an ECS Group
=====================

Function
--------

This API is used to create an ECS group.

Constraints
-----------

Only anti-affinity policies are supported.

URI
---

POST /v1/{project_id}/cloudservers/os-server-groups

`Table 1 <#enustopic0161097718table11729101619308>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0161097718table11729101619308:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0161097718table146581144163019>`__ describes the request parameters.



.. _ENUSTOPIC0161097718table146581144163019:

.. table:: **Table 2** Request parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                               |
   +==============+===========+========+===========================================================================================================================+
   | server_group | Yes       | Object | Specifies the ECS group information. For details, see `Table 3 <#enustopic0161097718enustopic0057973153table19917766>`__. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0161097718enustopic0057973153table19917766:

.. table:: **Table 3** **server_group** parameters

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
   |                 |                 |                  |    Only anti-affinity policies are supported. You are not advised to use other policies. If other policies are used, creating the ECS group will fail.                                                               |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

`Table 4 <#enustopic0161097718table776421293115>`__ describes the response parameters.



.. _ENUSTOPIC0161097718table776421293115:

.. table:: **Table 4** Response parameters

   +--------------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Type   | Description                                                                                                              |
   +==============+========+==========================================================================================================================+
   | server_group | Object | Specifies the ECS group information. For details, see `Table 5 <#enustopic0161097718enustopic0057973153table7944126>`__. |
   +--------------+--------+--------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0161097718enustopic0057973153table7944126:

.. table:: **Table 5** **server_group** parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                          |
   +=======================+=======================+======================================================================================================================================================================================================================+
   | id                    | String                | Specifies the ECS group UUID.                                                                                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the ECS group name.                                                                                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | policies              | Array of strings      | Specifies the policies associated with the ECS group. Options:                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                      |
   |                       |                       | -  **anti-affinity**: ECSs in this group must be deployed on different hosts.                                                                                                                                        |
   |                       |                       | -  **affinity**: ECSs in this group must be deployed on the same host.                                                                                                                                               |
   |                       |                       | -  **soft-anti-affinity**: ECSs in this group are deployed on different hosts if possible. If the ECSs cannot be deployed on different hosts, deploy them based on the actual condition for successful ECS creation. |
   |                       |                       | -  **soft-affinity**: ECSs in this group are deployed on the same host if possible. If the ECSs cannot be deployed on the same host, deploy them based on the actual condition for successful ECS creation.          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | members               | Array of strings      | Specifies the IDs of the ECSs in an ECS group.                                                                                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata              | Object                | Specifies the ECS group metadata.                                                                                                                                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v1/{project_id}/cloudservers/os-server-groups

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

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


