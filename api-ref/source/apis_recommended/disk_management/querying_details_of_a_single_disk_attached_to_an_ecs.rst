:original_name: en-us_topic_0167811961.html

.. _en-us_topic_0167811961:

Querying Details of a Single Disk Attached to an ECS
====================================================

Function
--------

This API is used to query details of a single disk attached to an ECS.

This API supports checking fine-grained permissions for enterprise projects. For details, see :ref:`ecs:cloudServers:showServerBlockDevice <en-us_topic_0103071514>`.

URI
---

GET /v1/{project_id}/cloudservers/{server_id}/block_device/{volume_id}

:ref:`Table 1 <en-us_topic_0167811961__table179834801714>` describes the parameters in the URI.

.. _en-us_topic_0167811961__table179834801714:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+-------------------------------------------+
   | Parameter             | Mandatory             | Description                               |
   +=======================+=======================+===========================================+
   | server_id             | Yes                   | **Definition**                            |
   |                       |                       |                                           |
   |                       |                       | Specifies the ECS ID in UUID format.      |
   |                       |                       |                                           |
   |                       |                       | **Constraints**                           |
   |                       |                       |                                           |
   |                       |                       | N/A                                       |
   |                       |                       |                                           |
   |                       |                       | **Range**                                 |
   |                       |                       |                                           |
   |                       |                       | N/A                                       |
   |                       |                       |                                           |
   |                       |                       | **Default Value**                         |
   |                       |                       |                                           |
   |                       |                       | N/A                                       |
   +-----------------------+-----------------------+-------------------------------------------+
   | project_id            | Yes                   | **Definition**                            |
   |                       |                       |                                           |
   |                       |                       | Specifies the project ID.                 |
   |                       |                       |                                           |
   |                       |                       | **Constraints**                           |
   |                       |                       |                                           |
   |                       |                       | N/A                                       |
   |                       |                       |                                           |
   |                       |                       | **Range**                                 |
   |                       |                       |                                           |
   |                       |                       | N/A                                       |
   |                       |                       |                                           |
   |                       |                       | **Default Value**                         |
   |                       |                       |                                           |
   |                       |                       | N/A                                       |
   +-----------------------+-----------------------+-------------------------------------------+
   | volume_id             | Yes                   | **Definition**                            |
   |                       |                       |                                           |
   |                       |                       | Specifies the EVS disk ID in UUID format. |
   |                       |                       |                                           |
   |                       |                       | **Constraints**                           |
   |                       |                       |                                           |
   |                       |                       | N/A                                       |
   |                       |                       |                                           |
   |                       |                       | **Range**                                 |
   |                       |                       |                                           |
   |                       |                       | N/A                                       |
   |                       |                       |                                           |
   |                       |                       | **Default Value**                         |
   |                       |                       |                                           |
   |                       |                       | N/A                                       |
   +-----------------------+-----------------------+-------------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0167811961__table11593131681815>` describes the response parameters.

.. _en-us_topic_0167811961__table11593131681815:

.. table:: **Table 2** Response parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                          |
   +=======================+=======================+======================================================================================================================+
   | volumeAttachment      | Object                | **Definition**                                                                                                       |
   |                       |                       |                                                                                                                      |
   |                       |                       | Specifies the disk attached to an ECS. For details, see :ref:`Table 3 <en-us_topic_0167811961__table1128997111919>`. |
   |                       |                       |                                                                                                                      |
   |                       |                       | **Range**                                                                                                            |
   |                       |                       |                                                                                                                      |
   |                       |                       | N/A                                                                                                                  |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0167811961__table1128997111919:

.. table:: **Table 3** **volumeAttachment** parameters

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
   |                       |                       | -  Non-**0** indicates a data disk.                                                      |
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

Example Request
---------------

Query information about a specified disk attached to an ECS.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/block_device/{volume_id}

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
