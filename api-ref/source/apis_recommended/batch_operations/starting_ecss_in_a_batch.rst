:original_name: en-us_topic_0020212207.html

.. _en-us_topic_0020212207:

Starting ECSs in a Batch
========================

Function
--------

This API is used to start ECSs in a batch based on specified ECS IDs. A maximum of 1,000 ECSs can be started in one minute.

This API is an asynchronous API. After the batch start request is successfully delivered, a job ID is returned. This does not mean the batch start is complete. You need to call the API by referring to :ref:`Querying Job Execution Status <en-us_topic_0022225398>` to query the job status. The SUCCESS status indicates that the batch start is successful.

URI
---

POST /v1/{project_id}/cloudservers/action

:ref:`Table 1 <en-us_topic_0020212207__table58892473>` describes the parameters in the URI.

.. _en-us_topic_0020212207__table58892473:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                              |
   +===========+===========+========+==========================================================================================================================+
   | os-start  | Yes       | Object | Specifies the operation to start the ECS. For details, see :ref:`Table 3 <en-us_topic_0020212207__table52132698163051>`. |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212207__table52132698163051:

.. table:: **Table 3** **os-start** field description

   +-----------+-----------+------------------+---------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                 |
   +===========+===========+==================+=============================================================================================+
   | servers   | Yes       | Array of objects | Specifies ECS IDs. For details, see :ref:`Table 4 <en-us_topic_0020212207__table23507505>`. |
   +-----------+-----------+------------------+---------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212207__table23507505:

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

Batch start ECSs whose IDs are **616fb98f-46ca-475e-917e-2563e5a8cd19** and **726fb98f-46ca-475e-917e-2563e5a8cd20** with the request parameter set to **os-start**.

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/cloudservers/action

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

.. code-block::

   {
       "job_id": "ff808082889bd9690189061140c235fe"
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
