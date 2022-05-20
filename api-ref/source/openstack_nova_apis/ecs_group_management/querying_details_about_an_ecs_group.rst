:original_name: en-us_topic_0065817722.html

.. _en-us_topic_0065817722:

Querying Details About an ECS Group
===================================

Function
--------

This API is used to query details bout an ECS group.

URI
---

GET /v2.1/{project_id}/os-server-groups/{server_group_id}

GET /v2/{project_id}/os-server-groups/{server_group_id}

:ref:`Table 1 <en-us_topic_0065817722__table1773113411618>` describes the parameters in the URI.

.. _en-us_topic_0065817722__table1773113411618:

.. table:: **Table 1** Parameter description

   =============== ========= =============================
   Parameter       Mandatory Description
   =============== ========= =============================
   project_id      Yes       Specifies the project ID.
   server_group_id Yes       Specifies the ECS group UUID.
   =============== ========= =============================

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0065817722__table176896216171>` describes the response parameters.

.. _en-us_topic_0065817722__table176896216171:

.. table:: **Table 2** Response parameters

   +--------------+--------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Type   | Description                                                                                                                         |
   +==============+========+=====================================================================================================================================+
   | server_group | Object | Specifies the ECS group information. For details, see :ref:`Table 3 <en-us_topic_0065817722__en-us_topic_0057973159_table5520021>`. |
   +--------------+--------+-------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817722__en-us_topic_0057973159_table5520021:

.. table:: **Table 3** **server_group** parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                   |
   +=======================+=======================+===============================================================================+
   | id                    | String                | Specifies the ECS group UUID.                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | name                  | String                | Specifies the ECS group name.                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | policies              | Array of strings      | Specifies the policies associated with the ECS group.                         |
   |                       |                       |                                                                               |
   |                       |                       | -  **anti-affinity**: ECSs in this group must be deployed on different hosts. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | members               | Array of strings      | Specifies the ECSs contained in the ECS group.                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | metadata              | Object                | Specifies the ECS group metadata.                                             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | project_id            | String                | Specifies the tenant ID in UUID format for the ECS group.                     |
   |                       |                       |                                                                               |
   |                       |                       | This parameter is supported in microversion 2.13 and later.                   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | user_id               | String                | Specifies the user ID in UUID format for the ECS group.                       |
   |                       |                       |                                                                               |
   |                       |                       | This parameter is supported in microversion 2.13 and later.                   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/os-server-groups/5bbcc3c4-1da2-4437-a48a-66f15b1b13f9
   GET https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/os-server-groups/5bbcc3c4-1da2-4437-a48a-66f15b1b13f9

Example Response
----------------

.. code-block::

   {
       "server_group": {
           "id": "5bbcc3c4-1da2-4437-a48a-66f15b1b13f9",
           "name": "test",
           "policies": ["anti-affinity"],
           "members": [],
           "metadata": {},
           "project_id": "9c53a566cb3443ab910cf0daebca90c4"
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
