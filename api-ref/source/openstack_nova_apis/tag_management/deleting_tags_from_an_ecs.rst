.. _en-us_topic_0065820824:

Deleting Tags from an ECS
=========================

This API is used to delete all tags of an ECS.

You are required to use the HTTP header **X-OpenStack-Nova-API-Version: 2.26** to specify the microversion on the client.

URI
---

DELETE /v2.1/{project_id}/servers/{server_id}/tags

:ref:`Table 1 <en-us_topic_0065820824__en-us_topic_0057972839_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0065820824__en-us_topic_0057972839_table32475667:

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

None

Example Request
---------------

.. code-block::

   DELETE https://{endpoint}/v2.1/{project_id}/servers/{server_id}/tags

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
