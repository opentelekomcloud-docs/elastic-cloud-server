:original_name: en-us_topic_0121978383.html

.. _en-us_topic_0121978383:

Listing NICs of an ECS
======================

Function
--------

This API is used to list NICs of an ECS.

URI
---

GET /v1/{project_id}/cloudservers/{server_id}/os-interface

:ref:`Table 1 <en-us_topic_0121978383__table38523909>` describes the parameters in the URI.

.. _en-us_topic_0121978383__table38523909:

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

:ref:`Table 2 <en-us_topic_0121978383__table25276401>` describes the response parameters.

.. _en-us_topic_0121978383__table25276401:

.. table:: **Table 2** Response parameters

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                           |
   +=======================+=======================+=======================================================================================================================================+
   | interfaceAttachments  | Array of objects      | **Definition**                                                                                                                        |
   |                       |                       |                                                                                                                                       |
   |                       |                       | Specifies ECS NICs. For details, see :ref:`Table 3 <en-us_topic_0121978383__table49805933>`.                                          |
   |                       |                       |                                                                                                                                       |
   |                       |                       | **Range**                                                                                                                             |
   |                       |                       |                                                                                                                                       |
   |                       |                       | N/A                                                                                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | attachableQuantity    | Object                | **Definition**                                                                                                                        |
   |                       |                       |                                                                                                                                       |
   |                       |                       | Specifies the number of NICs that can be attached to an ECS. For details, see :ref:`Table 4 <en-us_topic_0121978383__table19750463>`. |
   |                       |                       |                                                                                                                                       |
   |                       |                       | **Range**                                                                                                                             |
   |                       |                       |                                                                                                                                       |
   |                       |                       | N/A                                                                                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0121978383__table49805933:

.. table:: **Table 3** **interfaceAttachments** field description

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                             |
   +=======================+=======================+=========================================================================================================================+
   | port_state            | String                | **Definition**                                                                                                          |
   |                       |                       |                                                                                                                         |
   |                       |                       | Specifies the NIC port status.                                                                                          |
   |                       |                       |                                                                                                                         |
   |                       |                       | **Range**                                                                                                               |
   |                       |                       |                                                                                                                         |
   |                       |                       | N/A                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | fixed_ips             | Array of objects      | **Definition**                                                                                                          |
   |                       |                       |                                                                                                                         |
   |                       |                       | Specifies private IP addresses for NICs. For details, see :ref:`Table 5 <en-us_topic_0121978383__table15567163961815>`. |
   |                       |                       |                                                                                                                         |
   |                       |                       | **Range**                                                                                                               |
   |                       |                       |                                                                                                                         |
   |                       |                       | N/A                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | net_id                | String                | **Definition**                                                                                                          |
   |                       |                       |                                                                                                                         |
   |                       |                       | Specifies the network ID (network_id) that the NIC port belongs to.                                                     |
   |                       |                       |                                                                                                                         |
   |                       |                       | **Range**                                                                                                               |
   |                       |                       |                                                                                                                         |
   |                       |                       | N/A                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | port_id               | String                | **Definition**                                                                                                          |
   |                       |                       |                                                                                                                         |
   |                       |                       | Specifies the NIC port ID.                                                                                              |
   |                       |                       |                                                                                                                         |
   |                       |                       | **Range**                                                                                                               |
   |                       |                       |                                                                                                                         |
   |                       |                       | N/A                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | mac_addr              | String                | **Definition**                                                                                                          |
   |                       |                       |                                                                                                                         |
   |                       |                       | Specifies the MAC address of the NIC.                                                                                   |
   |                       |                       |                                                                                                                         |
   |                       |                       | **Range**                                                                                                               |
   |                       |                       |                                                                                                                         |
   |                       |                       | N/A                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | delete_on_termination | Boolean               | **Definition**                                                                                                          |
   |                       |                       |                                                                                                                         |
   |                       |                       | Specifies whether to delete a NIC when detaching it.                                                                    |
   |                       |                       |                                                                                                                         |
   |                       |                       | **Range**                                                                                                               |
   |                       |                       |                                                                                                                         |
   |                       |                       | -  **true**: Delete the NIC.                                                                                            |
   |                       |                       | -  **false**: Do not delete the NIC.                                                                                    |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | driver_mode           | String                | **Definition**                                                                                                          |
   |                       |                       |                                                                                                                         |
   |                       |                       | Specifies the NIC driver type, which is **virtio** by default. This parameter is a reserved field.                      |
   |                       |                       |                                                                                                                         |
   |                       |                       | **Range**                                                                                                               |
   |                       |                       |                                                                                                                         |
   |                       |                       | N/A                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | min_rate              | Integer               | **Definition**                                                                                                          |
   |                       |                       |                                                                                                                         |
   |                       |                       | Specifies the minimum NIC bandwidth.                                                                                    |
   |                       |                       |                                                                                                                         |
   |                       |                       | **Range**                                                                                                               |
   |                       |                       |                                                                                                                         |
   |                       |                       | N/A                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | multiqueue_num        | Integer               | **Definition**                                                                                                          |
   |                       |                       |                                                                                                                         |
   |                       |                       | Specifies the number of queues.                                                                                         |
   |                       |                       |                                                                                                                         |
   |                       |                       | **Range**                                                                                                               |
   |                       |                       |                                                                                                                         |
   |                       |                       | 1-64                                                                                                                    |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | pci_address           | String                | **Definition**                                                                                                          |
   |                       |                       |                                                                                                                         |
   |                       |                       | Specifies the BDF number of the NIC in Linux GuestOS.                                                                   |
   |                       |                       |                                                                                                                         |
   |                       |                       | .. note::                                                                                                               |
   |                       |                       |                                                                                                                         |
   |                       |                       |    If the NIC is not supported, no information will be returned.                                                        |
   |                       |                       |                                                                                                                         |
   |                       |                       | **Range**                                                                                                               |
   |                       |                       |                                                                                                                         |
   |                       |                       | N/A                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0121978383__table19750463:

