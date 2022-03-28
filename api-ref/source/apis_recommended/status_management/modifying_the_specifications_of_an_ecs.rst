Modifying the Specifications of an ECS
======================================

Function
--------

ECS specifications can be modified, for example, upgrading the vCPUs and memory, to meet service requirements. This API is used to modify ECS specifications.

An ECS flavor cannot be changed to certain flavors. For details, see `Querying the Target Flavors to Which an ECS Flavor Can Be Changed <../../apis_recommended/flavor_management/querying_the_target_flavors_to_which_an_ecs_flavor_can_be_changed.html>`__.

Constraints
-----------

-  You can modify the ECS specifications only when the ECS is stopped.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/resize

`Table 1 <#enustopic0020212653table29396722>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212653table29396722:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0020212653table6742880>`__ describes the request parameters. 

.. _ENUSTOPIC0020212653table6742880:

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                            |
   +===========+===========+========+========================================================================================================================+
   | resize    | Yes       | Object | Specifies the operation to modify ECS specifications. For details, see `Table 3 <#enustopic0020212653table7657338>`__. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212653table7657338:

.. table:: **Table 3** **resize** field description

   +-----------+-----------+--------+------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                |
   +===========+===========+========+============================================================+
   | flavorRef | Yes       | String | Specifies the flavor ID of the ECS after the modification. |
   +-----------+-----------+--------+------------------------------------------------------------+

Response
--------

See `Responses (Task) <../../common_parameters/task_request_result/responses_task.html>`__.

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/resize

.. code-block::

   {
   "resize": {
           "flavorRef": "c3.15xlarge.2"
       }
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


