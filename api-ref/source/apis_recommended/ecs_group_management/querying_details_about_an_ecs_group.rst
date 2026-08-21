:original_name: en-us_topic_0175597847.html

.. _en-us_topic_0175597847:

Querying Details About an ECS Group
===================================

Function
--------

This API is used to query details about an ECS group.

URI
---

GET /v1/{project_id}/cloudservers/os-server-groups/{server_group_id}

:ref:`Table 1 <en-us_topic_0175597847__table050833691012>` describes the parameters in the URI.

.. _en-us_topic_0175597847__table050833691012:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+------------------------------+
   | Parameter             | Mandatory             | Description                  |
   +=======================+=======================+==============================+
   | project_id            | Yes                   | **Definition**               |
   |                       |                       |                              |
   |                       |                       | Specifies the project ID.    |
   |                       |                       |                              |
   |                       |                       | **Constraints**              |
   |                       |                       |                              |
   |                       |                       | N/A                          |
   |                       |                       |                              |
   |                       |                       | **Range**                    |
   |                       |                       |                              |
   |                       |                       | N/A                          |
   |                       |                       |                              |
   |                       |                       | **Default Value**            |
   |                       |                       |                              |
   |                       |                       | N/A                          |
   +-----------------------+-----------------------+------------------------------+
   | server_group_id       | Yes                   | **Definition**               |
   |                       |                       |                              |
   |                       |                       | Specifies an ECS group UUID. |
   |                       |                       |                              |
   |                       |                       | **Constraints**              |
   |                       |                       |                              |
   |                       |                       | N/A                          |
   |                       |                       |                              |
   |                       |                       | **Range**                    |
   |                       |                       |                              |
   |                       |                       | N/A                          |
   |                       |                       |                              |
   |                       |                       | **Default Value**            |
   |                       |                       |                              |
   |                       |                       | N/A                          |
   +-----------------------+-----------------------+------------------------------+

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0175597847__table4683214181116>` describes the response parameters.

.. _en-us_topic_0175597847__table4683214181116:

.. table:: **Table 2** Response parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================+
   | server_group          | Object                | **Definition**                                                                                                                      |
   |                       |                       |                                                                                                                                     |
   |                       |                       | Specifies the ECS group information. For details, see :ref:`Table 3 <en-us_topic_0175597847__en-us_topic_0057973159_table5520021>`. |
   |                       |                       |                                                                                                                                     |
   |                       |                       | **Range**                                                                                                                           |
   |                       |                       |                                                                                                                                     |
   |                       |                       | N/A                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0175597847__en-us_topic_0057973159_table5520021:

.. table:: **Table 3** **server_group** parameters

   +-----------------------+-----------------------+-------------------------------------------------------+
   | Parameter             | Type                  | Description                                           |
   +=======================+=======================+=======================================================+
   | id                    | String                | **Definition**                                        |
   |                       |                       |                                                       |
   |                       |                       | Specifies an ECS group UUID.                          |
   |                       |                       |                                                       |
   |                       |                       | **Range**                                             |
   |                       |                       |                                                       |
   |                       |                       | N/A                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------+
   | name                  | String                | **Definition**                                        |
   |                       |                       |                                                       |
   |                       |                       | Specifies the ECS group name.                         |
   |                       |                       |                                                       |
   |                       |                       | **Range**                                             |
   |                       |                       |                                                       |
   |                       |                       | N/A                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------+
   | policies              | Array of strings      | **Definition**                                        |
   |                       |                       |                                                       |
   |                       |                       | Specifies the policies associated with the ECS group. |
   |                       |                       |                                                       |
   |                       |                       | **Range**                                             |
   |                       |                       |                                                       |
   |                       |                       | N/A                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------+
   | members               | Array of strings      | **Definition**                                        |
   |                       |                       |                                                       |
   |                       |                       | Specifies the ECS contained in an ECS group.          |
   |                       |                       |                                                       |
   |                       |                       | **Range**                                             |
   |                       |                       |                                                       |
   |                       |                       | N/A                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------+
   | metadata              | Object                | **Definition**                                        |
   |                       |                       |                                                       |
   |                       |                       | Specifies the ECS group metadata.                     |
   |                       |                       |                                                       |
   |                       |                       | **Range**                                             |
   |                       |                       |                                                       |
   |                       |                       | N/A                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------+

Example Request
---------------

Query details about the specified ECS group.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/cloudservers/os-server-groups/{server_group_id}

Example Response
----------------

.. code-block::

   {
       "server_group": {
           "id": "5bbcc3c4-1da2-4437-a48a-66f15b1b13f9",
           "name": "test",
           "policies": ["anti-affinity"],
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
