Querying ECS NICs
=================

Function
--------

This API is used to query information about ECS NICs.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/os-interface

GET /v2/{project_id}/servers/{server_id}/os-interface

`Table 1 <#enustopic0020212661table38523909>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212661table38523909:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

None

Response
--------

`Table 2 <#enustopic0020212661table25276401>`__ describes the response parameters. 

.. _ENUSTOPIC0020212661table25276401:

.. table:: **Table 2** Response parameters

   +----------------------+------------------+---------------------------------------------------------------------------------------+
   | Parameter            | Type             | Description                                                                           |
   +======================+==================+=======================================================================================+
   | interfaceAttachments | Array of objects | Specifies ECS NICs. For details, see `Table 3 <#enustopic0020212661table49805933>`__. |
   +----------------------+------------------+---------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212661table49805933:

.. table:: **Table 3** **interfaceAttachments** field description

   +------------+------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type             | Description                                                                                                |
   +============+==================+============================================================================================================+
   | port_state | String           | Specifies the NIC port status.                                                                             |
   +------------+------------------+------------------------------------------------------------------------------------------------------------+
   | fixed_ips  | Array of objects | Specifies private IP addresses for NICs. For details, see `Table 4 <#enustopic0020212661table19750463>`__. |
   +------------+------------------+------------------------------------------------------------------------------------------------------------+
   | net_id     | String           | Specifies the network ID to which the NIC port belongs.                                                    |
   +------------+------------------+------------------------------------------------------------------------------------------------------------+
   | port_id    | String           | Specifies the ID of the NIC port.                                                                          |
   +------------+------------------+------------------------------------------------------------------------------------------------------------+
   | mac_addr   | String           | Specifies the MAC address of the NIC.                                                                      |
   +------------+------------------+------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212661table19750463:

.. table:: **Table 4** **fixed_ips** field description

   ========== ====== ===================================================
   Parameter  Type   Description
   ========== ====== ===================================================
   subnet_id  String Specifies the subnet of the NIC private IP address.
   ip_address String Specifies the NIC private IP address.
   ========== ====== ===================================================

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/{project_id}/servers/{server_id}/os-interface
   GET https://{endpoint}/v2.1/{project_id}/servers/{server_id}/os-interface

Example Response
----------------

.. code-block::

   {
       "interfaceAttachments": [
           {
               "port_state": "ACTIVE",
               "fixed_ips": [
                   {
                       "subnet_id": "f8a6e8f8-c2ec-497c-9f23-da9616de54ef",
                       "ip_address": "192.168.1.3"
                   }
               ],
               "net_id": "3cb9bc59-5699-4588-a4b1-b87f96708bc6",
               "port_id": "ce531f90-199f-48c0-816c-13e38010b442",
               "mac_addr": "fa:16:3e:4c:2c:30"
           }
       ]
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


