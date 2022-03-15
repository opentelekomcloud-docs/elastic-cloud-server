Modifying the Specifications of an ECS
======================================

Function
--------

This API is used to modify the specifications of an ECS.

For a running ECS, the system will automatically stop the ECS, copy the ECS data to the target node, which can be the source node, and then restart the ECS.

This API supports automatic rollback if the underlying resources are insufficient.

This API must be used with the API for verifying ECS specifications modification (POST /v2.1/{project_id}/servers/{server_id}/action) or the API for rolling back ECS specifications modification (POST /v2.1/{project_id}/servers/{server_id}/action) if an ECS is detected to be in **VERIFY_RESIZE** state and its **OS-EXT-STS:vm_state** is **RESIZED**.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

`Table 1 <#enustopic0028714261table3588765216457>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0028714261table3588765216457:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0028714261table2242889516457>`__ describes the request parameters. 

.. _ENUSTOPIC0028714261table2242889516457:

.. table:: **Table 2** Request parameters

   ========= ========= ====== ===================================
   Parameter Mandatory Type   Description
   ========= ========= ====== ===================================
   flavorRef Yes       String Specifies the new flavor ID or URI.
   ========= ========= ====== ===================================

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
       "resize" : {
           "flavorRef" : "s6.medium.2"
       }
   }

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


