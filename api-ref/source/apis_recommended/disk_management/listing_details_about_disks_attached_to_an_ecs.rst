:original_name: en-us_topic_0122107473.html

.. _en-us_topic_0122107473:

Listing Details About Disks Attached to an ECS
==============================================

Function
--------

This API is used to list details about disks attached to an ECS.

URI
---

GET /v1/{project_id}/cloudservers/{server_id}/block_device

:ref:`Table 1 <en-us_topic_0122107473__table35893824>` describes the parameters in the URI.

.. _en-us_topic_0122107473__table35893824:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+--------------------------------------+
   | Parameter             | Mandatory             | Description                          |
   +=======================+=======================+======================================+
   | project_id            | Yes                   | **Definition**                       |
   |                       |                       |                                      |
   |                       |                       | Specifies the project ID.            |
   |                       |                       |                                      |
   |                       |                       | **Constraints**                      |
   |                       |                       |                                      |
   |                       |                       | N/A                                  |
   |                       |                       |                                      |
   |                       |                       | **Range**                            |
   |                       |                       |                                      |
   |                       |                       | N/A                                  |
   |                       |                       |                                      |
   |                       |                       | **Default Value**                    |
   |                       |                       |                                      |
   |                       |                       | N/A                                  |
   +-----------------------+-----------------------+--------------------------------------+
   | server_id             | Yes                   | **Definition**                       |
   |                       |                       |                                      |
   |                       |                       | Specifies the ECS ID in UUID format. |
   |                       |                       |                                      |
   |                       |                       | **Constraints**                      |
   |                       |                       |                                      |
   |                       |                       | N/A                                  |
   |                       |                       |                                      |
   |                       |                       | **Range**                            |
   |                       |                       |                                      |
   |                       |                       | N/A                                  |
   |                       |                       |                                      |
   |                       |                       | **Default Value**                    |
   |                       |                       |                                      |
   |                       |                       | N/A                                  |
   +-----------------------+-----------------------+--------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0122107473__table57959838>` describes the response parameters.

.. _en-us_topic_0122107473__table57959838:

.. table:: **Table 2** Response parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                  |
   +=======================+=======================+==============================================================================================================================================+
   | volumeAttachments     | Array of objects      | **Definition**                                                                                                                               |
   |                       |                       |                                                                                                                                              |
   |                       |                       | Specifies the disks attached to an ECS. For details, see :ref:`Table 3 <en-us_topic_0122107473__table7886611>`.                              |
   |                       |                       |                                                                                                                                              |
   |                       |                       | **Range**                                                                                                                                    |
   |                       |                       |                                                                                                                                              |
   |                       |                       | N/A                                                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | attachableQuantity    | Object                | **Definition**                                                                                                                               |
   |                       |                       |                                                                                                                                              |
   |                       |                       | Specifies the number of disks that can be attached to an ECS. For details, see :ref:`Table 4 <en-us_topic_0122107473__table17531254101519>`. |
   |                       |                       |                                                                                                                                              |
   |                       |                       | **Range**                                                                                                                                    |
   |                       |                       |                                                                                                                                              |
   |                       |                       | N/A                                                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0122107473__table7886611:

.. table:: **Table 3** **volumeAttachments** parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                              |
   +=======================+=======================+==========================================================================================+
   | serverId              | String                | **Definition**                                                                           |
   |                       |                       |                                                                                          |
   |                       |                       | Specifies the ECS ID in UUID format.                                                     |
   |                       |                       |                                                                                          |
   |                       |                       | **Range**                                                                                |
   |                       |                       |                                                                                          |
   |                       |                       | N/A                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | volumeId              | String                | **Definition**                                                                           |
   |                       |                       |                                                                                          |
   |                       |                       | Specifies the EVS disk ID in UUID format.                                                |
   |                       |                       |                                                                                          |
   |                       |                       | **Range**                                                                                |
   |                       |                       |                                                                                          |
   |                       |                       | N/A                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | id                    | String                | **Definition**                                                                           |
   |                       |                       |                                                                                          |
   |                       |                       | Specifies the mount ID, which is the same as the EVS disk ID.                            |
   |                       |                       |                                                                                          |
   |                       |                       | The value is in UUID format.                                                             |
   |                       |                       |                                                                                          |
   |                       |                       | **Range**                                                                                |
   |                       |                       |                                                                                          |
   |                       |                       | N/A                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | size                  | Integer               | **Definition**                                                                           |
   |                       |                       |                                                                                          |
   |                       |                       | Specifies the EVS disk size, in GiB.                                                     |
   |                       |                       |                                                                                          |
   |                       |                       | **Range**                                                                                |
   |                       |                       |                                                                                          |
   |                       |                       | N/A                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | device                | String                | **Definition**                                                                           |
   |                       |                       |                                                                                          |
   |                       |                       | Specifies the drive letter of the EVS disk, displayed as the device name on the console. |
   |                       |                       |                                                                                          |
   |                       |                       | **Range**                                                                                |
   |                       |                       |                                                                                          |
   |                       |                       | N/A                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | pciAddress            | String                | **Definition**                                                                           |
   |                       |                       |                                                                                          |
   |                       |                       | Specifies the PCI address.                                                               |
   |                       |                       |                                                                                          |
   |                       |                       | **Range**                                                                                |
   |                       |                       |                                                                                          |
   |                       |                       | N/A                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | bootIndex             | Integer               | **Definition**                                                                           |
   |                       |                       |                                                                                          |
   |                       |                       | Specifies the EVS disk boot sequence.                                                    |
   |                       |                       |                                                                                          |
   |                       |                       | **Range**                                                                                |
   |                       |                       |                                                                                          |
   |                       |                       | -  **0** indicates the system disk.                                                      |
   |                       |                       | -  A non-zero value indicates a data disk.                                               |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | bus                   | String                | **Definition**                                                                           |
   |                       |                       |                                                                                          |
   |                       |                       | Specifies the disk bus type.                                                             |
   |                       |                       |                                                                                          |
   |                       |                       | **Range**                                                                                |
   |                       |                       |                                                                                          |
   |                       |                       | -  virtio                                                                                |
   |                       |                       | -  scsi                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+

.. _en-us_topic_0122107473__table17531254101519:

.. table:: **Table 4** **attachableQuantity** parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                              |
   +=======================+=======================+==========================================================================+
   | free_scsi             | Integer               | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Specifies the number of SCSI disks that can be attached to an ECS.       |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | N/A                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | free_blk              | Integer               | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Specifies the number of virtio_blk disks that can be attached to an ECS. |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | N/A                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | free_disk             | Integer               | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Specifies the total number of disks that can be attached to an ECS.      |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | N/A                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+

Example Request
---------------

List details about disks attached to an ECS.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/block_device

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
               "size": 40,
               "bootIndex": 0,
               "bus":"virtio"
           },
           {
               "pciAddress": "0000:02:02.0",
               "volumeId": "a26887c6-c47b-4654-abb5-asdf234r234r",
               "device": "/dev/vdb",
               "serverId": "4d8c3732-a248-40ed-bebc-539a6ffd25c0",
               "id": "a26887c6-c47b-4654-abb5-asdf234r234r",
               "size": 10,
               "bootIndex": 1,
               "bus":"virtio"
           }
       ]
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
