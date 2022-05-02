:original_name: en-us_topic_0065817721.html

.. _en-us_topic_0065817721:

Querying ECS Groups
===================

Function
--------

This API is used to query ECS groups.

URI
---

GET /v2.1/{project_id}/os-server-groups

GET /v2/{project_id}/os-server-groups

:ref:`Table 1 <en-us_topic_0065817721__table12344152719154>` describes the parameters in the URI.

.. _en-us_topic_0065817721__table12344152719154:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Parameters in the following table can be used as URI parameters to filter query results.

Usage: /v2/{project_id}/os-server-groups?

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0065817721__table151218547156>` describes the response parameters.

.. _en-us_topic_0065817721__table151218547156:

.. table:: **Table 2** Response parameters

   +---------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type             | Description                                                                                                                          |
   +===============+==================+======================================================================================================================================+
   | server_groups | Array of objects | Specifies the ECS group information. For details, see :ref:`Table 3 <en-us_topic_0065817721__en-us_topic_0057973158_table47937085>`. |
   +---------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817721__en-us_topic_0057973158_table47937085:

.. table:: **Table 3** **server_groups** parameter information

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                          |
   +=======================+=======================+======================================================================================================================================================================================================================+
   | id                    | String                | Specifies the ECS group UUID.                                                                                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the ECS group name.                                                                                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | members               | Array of strings      | Specifies the ECSs in an ECS group.                                                                                                                                                                                  |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata              | Object                | Specifies the ECS group metadata.                                                                                                                                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                | Specifies the tenant ID in UUID format for the ECS group.                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                      |
   |                       |                       | This parameter is supported in microversion 2.13 and later.                                                                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | policies              | Array of strings      | Specifies the policies associated with the ECS group. Options:                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                      |
   |                       |                       | -  **anti-affinity**: ECSs in this group must be deployed on different hosts.                                                                                                                                        |
   |                       |                       | -  **affinity**: ECSs in this group must be deployed on the same host.                                                                                                                                               |
   |                       |                       | -  **soft-anti-affinity**: ECSs in this group are deployed on different hosts if possible. If the ECSs cannot be deployed on different hosts, deploy them based on the actual condition for successful ECS creation. |
   |                       |                       | -  **soft-affinity**: ECSs in this group are deployed on the same host if possible. If the ECSs cannot be deployed on the same host, deploy them based on the actual condition for successful ECS creation.          |
   |                       |                       |                                                                                                                                                                                                                      |
   |                       |                       | .. note::                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                      |
   |                       |                       |    Only anti-affinity policies are supported. You are not advised to use other policies. If other policies are used, creating the ECS group will fail.                                                               |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_id               | String                | Specifies the user ID in UUID format for the ECS group.                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                      |
   |                       |                       | This parameter is supported in microversion 2.13 and later.                                                                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/os-server-groups
   GET https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/os-server-groups

Example Response
----------------

.. code-block::

   {
       "server_groups": [
           {
               "id": "616fb98f-46ca-475e-917e-2563e5a8cd19",
               "name": "test",
               "policies": ["anti-affinity"],
               "members": [],
               "metadata": {},
               "project_id": "9c53a566cb3443ab910cf0daebca90c4"
           }
       ]
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
