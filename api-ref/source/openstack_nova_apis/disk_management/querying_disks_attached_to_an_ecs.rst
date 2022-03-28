Querying Disks Attached to an ECS
=================================

Function
--------

This API is used to query the disks attached to an ECS.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/os-volume_attachments

GET /v2/{project_id}/servers/{server_id}/os-volume_attachments

`Table 1 <#enustopic0020212671table35893824>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212671table35893824:

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

**Response parameters**

`Table 2 <#enustopic0020212671table57959838>`__ describes the response parameters. 

.. _ENUSTOPIC0020212671table57959838:

.. table:: **Table 2** Response parameters

   +-------------------+------------------+----------------------------------------------------------------------------------------------------------+
   | Parameter         | Type             | Description                                                                                              |
   +===================+==================+==========================================================================================================+
   | volumeAttachments | Array of objects | Specifies the disks attached to an ECS. For details, see `Table 3 <#enustopic0020212671table7886611>`__. |
   +-------------------+------------------+----------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212671table7886611:

.. table:: **Table 3** **volumeAttachments** field description

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

   GET https://{endpoint}/v2/{project_id}/servers/{server_id}/os-volume_attachments
   GET https://{endpoint}/v2.1/{project_id}/servers/{server_id}/os-volume_attachments

Example Response
----------------

.. code-block::

   {
       "volumeAttachments": [
           {
               "device": "/dev/sdd",
               "id": "a26887c6-c47b-4654-abb5-dfadf7d3f803",
               "serverId": "4d8c3732-a248-40ed-bebc-539a6ffd25c0",
               "volumeId": "a26887c6-c47b-4654-abb5-dfadf7d3f803"
           },
           {
               "device": "/dev/sdc",
               "id": "a26887c6-c47b-4654-abb5-dfadf7d3f804",
               "serverId": "4d8c3732-a248-40ed-bebc-539a6ffd25c0",
               "volumeId": "a26887c6-c47b-4654-abb5-dfadf7d3f804"
           }
       ]
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


