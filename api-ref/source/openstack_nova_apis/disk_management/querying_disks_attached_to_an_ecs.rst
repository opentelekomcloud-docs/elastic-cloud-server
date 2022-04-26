:original_name: en-us_topic_0020212671.html

.. _en-us_topic_0020212671:

Querying Disks Attached to an ECS
=================================

Function
--------

This API is used to query the disks attached to an ECS.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/os-volume_attachments

GET /v2/{project_id}/servers/{server_id}/os-volume_attachments

:ref:`Table 1 <en-us_topic_0020212671__table35893824>` describes the parameters in the URI.

.. _en-us_topic_0020212671__table35893824:

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

:ref:`Table 2 <en-us_topic_0020212671__table57959838>` describes the response parameters.

.. _en-us_topic_0020212671__table57959838:

.. table:: **Table 2** Response parameters

   +-------------------+------------------+-----------------------------------------------------------------------------------------------------------------+
   | Parameter         | Type             | Description                                                                                                     |
   +===================+==================+=================================================================================================================+
   | volumeAttachments | Array of objects | Specifies the disks attached to an ECS. For details, see :ref:`Table 3 <en-us_topic_0020212671__table7886611>`. |
   +-------------------+------------------+-----------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212671__table7886611:

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
