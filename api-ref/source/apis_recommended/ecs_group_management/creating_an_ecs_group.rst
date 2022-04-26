:original_name: en-us_topic_0161097718.html

.. _en-us_topic_0161097718:

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

:ref:`Table 1 <en-us_topic_0161097718__table11729101619308>` describes the parameters in the URI.

.. _en-us_topic_0161097718__table11729101619308:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0161097718__table146581144163019>` describes the request parameters.

.. _en-us_topic_0161097718__table146581144163019:

.. table:: **Table 2** Request parameters

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                          |
   +==============+===========+========+======================================================================================================================================+
   | server_group | Yes       | Object | Specifies the ECS group information. For details, see :ref:`Table 3 <en-us_topic_0161097718__en-us_topic_0057973153_table19917766>`. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0161097718__en-us_topic_0057973153_table19917766:

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

:ref:`Table 4 <en-us_topic_0161097718__table776421293115>` describes the response parameters.

.. _en-us_topic_0161097718__table776421293115:

.. table:: **Table 4** Response parameters

   +--------------+--------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Type   | Description                                                                                                                         |
   +==============+========+=====================================================================================================================================+
   | server_group | Object | Specifies the ECS group information. For details, see :ref:`Table 5 <en-us_topic_0161097718__en-us_topic_0057973153_table7944126>`. |
   +--------------+--------+-------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0161097718__en-us_topic_0057973153_table7944126:

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
