.. _en-us_topic_0167811967:

Querying Tags of an ECS
=======================

Function
--------

-  This API is used to query the tags of a specified ECS.
-  The Tag Management Service (TMS) uses this API to query all tags of an ECS.

URI
---

GET /v1/{project_id}/cloudservers/{server_id}/tags

:ref:`Table 1 <en-us_topic_0167811967__table194262014152810>` describes the parameters in the URI.

.. _en-us_topic_0167811967__table194262014152810:

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

:ref:`Table 2 <en-us_topic_0167811967__table1972264711286>` describes the response parameters.

.. _en-us_topic_0167811967__table1972264711286:

.. table:: **Table 2** Response parameters

   +-----------+------------------+-----------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                   |
   +===========+==================+===============================================================================================+
   | tags      | Array of objects | Specifies tags. For details, see :ref:`Table 3 <en-us_topic_0167811967__table1148911211295>`. |
   +-----------+------------------+-----------------------------------------------------------------------------------------------+

.. _en-us_topic_0167811967__table1148911211295:

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
