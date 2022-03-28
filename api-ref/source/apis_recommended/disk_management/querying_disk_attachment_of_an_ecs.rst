Querying Disk Attachment of an ECS
==================================

Function
--------

This API is used to query disk attachment of an ECS.

URI
---

GET /v2.1/servers/{server_id}/block_device

`Table 1 <#enustopic0101860613table35893824>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0101860613table35893824:

.. table:: **Table 1** Parameter description

   ========= ========= ====================================
   Parameter Mandatory Description
   ========= ========= ====================================
   server_id Yes       Specifies the ECS ID in UUID format.
   ========= ========= ====================================

Request
-------

None

Response
--------

`Table 2 <#enustopic0101860613table57959838>`__ describes the response parameters. 

.. _ENUSTOPIC0101860613table57959838:

.. table:: **Table 2** Response parameters

   +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Type             | Description                                                                                                                          |
   +====================+==================+======================================================================================================================================+
   | volumeAttachments  | Array of objects | Specifies the disks attached to an ECS. For details, see `Table 3 <#enustopic0101860613table7886611>`__.                             |
   +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | attachableQuantity | Object           | Specifies the number of disks that can be attached to an ECS. For details, see `Table 4 <#enustopic0101860613table1635814953813>`__. |
   +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0101860613table7886611:

.. table:: **Table 3** **volumeAttachments** parameters

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
   | bus                   | String                | Indicates the disk bus type.                                                          |
   |                       |                       |                                                                                       |
   |                       |                       | Options: **virtio** and **scsi**                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+



.. _ENUSTOPIC0101860613table1635814953813:

.. table:: **Table 4** **attachableQuantity** parameters

   +-----------+---------+--------------------------------------------------------------------------+
   | Parameter | Type    | Description                                                              |
   +===========+=========+==========================================================================+
   | free_scsi | Integer | Specifies the number of SCSI disks that can be attached to an ECS.       |
   +-----------+---------+--------------------------------------------------------------------------+
   | free_blk  | Integer | Specifies the number of virtio_blk disks that can be attached to an ECS. |
   +-----------+---------+--------------------------------------------------------------------------+
   | free_disk | Integer | Specifies the total number of disks that can be attached to an ECS.      |
   +-----------+---------+--------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2.1/servers/4d8c3732-a248-40ed-bebc-539a6ffd25c0/block_device

Example Response
----------------

.. code-block::

   {
       "attachableQuantity": {
               "free_scsi": 23,
               "free_blk": 15,
               "free_disk": 23
        },
       "volumeAttachments": [
           {
               "pciAddress": "0000:02:01.0",
               "volumeId": "a26887c6-c47b-4654-abb5-dfadf7d3f803",
               "device": "/dev/vda",
               "serverId": "4d8c3732-a248-40ed-bebc-539a6ffd25c0",
               "id": "a26887c6-c47b-4654-abb5-dfadf7d3f803",
               "size": "40",
               "bootIndex": 0,
               "bus":"virtio"
           },
           {
               "pciAddress": "0000:02:02.0",
               "volumeId": "a26887c6-c47b-4654-abb5-asdf234r234r",
               "device": "/dev/vdb",
               "serverId": "4d8c3732-a248-40ed-bebc-539a6ffd25c0",
               "id": "a26887c6-c47b-4654-abb5-asdf234r234r",
               "size": "10",
               "bootIndex": 1,
               "bus":"virtio"
           }
       ]
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


