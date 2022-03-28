Adding an ECS to an ECS Group
=============================

Function
--------

This API is used to add an ECS to an ECS group. The system automatically deploys the newly added ECS to a host that is different from the ones accommodating other ECSs in the ECS group.

Constraints
-----------

-  The ECS to be added has been stopped.
-  Only KVM ECSs can be added.
-  Only the anti-affinity policy is supported. ECSs in the same ECS group are deployed on different hosts, improving service reliability.

URI
---

POST /v1/{project_id}/cloudservers/os-server-groups/{server_group_id}/action

`Table 1 <#enustopic0133622595table042161072218>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0133622595table042161072218:

.. table:: **Table 1** Parameter description

   =============== ========= ===========================
   Parameter       Mandatory Description
   =============== ========= ===========================
   project_id      Yes       Specifies the project ID.
   server_group_id Yes       Specifies the ECS group ID.
   =============== ========= ===========================

Request
-------

`Table 2 <#enustopic0133622595table125642531229>`__ describes the request parameters.



.. _ENUSTOPIC0133622595table125642531229:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                           |
   +=================+=================+=================+=======================================================================+
   | add_member      | Yes             | Object          | Specifies the information of the ECS to be added to an ECS group.     |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | For details, see `Table 3 <#enustopic0133622595table532112610239>`__. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+



.. _ENUSTOPIC0133622595table532112610239:

.. table:: **Table 3** **add_member** parameters

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
       "add_member": {
           "instance_uuid":"34dac9a0-c4a7-457b-bab2-e2c696e0e401"
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


