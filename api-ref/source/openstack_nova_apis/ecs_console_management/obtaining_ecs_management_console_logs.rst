Obtaining ECS Management Console Logs
=====================================

Function
--------

This API is used to obtain ECS management console logs.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

`Table 1 <#enustopic0065817689table10917102617186>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817689table10917102617186:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Constraints
-----------

This API will be discarded since a version later than microversion 2.5. When using this API, set the microversion to 2.5 or earlier.

Request
-------

`Table 2 <#enustopic0065817689table168291156125012>`__ describes the request parameters.



.. _ENUSTOPIC0065817689table168291156125012:

.. table:: **Table 2** Request parameters

   +---------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory | Type   | Description                                                                                                                    |
   +=====================+===========+========+================================================================================================================================+
   | os-getConsoleOutput | Yes       | Object | Obtains ECS management console logs. For details, see `Table 3 <#enustopic0065817689enustopic0062473752table1919246111545>`__. |
   +---------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817689enustopic0062473752table1919246111545:

.. table:: **Table 3** os-getConsoleOutput parameter description

   +-----------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                                         |
   +===========+===========+=========+=====================================================================================================================================+
   | length    | Yes       | Integer | Specifies the number of request log rows. The value is greater than or equal to -1, which indicates that the output is not limited. |
   +-----------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

`Table 4 <#enustopic0065817689table18130192135217>`__ describes the response parameter.



.. _ENUSTOPIC0065817689table18130192135217:

.. table:: **Table 4** Response parameter

   ========= ====== ===============================
   Parameter Type   Description
   ========= ====== ===============================
   output    String Specifies the ECS console logs.
   ========= ====== ===============================

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/servers/47e9be4e-a7b9-471f-92d9-ffc83814e07a/action
   POST https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/servers/47e9be4e-a7b9-471f-92d9-ffc83814e07a/action

.. code-block::

   {
      "os-getConsoleOutput" : {
           "length" : "50"
       }
   }

Example Response
----------------

.. code-block::

   {
       "output": "FAKE CONSOLEOUTPUT\nANOTHER\nLAST LINE"
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


