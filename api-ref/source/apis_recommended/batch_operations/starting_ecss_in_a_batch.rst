Starting ECSs in a Batch
========================

Function
--------

This API is used to start ECSs in a batch based on specified ECS IDs. A maximum of 1000 ECSs can be started at a time.

URI
---

POST /v1/{project_id}/cloudservers/action

`Table 1 <#enustopic0020212207table58892473>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212207table58892473:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------



.. _ENUSTOPIC0020212207table66572856:

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                       |
   +===========+===========+========+===================================================================================================================+
   | os-start  | Yes       | Object | Specifies the operation to start the ECS. For details, see `Table 3 <#enustopic0020212207table52132698163051>`__. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212207table52132698163051:

.. table:: **Table 3** **os-start** field description

   +-----------+-----------+------------------+--------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                          |
   +===========+===========+==================+======================================================================================+
   | servers   | Yes       | Array of objects | Specifies ECS IDs. For details, see `Table 4 <#enustopic0020212207table23507505>`__. |
   +-----------+-----------+------------------+--------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212207table23507505:

.. table:: **Table 4** **servers** field description

   ========= ========= ====== =====================
   Parameter Mandatory Type   Description
   ========= ========= ====== =====================
   id        Yes       String Specifies the ECS ID.
   ========= ========= ====== =====================

Response
--------

See `Responses (Task) <../../common_parameters/task_request_result/responses_task.html>`__.

Example Request
---------------

In the request, the parameters to start ECSs must be sent with field **os-start**. For details, see the example request.

.. code-block::

   POST https://{endpoint}/v1/{project_id}/cloudservers/action

.. code-block::

   {
       "os-start": {
           "servers": [
               {
                   "id": "616fb98f-46ca-475e-917e-2563e5a8cd19"
               },
               {
                   "id": "726fb98f-46ca-475e-917e-2563e5a8cd20"
               }
           ]
       }
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


