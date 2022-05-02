:original_name: en-us_topic_0065817706.html

.. _en-us_topic_0065817706:

Querying the extra_specs Value for an ECS Flavor
================================================

Function
--------

This API is used to query the **extra_specs** value for a specified ECS flavor.

URI
---

GET /v2.1/{project_id}/flavors/{flavor_id}/os-extra_specs

GET /v2/{project_id}/flavors/{flavor_id}/os-extra_specs

:ref:`Table 1 <en-us_topic_0065817706__en-us_topic_0057973064_table47154420>` describes the parameters in the URI.

.. _en-us_topic_0065817706__en-us_topic_0057973064_table47154420:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   flavors_id Yes       Specifies the flavor ID.
   ========== ========= =========================

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0065817706__en-us_topic_0057973064_table28168569>` describes the response parameters.

.. _en-us_topic_0065817706__en-us_topic_0057973064_table28168569:

.. table:: **Table 2** Response parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================================+
   | extra_specs           | Map<String,String>    | Specifies the key-value pair of an ECS flavor.                                                                                                           |
   |                       |                       |                                                                                                                                                          |
   |                       |                       | For details about the returned fields, see the **os_extra_specs** field description in "Querying Details About Flavors and Extended Flavor Information". |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v2/743b4c0428d94531b9f2add666642e6b/flavors/c3.2xlarge.2/os-extra_specs
   GET https://{endpoint}/v2.1/743b4c0428d94531b9f2add666642e6b/flavors/c3.2xlarge.2/os-extra_specs

Example Response
----------------

.. code-block::

   {
       "extra_specs": {
           "ecs:performancetype": "computingv3",
           "resource_type": "IOoptimizedC3_2"
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
