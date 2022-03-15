Adding a NIC to an ECS
======================

Function
--------

This API is used to add a NIC to an ECS.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/os-interface

POST /v2/{project_id}/servers/{server_id}/os-interface

`Table 1 <#enustopic0020212664table55925239>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212664table55925239:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0020212664table21989419>`__ describes the request parameters. 

.. _ENUSTOPIC0020212664table21989419:

.. table:: **Table 2** Request parameters

   +---------------------+-----------+--------+---------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory | Type   | Description                                                                                       |
   +=====================+===========+========+===================================================================================================+
   | interfaceAttachment | Yes       | Object | Specifies the NICs to be added. For details, see `Table 3 <#enustopic0020212664table44975500>`__. |
   +---------------------+-----------+--------+---------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212664table44975500:

.. table:: **Table 3** **interfaceAttachment** field description

   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                       |
   +=================+=================+==================+===================================================================================================================================================================================+
   | port_id         | No              | String           | Specifies the port ID.                                                                                                                                                            |
   |                 |                 |                  |                                                                                                                                                                                   |
   |                 |                 |                  | Either **port_id** or **net_id** is used each time.                                                                                                                               |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | net_id          | No              | String           | Specifies the network ID.                                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                   |
   |                 |                 |                  | Either **port_id** or **net_id** is used each time.                                                                                                                               |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fixed_ips       | No              | Array of objects | Specifies a private IP address.                                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                                                                   |
   |                 |                 |                  | This parameter cannot be specified when **port_id** is used.                                                                                                                      |
   |                 |                 |                  |                                                                                                                                                                                   |
   |                 |                 |                  | This parameter must be used with **net_id**.                                                                                                                                      |
   |                 |                 |                  |                                                                                                                                                                                   |
   |                 |                 |                  | Only the first element in the list is valid. If two or more elements are used, an error will be reported. For details, see `Table 4 <#enustopic0020212664table26224215175117>`__. |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212664table26224215175117:

.. table:: **Table 4** **fixed_ips** field description

   ========== ========= ====== =========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================
   ip_address No        String Specifies the IP address.
   ========== ========= ====== =========================

Response
--------

`Table 5 <#enustopic0020212664table60398192112020>`__ describes the response parameters. 

.. _ENUSTOPIC0020212664table60398192112020:

.. table:: **Table 5** Response parameters

   +---------------------+--------+---------------------------------------------------------------------------------------+
   | Parameter           | Type   | Description                                                                           |
   +=====================+========+=======================================================================================+
   | interfaceAttachment | Object | Specifies ECS NICs. For details, see `Table 6 <#enustopic0020212664table49017803>`__. |
   +---------------------+--------+---------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212664table49017803:

.. table:: **Table 6** **interfaceAttachment** field description

   +------------+------------------+----------------------------------------------------------------------------------------------------------+
   | Parameter  | Type             | Description                                                                                              |
   +============+==================+==========================================================================================================+
   | port_state | String           | Specifies the port state.                                                                                |
   +------------+------------------+----------------------------------------------------------------------------------------------------------+
   | fixed_ips  | Array of objects | Specifies IP addresses for NICs. For details, see `Table 7 <#enustopic0020212664table35098076112057>`__. |
   +------------+------------------+----------------------------------------------------------------------------------------------------------+
   | port_id    | String           | Specifies the port ID.                                                                                   |
   +------------+------------------+----------------------------------------------------------------------------------------------------------+
   | net_id     | String           | Specifies the network ID.                                                                                |
   +------------+------------------+----------------------------------------------------------------------------------------------------------+
   | mac_addr   | String           | Specifies the MAC address.                                                                               |
   +------------+------------------+----------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212664table35098076112057:

.. table:: **Table 7** **fixed_ips** field description

   ========== ====== ===============================================
   Parameter  Type   Description
   ========== ====== ===============================================
   subnet_id  String Specifies the ID of the subnet used by the NIC.
   ip_address String Specifies the NIC IP address.
   ========== ====== ===============================================

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2/{project_id}/servers/{server_id}/os-interface
   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/os-interface

.. code-block::

   {
       "interfaceAttachment" : {
           "fixed_ips" : [ 
               {
                   "ip_address" : "192.168.1.3"
               } 
            ],
       "net_id" : "3cb9bc59-5699-4588-a4b1-b87f96708bc6"
       }
   }

.. code-block::

   {
       "interfaceAttachment" : {
       "port_id" : "ce531f90-199f-48c0-816c-13e38010b442"
       }
   }

Example Response
----------------

.. code-block::

   {
       "interfaceAttachment": {
           "port_state": "DOWN",
           "fixed_ips": [
               {
                   "subnet_id": "d9cfef77-0151-4c2a-9ed5-d951ada8adf3",
                   "ip_address": "10.0.1.11"
               }
           ],
           "port_id": " ce531f90-199f-48c0-816c-13e38010b442",
           "net_id": "0dc714fa-9022-4a03-bb22-9821a396bb9d",
           "mac_addr": "fa:16:3e:63:75:b2"
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


