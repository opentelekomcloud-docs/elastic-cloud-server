:original_name: en-us_topic_0028714261.html

.. _en-us_topic_0028714261:

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

:ref:`Table 1 <en-us_topic_0028714261__table3588765216457>` describes the parameters in the URI.

.. _en-us_topic_0028714261__table3588765216457:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0028714261__table3529164221216>` describes the request parameters.

.. _en-us_topic_0028714261__table3529164221216:

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                      |
   +===========+===========+========+==================================================================================================================+
   | resize    | Yes       | Object | For details about how to modify specifications, see :ref:`Table 3 <en-us_topic_0028714261__table2242889516457>`. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0028714261__table2242889516457:

.. table:: **Table 3** **resize** field description

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

Change the flavor of a specified ECS to **s3.medium.2**.

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/servers/{server_id}/action
   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

   {
       "resize" : {
           "flavorRef" : "s3.medium.2"
       }
   }

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
