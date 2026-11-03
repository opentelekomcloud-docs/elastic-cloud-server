:original_name: en-us_topic_0134192993.html

.. _en-us_topic_0134192993:

Modifying ECS Specifications
============================

Scenarios
---------

When ECS specifications fail to meet service requirements, they can be modified, for example, by upgrading the vCPUs and memory. Certain ECSs also support changing ECS types.

Constraints
-----------

-  You can modify the ECS specifications only when the ECS is stopped.
-  The EVS disk capacity of the ECS cannot be reduced during the specifications modification.
-  ECS specifications (vCPU or memory) reduction degrades the ECS performance.
-  Certain ECSs do not support specifications modification. For details about available ECS types as well as their functions and usage on the public cloud, see section "Notes" in `Instances and Application Scenarios <https://docs.otc.t-systems.com/en-us/usermanual/ecs/en-us_topic_0035470096.html>`__.

Involved APIs
-------------

Modifying ECS specifications involves the following APIs:

-  API for modifying the specifications of an ECS
-  API for confirming ECS specifications modification
-  API for rolling back ECS specifications modification

Procedure
---------

#. Modify the ECS specifications.

   -  API

      URI format: POST /v2/{tenant_id}/servers/{server_id}/action

      For details, see section "Modifying the Specifications of an ECS" in *Elastic Cloud Server API Reference*.

   -  Request example

      .. code-block::

         {
             "resize": {
                           "flavorRef": "4"
             }
         }

   -  Response example

      N/A

#. Confirm the specifications modification.

   The ECS must be in **resized** state. That is, the **OS-EXT-STS:vm_state** value of the ECS must be **resized**.

   -  API

      URI format: POST /v2/{tenant_id}/servers/{server_id}/action

      For details, see section "Confirming ECS Specifications Modification" in *Elastic Cloud Server API Reference*.

   -  Request example

      .. code-block::

         {
            "confirmResize": null
         }

   -  Response example

      N/A

#. (Optional) Roll back the specifications modification.

   Fallback notice:

   The ECS must be in **resized** state. That is, the **OS-EXT-STS:vm_state** value of the ECS must be **resized**.

   The data modified during specifications modification will be lost after the rollback.

   -  API

      URI format: POST /v2/{tenant_id}/servers/{server_id}/action

      For details, see section "Rolling Back ECS Specifications Modification" in *Elastic Cloud Server API Reference*.

   -  Request example

      .. code-block::

         {
             "revertResize": null
         }

   -  Response example

      N/A
