Deleting Specified ECS Metadata
===============================

Function
--------

This API is used to delete specified ECS metadata.

Constraints
-----------

An ECS must be in active, stopped, paused, or suspended state, which is specified by **OS-EXT-STS:vm_state**.

URI
---

DELETE /v2.1/{project_id}/servers/{server_id}/metadata/{key}

DELETE /v2/{project_id}/servers/{server_id}/metadata/{key}

`Table 1 <#enustopic0025560299table14014174185439>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0025560299table14014174185439:

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

None

Example Request
---------------

.. code-block::

   DELETE https://{endpoint}/v2/{project_id}/servers/{server_id}/metadata/{key}
   DELETE https://{endpoint}/v2.1/{project_id}/servers/{server_id}/metadata/{key}

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


