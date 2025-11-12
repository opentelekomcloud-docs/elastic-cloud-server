:original_name: en-us_topic_0020212649.html

.. _en-us_topic_0020212649:

Restarting ECSs in a Batch
==========================

Function
--------

This API is used to restart ECSs in a batch based on specified ECS IDs. A maximum of 1,000 ECSs can be restarted in one minute.

This API is an asynchronous API. After the batch restart request is successfully delivered, a job ID is returned. This does not mean the batch restart is complete. You need to call the API by referring to :ref:`Querying Job Execution Status <en-us_topic_0022225398>` to query the job status. The SUCCESS status indicates that the batch restart is successful.

URI
---

POST /v1/{project_id}/cloudservers/action

:ref:`Table 1 <en-us_topic_0020212649__table33008913>` describes the parameters in the URI.

.. _en-us_topic_0020212649__table33008913:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0020212649__table54749715>` describes the request parameters.

.. _en-us_topic_0020212649__table54749715:

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                |
   +===========+===========+========+============================================================================================================================+
   | reboot    | Yes       | Object | Specifies the operation to restart the ECS. For details, see :ref:`Table 3 <en-us_topic_0020212649__table64591731162222>`. |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212649__table64591731162222:

.. table:: **Table 3** **reboot** field description

   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                       |
   +=================+=================+==================+===================================================================================================+
   | type            | Yes             | String           | Specifies the type of the restart operation.                                                      |
   |                 |                 |                  |                                                                                                   |
   |                 |                 |                  | -  **SOFT**: normal restart                                                                       |
   |                 |                 |                  | -  **HARD**: forcible restart (hard restart)                                                      |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------+
   | servers         | Yes             | Array of objects | Specifies ECS IDs. For details, see :ref:`Table 4 <en-us_topic_0020212649__table26785545162223>`. |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212649__table26785545162223:

.. table:: **Table 4** **servers** field description

   ========= ========= ====== =====================
   Parameter Mandatory Type   Description
   ========= ========= ====== =====================
   id        Yes       String Specifies the ECS ID.
   ========= ========= ====== =====================

Response
--------

See :ref:`Responses (Jobs) <en-us_topic_0022067714>`.

Example Request
---------------

Batch restart ECSs whose IDs are **616fb98f-46ca-475e-917e-2563e5a8cd19** and **726fb98f-46ca-475e-917e-2563e5a8cd20** with the request parameter set to **reboot**.

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/cloudservers/action

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

.. code-block::

   {
       "job_id": "ff80808288d41e1b018990260955686a"
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
