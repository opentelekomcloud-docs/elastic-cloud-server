Adding an ECS to the Monitoring List
====================================

Function
--------

This API is used to add an ECS to the monitoring list.

Ceilometer periodically collects monitoring data on the ECSs added to the monitoring list and reports the data to Cloud Eye. The data includes the platform version, CPU, memory, NICs, disks, and hardware version. For example, the plug-in of an SAP ECS periodically obtains monitoring data from Cloud Eye and reports the data to SAP in reports.

URI
---

POST /v1.0/servers/{server_id}/action

`Table 1 <#enustopic0081529857table3713317418952>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0081529857table3713317418952:

.. table:: **Table 1** Parameter description

   ========= ========= =====================
   Parameter Mandatory Description
   ========= ========= =====================
   server_id Yes       Specifies the ECS ID.
   ========= ========= =====================

Request
-------

`Table 2 <#enustopic0081529857table20892986181041>`__ describes the request parameters. 

.. _ENUSTOPIC0081529857table20892986181041:

.. table:: **Table 2** Request parameters

   ============== ========= ==== ==============================
   Parameter      Mandatory Type Description
   ============== ========= ==== ==============================
   monitorMetrics Yes       Null Enables monitoring on the ECS.
   ============== ========= ==== ==============================

Response
--------

None

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v1.0/servers/{server_id}/action

.. code-block::

   {  
      "monitorMetrics" : null 
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


