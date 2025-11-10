:original_name: en-us_topic_0022472987.html

.. _en-us_topic_0022472987:

Attaching a Disk to an ECS
==========================

Function
--------

This API is used to attach a disk to an ECS.

This API is an asynchronous API. After the attachment request is successfully delivered, a job ID is returned. This does not mean the attachment is complete. You need to call the API by referring to :ref:`Querying Task Execution Status <en-us_topic_0022225398>` to query the job status. The SUCCESS status indicates that the attachment is successful.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/attachvolume

:ref:`Table 1 <en-us_topic_0022472987__table35528365105553>` describes the parameters in the URI.

.. _en-us_topic_0022472987__table35528365105553:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

.. table:: **Table 2** Request parameters

   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                |
   +==================+=================+=================+============================================================================================================================================================================================================================================================================================+
   | volumeAttachment | Yes             | Object          | Specifies the ECS attachment information. For details, see :ref:`Table 3 <en-us_topic_0022472987__table40707503151632>`.                                                                                                                                                                   |
   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dry_run          | No              | Boolean         | Specifies whether to check the request and attach the disk.                                                                                                                                                                                                                                |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                            |
   |                  |                 |                 | -  **true**: indicates that only the request is sent, and no disk will be attached. Check items include mandatory parameters, request format, and service restrictions. If the check fails, the system returns an error. If the check result is as expected, the system properly responds. |
   |                  |                 |                 | -  **false**: indicates that only the request is sent and the disk will be attached if the check result is as expected.                                                                                                                                                                    |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                            |
   |                  |                 |                 | The default value is **false**.                                                                                                                                                                                                                                                            |
   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0022472987__table40707503151632:

.. table:: **Table 3** **volumeAttachment** field description

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | volumeId        | Yes             | String          | Specifies the ID of the disk to be attached. The value is in UUID format.                                                                                                                                                                                                                                                                                                                                                                                |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | device          | No              | String          | Indicates the disk device name.                                                                                                                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 |    -  The new disk device name cannot be the same as an existing one.                                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 |    -  For KVM ECSs, set the parameter value to **/dev/vda** for system disks. The device names for data disks of KVM ECSs are optional. If the device names of data disks are required, set them in alphabetical order. For example, if there are two data disks, set the device names of the two data disks to **/dev/vdb** and **/dev/vdc**, respectively. If you set a device name starting with **/dev/sd**, the system uses **/dev/vd** by default. |
   |                 |                 |                 |    -  For ECSs that only support SCSI disks, set the device name of the system disk to **/dev/sda** and the device names of data disks in alphabetical order, for example, **/dev/sdb** and **/dev/sdc**. The system will not change the default device names.                                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_type     | No              | String          | Specifies the disk type.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | count           | No              | Integer         | Specifies the number of disks.                                                                                                                                                                                                                                                                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hw:passthrough  | No              | String          | -  If this parameter is set to **true**, the disk device type is SCSI, which allows ECS OSs to directly access the underlying storage media. SCSI reservation commands are supported.                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | -  If this parameter is set to **false**, the disk device type is VBD, which supports only simple SCSI read/write commands.                                                                                                                                                                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

See :ref:`Responses (Task) <en-us_topic_0022067714>`.

Example Request
---------------

-  Attach a SCSI EVS disk to device **/dev/sda**.

   .. code-block:: text

      POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/attachvolume

      {
          "volumeAttachment": {
               "volumeId": "a26887c6-c47b-4654-abb5-dfadf7d3f803",
               "device": "/dev/sda",
               "volume_type": "SSD",
               "count": 5,
               "hw:passthrough": "true"
          },
          "dry_run": false
      }

-  Send a pre-check request for attaching a disk.

   .. code-block:: text

      POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/attachvolume

      {
          "volumeAttachment": {
               "volumeId": "a26887c6-c47b-4654-abb5-dfadf7d3f803",
               "volume_type": "SSD",
               "count": 1,
               "hw:passthrough": "true"
          },
          "dry_run": true
      }

Example Response
----------------

.. code-block::

   {
       "job_id": "ff80808288d41e1b018990260955686a"
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
