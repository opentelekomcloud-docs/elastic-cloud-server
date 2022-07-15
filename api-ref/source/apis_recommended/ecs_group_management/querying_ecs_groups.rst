:original_name: en-us_topic_0175597846.html

.. _en-us_topic_0175597846:

Querying ECS Groups
===================

Function
--------

This API is used to query ECS groups.

URI
---

GET /v1/{project_id}/cloudservers/os-server-groups?limit={limit}&marker={marker}

:ref:`Table 1 <en-us_topic_0175597846__table566015531780>` describes the parameters in the URI.

.. _en-us_topic_0175597846__table566015531780:

.. table:: **Table 1** Path parameters

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                |
   +=================+=================+=================+============================================================================================================================+
   | limit           | No              | Integer         | Specifies the upper limit on the number of returned server groups. The maximum value is 1000.                              |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Specifies the marker that points to the ECS group. The query starts from the next piece of data indexed by this parameter. |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | Parameters marker and limit must be used together.                                                                         |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 3 <en-us_topic_0175597846__table696924014912>` describes the response parameters.

.. _en-us_topic_0175597846__table696924014912:

.. table:: **Table 3** Response parameters

   +---------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type             | Description                                                                                                                                                                         |
   +===============+==================+=====================================================================================================================================================================================+
   | server_groups | Array of objects | Specifies ECS groups. For details, see :ref:`Table 4 <en-us_topic_0175597846__en-us_topic_0057973158_table47937085>`.                                                               |
   +---------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | page_info     | Object           | If the pagination function is enabled, the UUID of the last ECS group on the current page is returned. For details, see :ref:`Table 5 <en-us_topic_0175597846__table139805663519>`. |
   +---------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0175597846__en-us_topic_0057973158_table47937085:

.. table:: **Table 4** **server_groups** parameter information

   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                   |
   +=======================+=======================+===============================================================================+
   | id                    | String                | Specifies the ECS group UUID.                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | name                  | String                | Specifies the ECS group name.                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | members               | Array of strings      | Specifies the ECSs contained in an ECS group.                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | metadata              | Object                | Specifies the ECS group metadata.                                             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | policies              | Array of strings      | Specifies the policies associated with the ECS group. Options:                |
   |                       |                       |                                                                               |
   |                       |                       | -  **anti-affinity**: ECSs in this group must be deployed on different hosts. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+

.. _en-us_topic_0175597846__table139805663519:

.. table:: **Table 5** **page_info** field description

   =========== ====== ============================
   Parameter   Type   Description
   =========== ====== ============================
   next_marker String Specifies an ECS group UUID.
   =========== ====== ============================

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/cloudservers/os-server-groups

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
               "metadata": {}
           }
       ],
       "page_info": {
           "next_marker": "616fb98f-46ca-475e-917e-2563e5a8cd19"
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
