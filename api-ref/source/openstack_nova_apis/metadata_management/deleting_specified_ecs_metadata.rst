.. _en-us_topic_0025560299:

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

:ref:`Table 1 <en-us_topic_0025560299__table14014174185439>` describes the parameters in the URI.

.. _en-us_topic_0025560299__table14014174185439:

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
