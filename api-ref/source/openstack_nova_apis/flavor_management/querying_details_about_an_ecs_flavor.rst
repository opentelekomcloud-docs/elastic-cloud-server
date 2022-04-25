:original_name: en-us_topic_0020212659.html

.. _en-us_topic_0020212659:

Querying Details About an ECS Flavor
====================================

Function
--------

This API is used to query the details about an ECS flavor based on the flavor ID.

URI
---

GET /v2.1/{project_id}/flavors/{flavor_id}

GET /v2/{project_id}/flavors/{flavor_id}

:ref:`Table 1 <en-us_topic_0020212659__table47154420>` describes the parameters in the URI.

.. _en-us_topic_0020212659__table47154420:

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

:ref:`Table 2 <en-us_topic_0020212659__table61695723>` describes the response parameters.

.. _en-us_topic_0020212659__table61695723:

.. table:: **Table 2** Response parameters

   +-----------+--------+----------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                        |
   +===========+========+====================================================================================================+
   | flavor    | Object | Specifies the ECS flavor. For details, see :ref:`Table 3 <en-us_topic_0020212659__table20109663>`. |
   +-----------+--------+----------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212659__table20109663:

.. table:: **Table 3** **flavor** field description

   +----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter                  | Type                  | Description                                                                                                              |
   +============================+=======================+==========================================================================================================================+
   | id                         | String                | Specifies the ID of the ECS flavor.                                                                                      |
   +----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | name                       | String                | Specifies the name of the ECS flavor.                                                                                    |
   +----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | description                | String                | Describes the ECS flavor.                                                                                                |
   |                            |                       |                                                                                                                          |
   |                            |                       | This parameter is supported in microversion 2.55 and later.                                                              |
   +----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | vcpus                      | Integer               | Specifies the number of vCPUs in the ECS flavor.                                                                         |
   +----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | ram                        | Integer               | Specifies the memory size (MB) in the ECS flavor.                                                                        |
   +----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | disk                       | Integer               | Specifies the system disk size in the ECS flavor.                                                                        |
   |                            |                       |                                                                                                                          |
   |                            |                       | This parameter has not been used. Its default value is **0**.                                                            |
   +----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | swap                       | String                | Specifies the swap partition size required by the ECS flavor.                                                            |
   |                            |                       |                                                                                                                          |
   |                            |                       | This parameter has not been used. Its default value is **""**.                                                           |
   +----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | OS-FLV-EXT-DATA:ephemeral  | Integer               | Specifies the temporary disk size. This is an extended attribute.                                                        |
   |                            |                       |                                                                                                                          |
   |                            |                       | This parameter has not been used. Its default value is **0**.                                                            |
   +----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | OS-FLV-DISABLED:disabled   | Boolean               | Specifies whether the ECS flavor has been disabled. This is an extended attribute.                                       |
   |                            |                       |                                                                                                                          |
   |                            |                       | This parameter has not been used. Its default value is **false**.                                                        |
   +----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | rxtx_factor                | Float                 | Specifies the ratio of the available network bandwidth to the network hardware bandwidth of the ECS.                     |
   |                            |                       |                                                                                                                          |
   |                            |                       | This parameter has not been used. Its default value is **1.0**.                                                          |
   +----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | os-flavor-access:is_public | Boolean               | Specifies whether a flavor is available to all tenants. This is an extended attribute.                                   |
   |                            |                       |                                                                                                                          |
   |                            |                       | -  **true**: indicates that a flavor is available to all tenants.                                                        |
   |                            |                       | -  **false**: indicates that a flavor is available only to certain tenants.                                              |
   |                            |                       |                                                                                                                          |
   |                            |                       | Default value: **true**                                                                                                  |
   +----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | links                      | Array of objects      | Specifies shortcut links for ECS flavors. For details, see :ref:`Table 4 <en-us_topic_0020212659__table35514108193545>`. |
   +----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212659__table35514108193545:

.. table:: **Table 4** **links** field description

   ========= ====== =========================================
   Parameter Type   Description
   ========= ====== =========================================
   rel       String Specifies the shortcut link marker name.
   href      String Provides the corresponding shortcut link.
   ========= ====== =========================================

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/743b4c0428d94531b9f2add666642e6b/flavors/c3.2xlarge.2
   GET https://{endpoint}/v2.1/743b4c0428d94531b9f2add666642e6b/flavors/c3.2xlarge.2

Example Response
----------------

.. code-block::

   {
       "flavor": {
           "name": "c3.2xlarge.2",
           "links": [
               {
                   "href": "https://compute.region.xxx.com/v2.1/743b4c0428d94531b9f2add666642e6b/flavors/c3.2xlarge.2",
                   "rel": "self"
               },
               {
                   "href": "https://compute.region.xxx.com/743b4c0428d94531b9f2add666642e6b/flavors/c3.2xlarge.2",
                   "rel": "bookmark"
               }
           ],
           "ram": 16384,
           "OS-FLV-DISABLED:disabled": false,
           "vcpus": 8,
           "swap": "",
           "os-flavor-access:is_public": true,
           "rxtx_factor": 1,
           "OS-FLV-EXT-DATA:ephemeral": 0,
           "disk": 0,
           "id": "c3.2xlarge.2"
       }
                   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
