Attaching a Disk to an ECS
==========================

Function
--------

This API is used to attach a disk to an ECS.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/attachvolume

`Table 1 <#enustopic0022472987table35528365105553>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0022472987table35528365105553:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------



.. _ENUSTOPIC0022472987table55654045105553:

.. table:: **Table 2** Request parameters

   +------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory | Type   | Description                                                                                                       |
   +==================+===========+========+===================================================================================================================+
   | volumeAttachment | Yes       | Object | Specifies the ECS attachment information. For details, see `Table 3 <#enustopic0022472987table40707503151632>`__. |
   +------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0022472987table40707503151632:

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
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

See `Responses (Task) <../../common_parameters/task_request_result/responses_task.html>`__.

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/attachvolume

.. code-block::

   {
       "volumeAttachment": {
            "volumeId": "a26887c6-c47b-4654-abb5-dfadf7d3f803",
            "device": "/dev/sda"
       }
   }

Example Response
----------------

.. code-block::

   {
       "job_id": "70a599e0-31e7-49b7-b260-868f441e862b"
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


