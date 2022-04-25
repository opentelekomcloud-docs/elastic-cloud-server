:original_name: en-us_topic_0000001207783562.html

.. _en-us_topic_0000001207783562:

Querying Tags of an ECS (Discarded)
===================================

Function
--------

-  This API is used to query the tags of a specified ECS.
-  The Tag Management Service (TMS) uses this API to query all tags of an ECS.

.. note::

   This API has been discarded. Use the API described in :ref:`Querying Tags of an ECS <en-us_topic_0167811967>`.

URI
---

GET /v1/{project_id}/servers/{server_id}/tags

:ref:`Table 1 <en-us_topic_0000001207783562__table431622145919>` lists the parameters.

.. _en-us_topic_0000001207783562__table431622145919:

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

:ref:`Table 2 <en-us_topic_0000001207783562__table725495518449>` describes the response parameter.

.. _en-us_topic_0000001207783562__table725495518449:

.. table:: **Table 2** Response parameter

   ========= ================ ===============
   Parameter Type             Description
   ========= ================ ===============
   tags      Array of objects Specifies tags.
   ========= ================ ===============

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
