:original_name: en-us_topic_0065817714.html

.. _en-us_topic_0065817714:

Obtaining ECS Metadata with a Specified Key
===========================================

Function
--------

This API is used to obtain ECS metadata with a specified key.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/metadata/{key}

GET /v2/{project_id}/servers/{server_id}/metadata/{key}

:ref:`Table 1 <en-us_topic_0065817714__en-us_topic_0057973169_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0065817714__en-us_topic_0057973169_table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= ===============================
   Parameter  Mandatory Description
   ========== ========= ===============================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   key        Yes       Specifies the ECS metadata key.
   ========== ========= ===============================

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0065817714__en-us_topic_0057973169_table40140147>` describes the response parameters.

.. _en-us_topic_0065817714__en-us_topic_0057973169_table40140147:

.. table:: **Table 2** Response parameters

   ========= ====== ===================================================
   Parameter Type   Description
   ========= ====== ===================================================
   meta      Object Specifies the user-defined metadata key-value pair.
   ========= ====== ===================================================

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/servers/998af54b-5762-4041-abc1-f98a2c27b3a2/metadata/key1
   GET https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/servers/998af54b-5762-4041-abc1-f98a2c27b3a2/metadata/key1

Example Response
----------------

.. code-block::

   {
       "meta": {
           "key1": "value1"
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
