:original_name: en-us_topic_0101860614.html

.. _en-us_topic_0101860614:

Querying a Single Disk Attached to an ECS
=========================================

Function
--------

This API is used to query a disk attached to an ECS.

URI
---

GET /v2.1/servers/{server_id}/block_device/{volume_id}

:ref:`Table 1 <en-us_topic_0101860614__table35893824>` describes the parameters in the URI.

.. _en-us_topic_0101860614__table35893824:

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

:ref:`Table 2 <en-us_topic_0101860614__table57959838>` describes the response parameters.

.. _en-us_topic_0101860614__table57959838:

.. table:: **Table 2** Response parameters

   +------------------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter        | Type   | Description                                                                                                    |
   +==================+========+================================================================================================================+
   | volumeAttachment | Object | Specifies the disk attached to an ECS. For details, see :ref:`Table 3 <en-us_topic_0101860614__table7886611>`. |
   +------------------+--------+----------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0101860614__table7886611:

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
   |                       |                       | -  A non-zero value indicates a data disk.                                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | bus                   | String                | Specifies the disk bus type.                                                          |
   |                       |                       |                                                                                       |
   |                       |                       | Options: **virtio** and **scsi**                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
