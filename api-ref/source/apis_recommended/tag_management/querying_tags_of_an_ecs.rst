Querying Tags of an ECS
=======================

Function
--------

-  This API is used to query the tags of a specified ECS.
-  The Tag Management Service (TMS) uses this API to query all tags of an ECS.

URI
---

GET /v1/{project_id}/cloudservers/{server_id}/tags

`Table 1 <#enustopic0167811967table194262014152810>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0167811967table194262014152810:

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

`Table 2 <#enustopic0167811967table1972264711286>`__ describes the response parameters.



.. _ENUSTOPIC0167811967table1972264711286:

.. table:: **Table 2** Response parameters

   +-----------+------------------+----------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                            |
   +===========+==================+========================================================================================+
   | tags      | Array of objects | Specifies tags. For details, see `Table 3 <#enustopic0167811967table1148911211295>`__. |
   +-----------+------------------+----------------------------------------------------------------------------------------+



.. _ENUSTOPIC0167811967table1148911211295:

.. table:: **Table 3** **tags** field description

   ========= ====== ========================
   Parameter Type   Description
   ========= ====== ========================
   key       String Specifies the tag key.
   value     String Specifies the tag value.
   ========= ====== ========================

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/tags

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


