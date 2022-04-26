:original_name: en-us_topic_0065817690.html

.. _en-us_topic_0065817690:

Locking an ECS
==============

Function
--------

This API is used to lock an ECS.

You are only allowed to lock your own ECSs. After ECSs are locked, you will not be able to perform management operations on them, including life cycle management, status management, NIC management, disk management, and password management.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

:ref:`Table 1 <en-us_topic_0065817690__en-us_topic_0057973175_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0065817690__en-us_topic_0057973175_table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0065817690__en-us_topic_0057973175_table18228066>` describes the request parameters.

.. _en-us_topic_0065817690__en-us_topic_0057973175_table18228066:

.. table:: **Table 2** Request parameters

   ========= ==== ========= =============
   Parameter Type Mandatory Description
   ========= ==== ========= =============
   lock      Null Yes       Locks an ECS.
   ========= ==== ========= =============

Response
--------

None

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2/{project_id}/servers/{server_id}/action
   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

.. code-block::

   {
       "lock": null
   }

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
