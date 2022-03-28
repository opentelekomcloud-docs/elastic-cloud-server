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

`Table 1 <#enustopic0065817690enustopic0057973175table32475667>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817690enustopic0057973175table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0065817690enustopic0057973175table18228066>`__ describes the request parameters.



.. _ENUSTOPIC0065817690enustopic0057973175table18228066:

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

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


