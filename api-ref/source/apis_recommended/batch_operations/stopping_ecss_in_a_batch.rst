:original_name: en-us_topic_0020212651.html

.. _en-us_topic_0020212651:

Stopping ECSs in a Batch
========================

Function
--------

This API is used to stop ECSs in a batch based on the specified ECS ID list. A maximum of 1000 ECSs can be stopped at a time.

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

See :ref:`Responses (Task) <en-us_topic_0022067714>`.

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