.. table:: **Table 4** **attachableQuantity** field description

   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                            |
   +=======================+=======================+========================================================================+
   | free_nic              | Integer               | **Definition**                                                         |
   |                       |                       |                                                                        |
   |                       |                       | Specifies the remaining number of NICs that can be attached to an ECS. |
   |                       |                       |                                                                        |
   |                       |                       | **Range**                                                              |
   |                       |                       |                                                                        |
   |                       |                       | N/A                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | free_efi_nic          | Integer               | **Definition**                                                         |
   |                       |                       |                                                                        |
   |                       |                       | Specifies the remaining number of EFIs that can be attached to an ECS. |
   |                       |                       |                                                                        |
   |                       |                       | **Range**                                                              |
   |                       |                       |                                                                        |
   |                       |                       | N/A                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------+

.. _en-us_topic_0121978383__table15567163961815:

.. table:: **Table 5** **fixed_ips** field description

   +-----------------------+-----------------------+-----------------------------------------------------+
   | Parameter             | Type                  | Description                                         |
   +=======================+=======================+=====================================================+
   | subnet_id             | String                | **Definition**                                      |
   |                       |                       |                                                     |
   |                       |                       | Specifies the subnet of the NIC private IP address. |
   |                       |                       |                                                     |
   |                       |                       | **Range**                                           |
   |                       |                       |                                                     |
   |                       |                       | N/A                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | ip_address            | String                | **Definition**                                      |
   |                       |                       |                                                     |
   |                       |                       | Specifies the NIC private IP address.               |
   |                       |                       |                                                     |
   |                       |                       | **Range**                                           |
   |                       |                       |                                                     |
   |                       |                       | N/A                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------+

Example Request
---------------

List NICs of an ECS.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/os-interface

Example Response
----------------

.. code-block::

   {
       "attachableQuantity": {
           "free_nic": 1,
           "free_efi_nic": 0
       },
       "interfaceAttachments": [
           {
               "port_state": "ACTIVE",
               "fixed_ips": [
                   {
                       "subnet_id": "ba31e1f5-fa76-4530-862c-5176fad033cf",
                       "ip_address": "192.168.0.33"
                   }
               ],
               "net_id": "610a4af2-1d90-4d2b-8057-dc238b26febf",
               "port_id": "04819c0a-6a07-44b6-945e-fb932071888e",
               "mac_addr": "fa:16:3e:45:65:c4",
               "delete_on_termination": false,
               "driver_mode": null,
               "min_rate": null,
               "multiqueue_num": null,
               "pci_address": null
           }
       ]
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
