Removing an ECS from an ECS Group
=================================

Function
--------

This API is used to remove an ECS from an ECS group. After being removed, the anti-affinity policy will not take effect on this ECS and other ECSs in the same ECS group.

Constraints
-----------

Only the anti-affinity policy is supported. ECSs in the same ECS group are deployed on different hosts, improving service reliability.

URI
---

POST /v1/{project_id}/cloudservers/os-server-groups/{server_group_id}/action

`Table 1 <#enustopic0133622596table10769113472410>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0133622596table10769113472410:

.. table:: **Table 1** Parameter description

   =============== ========= ===========================
   Parameter       Mandatory Description
   =============== ========= ===========================
   project_id      Yes       Specifies the project ID.
   server_group_id Yes       Specifies the ECS group ID.
   =============== ========= ===========================

Request
-------

`Table 2 <#enustopic0133622596table45526613251>`__ describes the request parameters.



.. _ENUSTOPIC0133622596table45526613251:

.. table:: **Table 2** Request parameters

   +---------------+-----------+--------+-----------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                           |
   +===============+===========+========+=======================================================================+
   | remove_member | Yes       | Object | Specifies the information of the ECS to be removed from an ECS group. |
   +---------------+-----------+--------+-----------------------------------------------------------------------+



.. _ENUSTOPIC0133622596enustopic0057973153table19917766:

.. table:: **Table 3** **remove_member** parameters

   ============= ========= ====== =======================
   Parameter     Mandatory Type   Description
   ============= ========= ====== =======================
   instance_uuid Yes       String Specifies the ECS UUID.
   ============= ========= ====== =======================

Response
--------

None

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v1/{project_id}/cloudservers/os-server-groups/{server_group_id}/action

.. code-block::

   {
       "remove_member": {
           "instance_uuid": "34dac9a0-c4a7-457b-bab2-e2c696e0e401"
       }
   }

Example Response
----------------

Status code 200, indicating that the operation is successful

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


