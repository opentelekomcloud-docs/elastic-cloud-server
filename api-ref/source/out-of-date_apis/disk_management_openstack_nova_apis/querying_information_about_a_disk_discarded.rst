Querying Information About a Disk (Discarded)
=============================================

Function
--------

This API is used to query information about a specified disk.

This API has been discarded. Use the EVS API "Querying Details About a Disk (OpenStack Cinder API v2)".

URI
---

GET /v2/{project_id}/os-volumes/{volume_id}

GET /v2.1/{project_id}/os-volumes/{volume_id}

`Table 1 <#enustopic0065817711enustopic0057973212table2814978410562>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817711enustopic0057973212table2814978410562:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   volume_id  Yes       Specifies the disk ID.
   ========== ========= =========================

Request
-------

None

Response
--------

`Table 2 <#enustopic0065817711enustopic0057973212table27581142>`__ describes the response parameters.



.. _ENUSTOPIC0065817711enustopic0057973212table27581142:

.. table:: **Table 2** Response parameters

   +--------------------+------------------+----------------------------------------------------+
   | Parameter          | Type             | Description                                        |
   +====================+==================+====================================================+
   | id                 | String           | Specifies the disk ID in UUID format.              |
   +--------------------+------------------+----------------------------------------------------+
   | displayName        | String           | Specifies the disk name.                           |
   +--------------------+------------------+----------------------------------------------------+
   | status             | String           | Specifies the disk status.                         |
   +--------------------+------------------+----------------------------------------------------+
   | attachments        | Array of objects | Specifies the attachment information about a disk. |
   +--------------------+------------------+----------------------------------------------------+
   | availabilityZone   | String           | Specifies the AZ to which the disk belongs.        |
   +--------------------+------------------+----------------------------------------------------+
   | createdAt          | String           | Specifies the time when the disk was created.      |
   +--------------------+------------------+----------------------------------------------------+
   | displayDescription | String           | Specifies the disk description.                    |
   +--------------------+------------------+----------------------------------------------------+
   | volumeType         | String           | Specifies the disk type.                           |
   +--------------------+------------------+----------------------------------------------------+
   | snapshotId         | String           | Specifies the snapshot ID.                         |
   +--------------------+------------------+----------------------------------------------------+
   | metadata           | Object           | Specifies the disk metadata.                       |
   +--------------------+------------------+----------------------------------------------------+
   | size               | Integer          | Specifies the disk size.                           |
   +--------------------+------------------+----------------------------------------------------+



.. _ENUSTOPIC0065817711enustopic0057973212table10694153118228:

.. table:: **Table 3** **attachments** field description

   ========= ====== =====================================================
   Parameter Type   Description
   ========= ====== =====================================================
   device    String Specifies the directory to which the disk is mounted.
   id        String Specifies the ID of the attached resource.
   serverId  String Specifies the ECS ID.
   volumeId  String Specifies the ID of the attached disk.
   ========= ====== =====================================================

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/b84c367e4d1047fc9b54f28b400ddbc2/os-volumes/70b14513-faad-4646-b7ab-a065cef282b4
   GET https://{endpoint}/v2.1/b84c367e4d1047fc9b54f28b400ddbc2/os-volumes/70b14513-faad-4646-b7ab-a065cef282b4

Example Response
----------------

.. code-block::

   {
       "volume": 
       {
           "status": "available",
           "attachments": [{}],
           "availabilityZone": "nova",
           "createdAt": "2016-05-20T07:57:56.299000",
           "displayDescription": null,
           "volumeType": null,
           "dispalyName": "test",
           "snapshotId": null,
           "metadata": {},
           "id": "70b14513-faad-4646-b7ab-a065cef282b4",
           "size": 1    
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

