Stopping ECSs in a Batch
========================

Function
--------

This API is used to stop ECSs in a batch based on the specified ECS ID list. A maximum of 1000 ECSs can be stopped at a time.

URI
---

POST /v1/{project_id}/cloudservers/action

`Table 1 <#enustopic0020212651table66418347>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212651table66418347:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------



.. _ENUSTOPIC0020212651table12156768:

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                      |
   +===========+===========+========+==================================================================================================================+
   | os-stop   | Yes       | Object | Specifies the operation to stop the ECS. For details, see `Table 3 <#enustopic0020212651table51053190162024>`__. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212651table51053190162024:

.. table:: **Table 3** **os-stop** field description

   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                          |
   +=================+=================+==================+======================================================================================+
   | servers         | Yes             | Array of objects | Specifies ECS IDs. For details, see `Table 4 <#enustopic0020212651table48932206>`__. |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------+
   | type            | No              | String           | Specifies an ECS stop type. The default value is **SOFT**.                           |
   |                 |                 |                  |                                                                                      |
   |                 |                 |                  | **SOFT**: normal ECS stop (default)                                                  |
   |                 |                 |                  |                                                                                      |
   |                 |                 |                  | **HARD**: forcible ECS stop                                                          |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212651table48932206:

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

In the request parameters, the request for stopping the ECS must be issued with field **os-stop**, as shown in the example request.

.. code-block::

   POST https://{endpoint}/v1/{project_id}/cloudservers/action

.. code-block::

   {
       "os-stop": {
           "type":"HARD",
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


