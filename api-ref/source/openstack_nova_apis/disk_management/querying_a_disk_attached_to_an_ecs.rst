:original_name: en-us_topic_0020212672.html

.. _en-us_topic_0020212672:

Querying a Disk Attached to an ECS
==================================

Function
--------

This API is used to query a disk attached to an ECS based on the disk ID.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/os-volume_attachments/{volume_id}

GET /v2/{project_id}/servers/{server_id}/os-volume_attachments/{volume_id}

:ref:`Table 1 <en-us_topic_0020212672__table61787501>` describes the parameters in the URI.

.. _en-us_topic_0020212672__table61787501:

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

:ref:`Table 2 <en-us_topic_0020212672__table769899>` describes the response parameters.

.. _en-us_topic_0020212672__table769899:

.. table:: **Table 2** Response parameters

   +------------------+--------+------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Type   | Description                                                                                                      |
   +==================+========+==================================================================================================================+
   | volumeAttachment | Object | Specifies the disks attached to an ECS. For details, see :ref:`Table 3 <en-us_topic_0020212672__table42716605>`. |
   +------------------+--------+------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212672__table42716605:

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
