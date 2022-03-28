Deleting Tags from an ECS in a Batch
====================================

Function
--------

-  This API is used to delete tags from a specified ECS in a batch.
-  The Tag Management Service (TMS) uses this API to batch manage the tags of an ECS.

.. note::

   -  This API is idempotent. When you delete a tag but the tag does not exist, a successful result is returned.

Constraints
-----------

An ECS allows a maximum of 10 tags.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/tags/action

`Table 1 <#enustopic0167811964table1320245602220>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0167811964table1320245602220:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0167811964table105531424192318>`__ describes the request parameters.



.. _ENUSTOPIC0167811964table105531424192318:

.. table:: **Table 2** Request parameters

   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                                                |
   +===========+===========+==================+============================================================================================================================+
   | tags      | Yes       | Array of objects | Specifies tags. For details, see `Table 3 <#enustopic0167811964table6449181462417>`__.                                     |
   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------+
   | action    | Yes       | String           | Specifies the operation. (Only lowercase letters are supported.) For example, **delete** indicates the deletion operation. |
   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0167811964table6449181462417:

.. table:: **Table 3** **tags** field description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                               |
   +=================+=================+=================+===========================================================================+
   | key             | Yes             | String          | Specifies the tag key.                                                    |
   |                 |                 |                 |                                                                           |
   |                 |                 |                 | It contains a maximum of 127 Unicode characters and cannot be left blank. |
   |                 |                 |                 |                                                                           |
   |                 |                 |                 | The tag key of an ECS must be unique.                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------+
   | value           | No              | String          | Specifies the tag value.                                                  |
   |                 |                 |                 |                                                                           |
   |                 |                 |                 | It contains a maximum of 255 Unicode characters and can be left blank.    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------+

Response
--------

None

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/tags/action

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


