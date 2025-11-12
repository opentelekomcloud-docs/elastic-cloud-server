:original_name: en-us_topic_0065817689.html

.. _en-us_topic_0065817689:

Obtaining ECS Management Console Logs
=====================================

Function
--------

This API is used to obtain ECS management console logs.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

:ref:`Table 1 <en-us_topic_0065817689__table10917102617186>` describes the parameters in the URI.

.. _en-us_topic_0065817689__table10917102617186:

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

:ref:`Table 2 <en-us_topic_0065817689__table168291156125012>` describes the request parameters.

.. _en-us_topic_0065817689__table168291156125012:

.. table:: **Table 2** Request parameters

   +---------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory | Type   | Description                                                                                                                               |
   +=====================+===========+========+===========================================================================================================================================+
   | os-getConsoleOutput | Yes       | Object | Obtains ECS management console logs. For details, see :ref:`Table 3 <en-us_topic_0065817689__en-us_topic_0062473752_table1919246111545>`. |
   +---------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817689__en-us_topic_0062473752_table1919246111545:

.. table:: **Table 3** os-getConsoleOutput parameter description

   +-----------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                                         |
   +===========+===========+=========+=====================================================================================================================================+
   | length    | Yes       | Integer | Specifies the number of request log rows. The value is greater than or equal to -1, which indicates that the output is not limited. |
   +-----------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 4 <en-us_topic_0065817689__table18130192135217>` describes the response parameter.

.. _en-us_topic_0065817689__table18130192135217:

.. table:: **Table 4** Response parameters

   ========= ====== =======================
   Parameter Type   Description
   ========= ====== =======================
   output    String ECS console log results
   ========= ====== =======================

Example Request
---------------

Obtain console logs of a specified ECS.

.. code-block:: text

   POST https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/servers/47e9be4e-a7b9-471f-92d9-ffc83814e07a/action
   POST https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/servers/47e9be4e-a7b9-471f-92d9-ffc83814e07a/action

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
