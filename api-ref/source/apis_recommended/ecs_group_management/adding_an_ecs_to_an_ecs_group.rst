.. _en-us_topic_0133622595:

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

:ref:`Table 1 <en-us_topic_0133622595__table042161072218>` describes the parameters in the URI.

.. _en-us_topic_0133622595__table042161072218:

.. table:: **Table 1** Parameter description

   =============== ========= ===========================
   Parameter       Mandatory Description
   =============== ========= ===========================
   project_id      Yes       Specifies the project ID.
   server_group_id Yes       Specifies the ECS group ID.
   =============== ========= ===========================

Request
-------

:ref:`Table 2 <en-us_topic_0133622595__table125642531229>` describes the request parameters.

.. _en-us_topic_0133622595__table125642531229:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                  |
   +=================+=================+=================+==============================================================================+
   | add_member      | Yes             | Object          | Specifies the information of the ECS to be added to an ECS group.            |
   |                 |                 |                 |                                                                              |
   |                 |                 |                 | For details, see :ref:`Table 3 <en-us_topic_0133622595__table532112610239>`. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+

.. _en-us_topic_0133622595__table532112610239:

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
