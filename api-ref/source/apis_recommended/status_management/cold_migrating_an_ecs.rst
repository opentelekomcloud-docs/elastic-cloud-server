Cold Migrating an ECS
=====================

Function
--------

-  An ECS deployed on a DeH can be migrated to another DeH.
-  An ECS deployed on a DeH can be migrated to a public resource pool.
-  An ECS deployed in a public resource pool can be migrated to a DeH.

Constraints
-----------

-  This API is supported by DeHs only.
-  Only a stopped ECS can be cold migrated.
-  Existing constraints of the native cold migration API are inherited.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/migrate

`Table 1 <#enustopic0132905656table29396722>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0132905656table29396722:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0132905656table6742880>`__ describes the request parameters. 

.. _ENUSTOPIC0132905656table6742880:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                        |
   +=================+=================+=================+====================================================================================================+
   | migrate         | Yes             | Object          | Specifies the ECS to be migrated. For details, see `Table 3 <#enustopic0132905656table7657338>`__. |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | When migrating an ECS from a DeH to a public resource pool, the **migrate** value is null.         |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0132905656table7657338:

.. table:: **Table 3** **migrate** field description

   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                       |
   +===================+=================+=================+===================================================================================================================================+
   | dedicated_host_id | No              | String          | Specifies the DeH ID.                                                                                                             |
   |                   |                 |                 |                                                                                                                                   |
   |                   |                 |                 | This parameter takes effect when an ECS is migrated from a public resource pool to a DeH or when an ECS is migrated between DeHs. |
   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+

Response
--------

See `Responses (Task) <../../common_parameters/task_request_result/responses_task.html>`__.

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/migrate

.. code-block::

   {
       "migrate": {
           "dedicated_host_id": "459a2b9d-804a-4745-ab19-a113bb1b4ddc"
       }
   }
   Or
   {
       "migrate": null
   }

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


