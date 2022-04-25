:original_name: en-us_topic_0020212664.html

.. _en-us_topic_0020212664:

Adding a NIC to an ECS
======================

Function
--------

This API is used to add a NIC to an ECS.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/os-interface

POST /v2/{project_id}/servers/{server_id}/os-interface

:ref:`Table 1 <en-us_topic_0020212664__table55925239>` describes the parameters in the URI.

.. _en-us_topic_0020212664__table55925239:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0020212664__table21989419>` describes the request parameters.

.. _en-us_topic_0020212664__table21989419:

.. table:: **Table 2** Request parameters

   +---------------------+-----------+--------+----------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory | Type   | Description                                                                                              |
   +=====================+===========+========+==========================================================================================================+
   | interfaceAttachment | Yes       | Object | Specifies the NICs to be added. For details, see :ref:`Table 3 <en-us_topic_0020212664__table44975500>`. |
   +---------------------+-----------+--------+----------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212664__table44975500:

.. table:: **Table 3** **interfaceAttachment** field description

   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                              |
   +=================+=================+==================+==========================================================================================================================================================================================+
   | port_id         | No              | String           | Specifies the port ID.                                                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                                                                          |
   |                 |                 |                  | Either **port_id** or **net_id** is used each time.                                                                                                                                      |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | net_id          | No              | String           | Specifies the network ID.                                                                                                                                                                |
   |                 |                 |                  |                                                                                                                                                                                          |
   |                 |                 |                  | Either **port_id** or **net_id** is used each time.                                                                                                                                      |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fixed_ips       | No              | Array of objects | Specifies a private IP address.                                                                                                                                                          |
   |                 |                 |                  |                                                                                                                                                                                          |
   |                 |                 |                  | This parameter cannot be specified when **port_id** is used.                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                          |
   |                 |                 |                  | This parameter must be used with **net_id**.                                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                          |
   |                 |                 |                  | Only the first element in the list is valid. If two or more elements are used, an error will be reported. For details, see :ref:`Table 4 <en-us_topic_0020212664__table26224215175117>`. |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212664__table26224215175117:

.. table:: **Table 4** **fixed_ips** field description

   ========== ========= ====== =========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================
   ip_address No        String Specifies the IP address.
   ========== ========= ====== =========================

Response
--------

:ref:`Table 5 <en-us_topic_0020212664__table60398192112020>` describes the response parameters.

.. _en-us_topic_0020212664__table60398192112020:

.. table:: **Table 5** Response parameters

   +---------------------+--------+----------------------------------------------------------------------------------------------+
   | Parameter           | Type   | Description                                                                                  |
   +=====================+========+==============================================================================================+
   | interfaceAttachment | Object | Specifies ECS NICs. For details, see :ref:`Table 6 <en-us_topic_0020212664__table49017803>`. |
   +---------------------+--------+----------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212664__table49017803:

.. table:: **Table 6** **interfaceAttachment** field description

   +------------+------------------+-----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type             | Description                                                                                                     |
   +============+==================+=================================================================================================================+
   | port_state | String           | Specifies the port state.                                                                                       |
   +------------+------------------+-----------------------------------------------------------------------------------------------------------------+
   | fixed_ips  | Array of objects | Specifies IP addresses for NICs. For details, see :ref:`Table 7 <en-us_topic_0020212664__table35098076112057>`. |
   +------------+------------------+-----------------------------------------------------------------------------------------------------------------+
   | port_id    | String           | Specifies the port ID.                                                                                          |
   +------------+------------------+-----------------------------------------------------------------------------------------------------------------+
   | net_id     | String           | Specifies the network ID.                                                                                       |
   +------------+------------------+-----------------------------------------------------------------------------------------------------------------+
   | mac_addr   | String           | Specifies the MAC address.                                                                                      |
   +------------+------------------+-----------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212664__table35098076112057:

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
