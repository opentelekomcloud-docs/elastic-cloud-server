Querying ECS Groups
===================

Function
--------

This API is used to query ECS groups.

URI
---

GET /v1/{project_id}/cloudservers/os-server-groups?limit={limit}&marker={marker}

`Table 1 <#enustopic0175597846table566015531780>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0175597846table566015531780:

.. table:: **Table 1** Path parameters

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================



.. _ENUSTOPIC0175597846enustopic0057973158table7928881:

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

`Table 3 <#enustopic0175597846table696924014912>`__ describes the response parameters. 

.. _ENUSTOPIC0175597846table696924014912:

.. table:: **Table 3** Response parameters

   +---------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type             | Description                                                                                                                                                                  |
   +===============+==================+==============================================================================================================================================================================+
   | server_groups | Array of objects | Specifies ECS groups. For details, see `Table 4 <#enustopic0175597846enustopic0057973158table47937085>`__.                                                                   |
   +---------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | page_info     | Object           | If the pagination function is enabled, the UUID of the last ECS group on the current page is returned. For details, see `Table 5 <#enustopic0175597846table139805663519>`__. |
   +---------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0175597846enustopic0057973158table47937085:

.. table:: **Table 4** **server_groups** parameter information

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                          |
   +=======================+=======================+======================================================================================================================================================================================================================+
   | id                    | String                | Specifies the ECS group UUID.                                                                                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the ECS group name.                                                                                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | members               | Array of strings      | Specifies the ECSs contained in an ECS group.                                                                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata              | Object                | Specifies the ECS group metadata.                                                                                                                                                                                    |
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



.. _ENUSTOPIC0175597846table139805663519:

.. table:: **Table 5** **page_info** field description

   =========== ====== ============================
   Parameter   Type   Description
   =========== ====== ============================
   next_marker String Specifies an ECS group UUID.
   =========== ====== ============================

Example Request
---------------

.. code-block::

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

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


