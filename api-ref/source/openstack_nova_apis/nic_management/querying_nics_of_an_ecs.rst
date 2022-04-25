:original_name: en-us_topic_0020212662.html

.. _en-us_topic_0020212662:

Querying NICs of an ECS
=======================

Function
--------

This API is used to query NICs of an ECS based on the NIC ID.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/os-interface/{id}

GET /v2/{project_id}/servers/{server_id}/os-interface/{id}

:ref:`Table 1 <en-us_topic_0020212662__table25654779>` describes the parameters in the URI.

.. _en-us_topic_0020212662__table25654779:

.. table:: **Table 1** Parameter description

   ========== ========= =================================
   Parameter  Mandatory Description
   ========== ========= =================================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   id         Yes       Specifies the port ID of the NIC.
   ========== ========= =================================

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0020212662__table59131099>` describes the response parameters.

.. _en-us_topic_0020212662__table59131099:

.. table:: **Table 2** Response parameters

   +---------------------+--------+----------------------------------------------------------------------------------------------+
   | Parameter           | Type   | Description                                                                                  |
   +=====================+========+==============================================================================================+
   | interfaceAttachment | Object | Specifies ECS NICs. For details, see :ref:`Table 3 <en-us_topic_0020212662__table24005299>`. |
   +---------------------+--------+----------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212662__table24005299:

.. table:: **Table 3** **interfaceAttachment** field description

   +------------+------------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter  | Type             | Description                                                                                               |
   +============+==================+===========================================================================================================+
   | port_state | String           | Specifies the NIC port status.                                                                            |
   +------------+------------------+-----------------------------------------------------------------------------------------------------------+
   | fixed_ips  | Array of objects | Specifies IP addresses for NICs. For details, see :ref:`Table 4 <en-us_topic_0020212662__table53180163>`. |
   +------------+------------------+-----------------------------------------------------------------------------------------------------------+
   | net_id     | String           | Specifies the network ID to which the NIC port belongs.                                                   |
   +------------+------------------+-----------------------------------------------------------------------------------------------------------+
   | port_id    | String           | Specifies the ID of the NIC port.                                                                         |
   +------------+------------------+-----------------------------------------------------------------------------------------------------------+
   | mac_addr   | String           | Specifies the MAC address of the NIC.                                                                     |
   +------------+------------------+-----------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212662__table53180163:

.. table:: **Table 4** **fixed_ips** field description

   ========== ====== ===============================================
   Parameter  Type   Description
   ========== ====== ===============================================
   subnet_id  String Specifies the ID of the subnet used by the NIC.
   ip_address String Specifies the NIC IP address.
   ========== ====== ===============================================

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/{project_id}/servers/{server_id}/os-interface/{id}
   GET https://{endpoint}/v2.1/{project_id}/servers/{server_id}/os-interface/{id}

Example Response
----------------

.. code-block::

   {
       "interfaceAttachment": 
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
                       }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
