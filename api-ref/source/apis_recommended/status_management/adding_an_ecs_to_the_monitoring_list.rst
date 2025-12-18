:original_name: en-us_topic_0000001635605869.html

.. _en-us_topic_0000001635605869:

Adding an ECS to the Monitoring List
====================================

Function
--------

This API is used to add an ECS to the monitoring list.

Ceilometer periodically collects monitoring data on the ECSs added to the monitoring list and reports the data to Cloud Eye. The data includes the platform version, CPU, memory, NICs, disks, and hardware version.

URI
---

POST /v1.0/servers/{server_id}/action

:ref:`Table 1 <en-us_topic_0000001635605869__en-us_topic_0081529857_table3713317418952>` describes the parameters in the URI.

.. _en-us_topic_0000001635605869__en-us_topic_0081529857_table3713317418952:

.. table:: **Table 1** Parameter description

   ========= ========= =====================
   Parameter Mandatory Description
   ========= ========= =====================
   server_id Yes       Specifies the ECS ID.
   ========= ========= =====================

Request
-------

:ref:`Table 2 <en-us_topic_0000001635605869__en-us_topic_0081529857_table20892986181041>` describes the request parameters.

.. _en-us_topic_0000001635605869__en-us_topic_0081529857_table20892986181041:

.. table:: **Table 2** Request parameters

   ============== ========= ====== ===================================
   Parameter      Mandatory Type   Description
   ============== ========= ====== ===================================
   monitorMetrics Yes       String Adds an ECS to the monitoring list.
   ============== ========= ====== ===================================

Response
--------

None

Example Request
---------------

Add a specified ECS to the monitoring list.

.. code-block:: text

   POST https://{endpoint}/v1.0/servers/{server_id}/action

   {
       "monitorMetrics": ""
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
