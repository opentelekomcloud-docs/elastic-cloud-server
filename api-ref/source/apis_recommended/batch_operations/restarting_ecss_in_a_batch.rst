Restarting ECSs in a Batch
==========================

Function
--------

This API is used to restart ECSs in a batch based on specified ECS IDs. A maximum of 1000 ECSs can be restarted at a time.

URI
---

POST /v1/{project_id}/cloudservers/action

`Table 1 <#enustopic0020212649table33008913>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212649table33008913:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0020212649table54749715>`__ describes the request parameters. 

.. _ENUSTOPIC0020212649table54749715:

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                         |
   +===========+===========+========+=====================================================================================================================+
   | reboot    | Yes       | Object | Specifies the operation to restart the ECS. For details, see `Table 3 <#enustopic0020212649table64591731162222>`__. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212649table64591731162222:

.. table:: **Table 3** **reboot** field description

   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                |
   +=================+=================+==================+============================================================================================+
   | type            | Yes             | String           | Specifies the type of the restart operation.                                               |
   |                 |                 |                  |                                                                                            |
   |                 |                 |                  | -  **SOFT**: soft restart                                                                  |
   |                 |                 |                  | -  **HARD**: forcible restart (hard restart)                                               |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------+
   | servers         | Yes             | Array of objects | Specifies ECS IDs. For details, see `Table 4 <#enustopic0020212649table26785545162223>`__. |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212649table26785545162223:

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

In the request, the parameters to restart ECSs must be sent with field **reboot**. For details, see the example request.

.. code-block::

   POST https://{endpoint}/v1/{project_id}/cloudservers/action

.. code-block::

   {
       "reboot": {
           "type":"SOFT",
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


