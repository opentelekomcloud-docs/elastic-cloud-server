Querying a Disk Attached to an ECS
==================================

Function
--------

This API is used to query a disk attached to an ECS based on the disk ID.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/os-volume_attachments/{volume_id}

GET /v2/{project_id}/servers/{server_id}/os-volume_attachments/{volume_id}

`Table 1 <#enustopic0020212672table61787501>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212672table61787501:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   volume_id  Yes       Specifies the disk ID.
   ========== ========= =========================

Request
-------

None

Response
--------

`Table 2 <#enustopic0020212672table769899>`__ describes the response parameters. 

.. _ENUSTOPIC0020212672table769899:

.. table:: **Table 2** Response parameters

   +------------------+--------+-----------------------------------------------------------------------------------------------------------+
   | Parameter        | Type   | Description                                                                                               |
   +==================+========+===========================================================================================================+
   | volumeAttachment | Object | Specifies the disks attached to an ECS. For details, see `Table 3 <#enustopic0020212672table42716605>`__. |
   +------------------+--------+-----------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212672table42716605:

.. table:: **Table 3** **volumeAttachment** field description

   ========= ====== ==========================================
   Parameter Type   Description
   ========= ====== ==========================================
   device    String Specifies the attached directory.
   id        String Specifies the ID of the attached resource.
   serverId  String Specifies the ECS ID.
   volumeId  String Specifies the ID of the attached disk.
   ========= ====== ==========================================

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/{project_id}/servers/{server_id}/os-volume_attachments/{volume_id}
   GET https://{endpoint}/v2.1/{project_id}/servers/{server_id}/os-volume_attachments/{volume_id}

Example Response
----------------

.. code-block::

   {
       "volumeAttachment": 
           {
               "device": "/dev/sdd",
               "id": "a26887c6-c47b-4654-abb5-dfadf7d3f803",
               "serverId": "4d8c3732-a248-40ed-bebc-539a6ffd25c0",
               "volumeId": "a26887c6-c47b-4654-abb5-dfadf7d3f803"
           }
    }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


