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
-  Downgrading ECS specifications (vCPU or memory) deteriorates the ECS performance.
-  Certain ECSs do not support specifications modification. For details about available ECS types as well as their functions and usage on the public cloud, see section "Notes" in `ECS Specifications <https://docs.otc.t-systems.com/en-us/usermanual/ecs/en-us_topic_0132345719.html>`__.

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

      URI format: POST /v2/{project_id}/servers/{server_id}/action

      For details, see section "Modifying the Specifications of an ECS" in *Elastic Cloud Server API Reference*.

   -  Request example

      POST https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/servers/11e8f727-d439-4ed1-b3b8-33f46c0379c4/action

      Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

      Body:

      .. code-block::

         {
             "resize": {
                           "flavorRef": "c3.4xlarge.2"
             }
         }

   -  Response example

      N/A

#. Confirm the specifications modification.

   The ECS status must be **resized**. That is, the **OS-EXT-STS:vm_state** value of the ECS must be **resized**.

   -  API

      URI format: POST /v2/{project_id}/servers/{server_id}/action

      For details, see section "Confirming the Specifications Modification of an ECS" in *Elastic Cloud Server API Reference*.

   -  Request example

      POST https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/servers/11e8f727-d439-4ed1-b3b8-33f46c0379c4/action

      Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

      Body:

      .. code-block::

         {
            "confirmResize": null
         }

   -  Response example

      N/A

#. (Optional) Roll back the specifications modification.

   Fallback notice:

   The ECS status must be **resized**. That is, the **OS-EXT-STS:vm_state** value of the ECS must be **resized**.

   The data modified during specifications modification will be lost after the rollback.

   -  API

      URI format: POST /v2/{project_id}/servers/{server_id}/action

      For details, see section "Rolling Back ECS Specifications Modification" in *Elastic Cloud Server API Reference*.

   -  Request example

      POST https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/servers/11e8f727-d439-4ed1-b3b8-33f46c0379c4/action

      Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

      Body:

      .. code-block::

         {
             "revertResize": null
         }

   -  Response example

      N/A
