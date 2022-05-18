:original_name: en-us_topic_0065817691.html

.. _en-us_topic_0065817691:

Unlocking an ECS
================

Function
--------

This API is used to unlock an ECS.

After an ECS is unlocked, common users are allowed to manage the ECS.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

:ref:`Table 1 <en-us_topic_0065817691__en-us_topic_0057973176_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0065817691__en-us_topic_0057973176_table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0065817691__en-us_topic_0057973176_table65978805>` describes the request parameters.

.. _en-us_topic_0065817691__en-us_topic_0057973176_table65978805:

.. table:: **Table 2** Request parameters

   ========= ========= ==== ===============
   Parameter Mandatory Type Description
   ========= ========= ==== ===============
   unlock    Yes       Null Unlocks an ECS.
   ========= ========= ==== ===============

Response
--------

None

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/servers/{server_id}/action
   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

.. code-block::

   {
      "unlock": null
   }

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
