:original_name: en-us_topic_0020212661.html

.. _en-us_topic_0020212661:

Listing NICs of an ECS
======================

Function
--------

This API is used to list NICs attached to an ECS.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/os-interface

GET /v2/{project_id}/servers/{server_id}/os-interface

:ref:`Table 1 <en-us_topic_0020212661__table38523909>` describes the parameters in the URI.

.. _en-us_topic_0020212661__table38523909:

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

:ref:`Table 2 <en-us_topic_0020212661__table25276401>` describes the response parameters.

.. _en-us_topic_0020212661__table25276401:

.. table:: **Table 2** Response parameters

   +----------------------+------------------+----------------------------------------------------------------------------------------------+
   | Parameter            | Type             | Description                                                                                  |
   +======================+==================+==============================================================================================+
   | interfaceAttachments | Array of objects | Specifies ECS NICs. For details, see :ref:`Table 3 <en-us_topic_0020212661__table49805933>`. |
   +----------------------+------------------+----------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212661__table49805933:

.. table:: **Table 3** **interfaceAttachments** field description

   +------------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type             | Description                                                                                                       |
   +============+==================+===================================================================================================================+
   | port_state | String           | Specifies the NIC port status.                                                                                    |
   +------------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | fixed_ips  | Array of objects | Specifies private IP addresses for NICs. For details, see :ref:`Table 4 <en-us_topic_0020212661__table19750463>`. |
   +------------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | net_id     | String           | Specifies the network ID (network_id) that the NIC port belongs to.                                               |
   +------------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | port_id    | String           | Specifies the ID of the NIC port.                                                                                 |
   +------------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | mac_addr   | String           | Specifies the MAC address of the NIC.                                                                             |
   +------------+------------------+-------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212661__table19750463:

.. table:: **Table 4** **fixed_ips** field description

   ========== ====== ===================================================
   Parameter  Type   Description
   ========== ====== ===================================================
   subnet_id  String Specifies the subnet of the NIC private IP address.
   ip_address String Specifies the NIC private IP address.
   ========== ====== ===================================================

Example Request
---------------

List NICs attached to an ECS.

.. code-block:: text

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
