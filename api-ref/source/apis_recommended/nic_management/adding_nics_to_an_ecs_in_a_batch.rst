Adding NICs to an ECS in a Batch
================================

Function
--------

This API is used to add one or multiple NICs to an ECS.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/nics

`Table 1 <#enustopic0020212663table54800025>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212663table54800025:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0020212663table23831236>`__ describes the request parameters. 

.. _ENUSTOPIC0020212663table23831236:

.. table:: **Table 2** Request parameters

   +-----------+-----------+------------------+---------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                       |
   +===========+===========+==================+===================================================================================================+
   | nics      | Yes       | Array of objects | Specifies the NICs to be added. For details, see `Table 3 <#enustopic0020212663table58396974>`__. |
   +-----------+-----------+------------------+---------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212663table58396974:

.. table:: **Table 3** **nics** field description

   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                               |
   +=================+=================+==================+===========================================================================================================+
   | subnet_id       | Yes             | String           | Specifies the information about the NICs to be added to an ECS.                                           |
   |                 |                 |                  |                                                                                                           |
   |                 |                 |                  | The value must be the ID of a created network in UUID format.                                             |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------+
   | security_groups | No              | Array of objects | Specifies the security groups for NICs. For details, see `Table 4 <#enustopic0020212663table16100147>`__. |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------+
   | ip_address      | No              | String           | Specifies the IP address. If this parameter is unavailable, the IP address is automatically assigned.     |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212663table16100147:

.. table:: **Table 4** **security_groups** field description

   ========= ========= ====== =======================================
   Parameter Mandatory Type   Description
   ========= ========= ====== =======================================
   id        Yes       String Specifies the ID of the security group.
   ========= ========= ====== =======================================

Response
--------

See `Responses (Task) <../../common_parameters/task_request_result/responses_task.html>`__.

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/nics

.. code-block::

   {
       "nics": [
           {
               "subnet_id": "d32019d3-bc6e-4319-9c1d-6722fc136a23", 
               "security_groups": [
                   {
                       "id": "f0ac4394-7e4a-4409-9701-ba8be283dbc3"
                   }
               ]
           }
       ]
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


