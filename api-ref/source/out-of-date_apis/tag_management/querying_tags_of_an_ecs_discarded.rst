Querying Tags of an ECS (Discarded)
===================================

Function
--------

-  This API is used to query the tags of a specified ECS.
-  The Tag Management Service (TMS) uses this API to query all tags of an ECS.

.. note::

   This API has been discarded. Use the API described in `Querying Tags of an ECS <../../apis_recommended/tag_management/querying_tags_of_an_ecs.html>`__.

URI
---

GET /v1/{project_id}/servers/{server_id}/tags

`Table 1 <#enustopic0000001207783562table431622145919>`__ lists the parameters. 

.. _ENUSTOPIC0000001207783562table431622145919:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

None

Response
--------

`Table 2 <#enustopic0000001207783562table725495518449>`__ describes the response parameter.



.. _ENUSTOPIC0000001207783562table725495518449:

.. table:: **Table 2** Response parameter

   ========= ================ ===============
   Parameter Type             Description
   ========= ================ ===============
   tags      Array of objects Specifies tags.
   ========= ================ ===============



.. _ENUSTOPIC0000001207783562table109271241135919:

.. table:: **Table 3** **resource_tag** field description

   ========= ====== ========================
   Parameter Type   Description
   ========= ====== ========================
   key       String Specifies the tag key.
   value     String Specifies the tag value.
   ========= ====== ========================

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v1/{project_id}/servers/{server_id}/tags

Example Response
----------------

.. code-block::

   {
          "tags": [
           {
               "key": "key1",
               "value": "value1"
           },
           {
               "key": "key2",
               "value": "value3"
           }
       ]
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


