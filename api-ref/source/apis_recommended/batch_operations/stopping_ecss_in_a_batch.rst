:original_name: en-us_topic_0020212651.html

.. _en-us_topic_0020212651:

Stopping ECSs in a Batch
========================

Function
--------

This API is used to stop ECSs in a batch based on specified ECS IDs. A maximum of 1,000 ECSs can be stopped in one minute.

This API is an asynchronous API. After the batch stop request is successfully delivered, a job ID is returned. This does not mean the batch stop is complete. You need to call the API by referring to :ref:`Querying Job Execution Status <en-us_topic_0022225398>` to query the job status. The SUCCESS status indicates that the batch stop is successful.

URI
---

POST /v1/{project_id}/cloudservers/action

:ref:`Table 1 <en-us_topic_0020212651__table66418347>` describes the parameters in the URI.

.. _en-us_topic_0020212651__table66418347:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                             |
   +===========+===========+========+=========================================================================================================================+
   | os-stop   | Yes       | Object | Specifies the operation to stop the ECS. For details, see :ref:`Table 3 <en-us_topic_0020212651__table51053190162024>`. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212651__table51053190162024:

.. table:: **Table 3** **os-stop** field description

   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                 |
   +=================+=================+==================+=============================================================================================+
   | servers         | Yes             | Array of objects | Specifies ECS IDs. For details, see :ref:`Table 4 <en-us_topic_0020212651__table48932206>`. |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------+
   | type            | No              | String           | Specifies an ECS stop type. The default value is **SOFT**.                                  |
   |                 |                 |                  |                                                                                             |
   |                 |                 |                  | **SOFT**: normal ECS stop (default)                                                         |
   |                 |                 |                  |                                                                                             |
   |                 |                 |                  | **HARD**: forcible ECS stop                                                                 |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212651__table48932206:

.. table:: **Table 4** **servers** field description

   ========= ========= ====== =====================
   Parameter Mandatory Type   Description
   ========= ========= ====== =====================
   id        Yes       String Specifies the ECS ID.
   ========= ========= ====== =====================

Response
--------

:ref:`Table 5 <en-us_topic_0020212651__table2824153181913>` describes the response parameters.

.. _en-us_topic_0020212651__table2824153181913:

.. table:: **Table 5** Response parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                 |
   +=======================+=======================+=============================================================================================================================================================================================================================================================+
   | job_id                | String                | **Definition**                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                             |
   |                       |                       | Specifies the job ID returned after a job is delivered. The job ID can be used to query the job execution progress. For details about how to query the job execution status based on **job_id**, see :ref:`Job Status Management <en-us_topic_0022225397>`. |
   |                       |                       |                                                                                                                                                                                                                                                             |
   |                       |                       | **Range**                                                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                             |
   |                       |                       | N/A                                                                                                                                                                                                                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

For details about abnormal responses, see :ref:`Responses (Jobs) <en-us_topic_0022067714>`.

Example Request
---------------

Batch stop ECSs whose IDs are **616fb98f-46ca-475e-917e-2563e5a8cd19** and **726fb98f-46ca-475e-917e-2563e5a8cd20** with the request parameter set to **os-stop**.

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/cloudservers/action

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
