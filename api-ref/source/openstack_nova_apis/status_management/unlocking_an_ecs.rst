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

`Table 1 <#enustopic0065817691enustopic0057973176table32475667>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817691enustopic0057973176table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0065817691enustopic0057973176table65978805>`__ describes the request parameters.



.. _ENUSTOPIC0065817691enustopic0057973176table65978805:

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

.. code-block::

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

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


