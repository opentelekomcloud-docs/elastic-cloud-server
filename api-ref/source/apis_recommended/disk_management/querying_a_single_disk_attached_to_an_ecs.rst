Querying a Single Disk Attached to an ECS
=========================================

Function
--------

This API is used to query a disk attached to an ECS.

URI
---

GET /v2.1/servers/{server_id}/block_device/{volume_id}

`Table 1 <#enustopic0101860614table35893824>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0101860614table35893824:

.. table:: **Table 1** Parameter description

   ========= ========= =========================================
   Parameter Mandatory Description
   ========= ========= =========================================
   server_id Yes       Specifies the ECS ID in UUID format.
   volume_id Yes       Specifies the EVS disk ID in UUID format.
   ========= ========= =========================================

Request
-------

None

Response
--------

`Table 2 <#enustopic0101860614table57959838>`__ describes the response parameters. 

.. _ENUSTOPIC0101860614table57959838:

.. table:: **Table 2** Response parameters

   +------------------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter        | Type   | Description                                                                                             |
   +==================+========+=========================================================================================================+
   | volumeAttachment | Object | Specifies the disk attached to an ECS. For details, see `Table 3 <#enustopic0101860614table7886611>`__. |
   +------------------+--------+---------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0101860614table7886611:

.. table:: **Table 3** **volumeAttachment** parameters

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                           |
   +=======================+=======================+=======================================================================================+
   | serverId              | String                | Specifies the ECS ID in UUID format.                                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | volumeId              | String                | Specifies the EVS disk ID in UUID format.                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | id                    | String                | Specifies the mount ID, which is the same as the EVS disk ID.                         |
   |                       |                       |                                                                                       |
   |                       |                       | The value is in UUID format.                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | size                  | Integer               | Specifies the EVS disk size in GB.                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | device                | String                | Specifies the drive letter of the EVS disk, which is the device name of the EVS disk. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | pciAddress            | String                | Specifies the PCI address.                                                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | bootIndex             | Boolean               | Specifies the EVS disk boot sequence.                                                 |
   |                       |                       |                                                                                       |
   |                       |                       | -  **0** indicates the system disk.                                                   |
   |                       |                       | -  Non-0 indicates a data disk.                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | bus                   | String                | Specifies the disk bus type.                                                          |
   |                       |                       |                                                                                       |
   |                       |                       | Options: **virtio** and **scsi**                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2.1/servers/{server_id}/block_device/{volume_id}

Example Response
----------------

.. code-block::

   {
       "volumeAttachment": {
           "pciAddress": "0000:02:01.0",
           "volumeId": "a26887c6-c47b-4654-abb5-asdf234r234r",
           "device": "/dev/vda",
           "serverId": "4d8c3732-a248-40ed-bebc-539a6ffd25c0",
           "id": "a26887c6-c47b-4654-abb5-asdf234r234r",
           "size": "40",
           "bootIndex": 0,
           "bus":"virtio"
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


