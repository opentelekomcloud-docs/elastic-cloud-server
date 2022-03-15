Deleting Tags from an ECS in a Batch (Discarded)
================================================

Function
--------

-  This API is used to delete tags from a specified ECS in a batch.
-  The Tag Management Service (TMS) uses this API to batch manage the tags of an ECS.
-  This API is idempotent. When you delete a tag but the tag does not exist, a successful result is returned.

.. note::

   This API has been discarded. Use the API described in `Deleting Tags from an ECS in a Batch <../../apis_recommended/tag_management/deleting_tags_from_an_ecs_in_a_batch.html>`__.

Constraints
-----------

An ECS allows a maximum of 10 tags.

URI
---

POST /v1/{project_id}/servers/{server_id}/tags/action

`Table 1 <#enustopic0000001252263549enustopic0096282701table19484740133714>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0000001252263549enustopic0096282701table19484740133714:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0000001252263549table787034194212>`__ describes the request parameters.



.. _ENUSTOPIC0000001252263549table787034194212:

.. table:: **Table 2** Request parameters

   +-----------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                                               |
   +===========+===========+==================+===========================================================================================================================+
   | tags      | Yes       | Array of objects | Specifies tags.                                                                                                           |
   +-----------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | action    | Yes       | String           | Specifies the operation (only lowercase letters are supported). For example, **delete** indicates the deletion operation. |
   +-----------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0000001252263549table3147055191316:

.. table:: **Table 3** **resource_tag** field description

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                      |
   +=================+=================+=================+==================================================================================+
   | key             | Yes             | String          | Specifies the tag key.                                                           |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 | It contains a maximum of 127 Unicode characters and cannot be left blank.        |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 | The tag key of an ECS must be unique.                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------+
   | value           | No              | String          | Specifies the tag value.                                                         |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 | The value can contain a maximum of 255 Unicode characters and can be left blank. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------+

Response
--------

None

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v1/{project_id}/servers/{server_id}/tags/action

.. code-block::

   {
       "action": "delete",
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

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


