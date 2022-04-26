:original_name: en-us_topic_0065817698.html

.. _en-us_topic_0065817698:

Querying the Metadata of a Specified Image (Discarded)
======================================================

Function
--------

This API is used to query the metadata of the specified image.

This API has been discarded. Use the API described in "Querying Image Metadata (Native OpenStack API)".

URI
---

GET /v2/{project_id}/images/{image_id}/metadata

GET /v2.1/{project_id}/images/{image_id}/metadata

:ref:`Table 1 <en-us_topic_0065817698__table5587311174112>` describes the parameters in the URI.

.. _en-us_topic_0065817698__table5587311174112:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   image_id   Yes       Specifies the image ID.
   ========== ========= =========================

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0065817698__table10666498410>` describes the response parameters.

.. _en-us_topic_0065817698__table10666498410:

.. table:: **Table 2** Response parameters

   ================== ====== =======================================
   Parameter          Type   Description
   ================== ====== =======================================
   User customization String Specifies the key pair of the metadata.
   ================== ====== =======================================

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/images/17a1890b-0fa4-485e-8505-14e294017988/metadata
   GET https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/images/17a1890b-0fa4-485e-8505-14e294017988/metadata

Example Response
----------------

.. code-block::

   {
       "metadata": {
           "__os_version": "Suse Linux Enterprise 12.2 64bit",
           "__image_source_type": "uds",
           "__imagetype": "gold",
           "__os_bit": "64",
           "__os_type": "Suse",
           "__isregistered": "true",
           "__image_location": "192.168.80.11:5080:pcsimsbeta:suse12.2-addx710-05-11",
           "virtual_env_type": "Ironic",
           "__platform": "Suse",
           "__support_o3s": "true"
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
