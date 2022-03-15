Deleting an ECS
===============

Function
--------

This API is used to delete an ECS.

Constraints
-----------

When an ECS is deleted, all NICs attached to the ECS through the OpenStack Nova API will be deleted.

URI
---

DELETE /v2.1/{project_id}/servers/{server_id}

DELETE /v2/{project_id}/servers/{server_id}

`Table 1 <#enustopic0025560296table2659898791032>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0025560296table2659898791032:

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

   DELETE https://{endpoint}/v2/{project_id}/servers/{server_id}
   DELETE https://{endpoint}/v2.1/{project_id}/servers/{server_id}

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


