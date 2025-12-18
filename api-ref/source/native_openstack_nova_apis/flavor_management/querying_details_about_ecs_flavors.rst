:original_name: en-us_topic_0020212658.html

.. _en-us_topic_0020212658:

Querying Details About ECS Flavors
==================================

Function
--------

This API is used to query details about ECS flavors.

URI
---

GET /v2.1/{project_id}/flavors/detail?minDisk={minDisk}&minRam={minRam}&sort_key={sort_key}&sort_dir={sort_dir}

GET /v2/{project_id}/flavors/detail?minDisk={minDisk}&minRam={minRam}&sort_key={sort_key}&sort_dir={sort_dir}

:ref:`Table 1 <en-us_topic_0020212658__table46110007>` describes the parameters in the URI.

.. _en-us_topic_0020212658__table46110007:

.. table:: **Table 1** Path parameters

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

.. table:: **Table 2** Query parameters

   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                      |
   +===========+===========+========+==================================================================================================================================================================================+
   | minDisk   | No        | String | Specifies the minimum disk size in GiB. Only the ECSs with a disk size greater than or equal to the minimum size can be queried.                                                 |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | minRam    | No        | String | Specifies the minimum memory size in MiB. Only the ECSs with the memory size greater than or equal to the minimum size can be queried.                                           |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_key  | No        | String | Indicates a sorting field, the default value of which is **flavorid**. The value of this parameter can also be **name**, **memory_mb**, **vcpus**, **root_gb**, or **flavorid**. |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_dir  | No        | String | Specifies the ascending (**asc**) or descending (**desc**) sorting. The default value is **asc**.                                                                                |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 3 <en-us_topic_0020212658__table23477058>` describes the response parameters.

.. _en-us_topic_0020212658__table23477058:

.. table:: **Table 3** Response parameters

   +---------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type             | Description                                                                                                                                          |
   +===============+==================+======================================================================================================================================================+
   | flavors       | Array of objects | Specifies ECS flavors. For details, see :ref:`Table 4 <en-us_topic_0020212658__table13194498>`.                                                      |
   +---------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavors_links | Array of objects | Specifies data links for querying the next pages in pagination query. For details, see :ref:`Table 5 <en-us_topic_0020212658__table15913898194628>`. |
   +---------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212658__table13194498:

.. table:: **Table 4** **flavors** field description

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
   | ram                        | Integer               | Specifies the memory size (MiB) in the ECS flavor.                                                                       |
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
   | links                      | Array of objects      | Specifies shortcut links for ECS flavors. For details, see :ref:`Table 5 <en-us_topic_0020212658__table15913898194628>`. |
   +----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212658__table15913898194628:

.. table:: **Table 5** **links** field description

   ========= ====== =========================================
   Parameter Type   Description
   ========= ====== =========================================
   rel       String Specifies the shortcut link marker name.
   href      String Provides the corresponding shortcut link.
   ========= ====== =========================================

Example Request
---------------

Query details about ECS flavors.

.. code-block:: text

   GET https://{endpoint}/v2/743b4c0428d94531b9f2add666642e6b/flavors/detail
   GET https://{endpoint}/v2.1/743b4c0428d94531b9f2add666642e6b/flavors/detail

Example Response
----------------

.. code-block::

   {
       "flavors": [
           {
               "name": "c3.2xlarge.2",
               "links": [
                   {
                       "href": "https://compute.region.example.com/v2.1/743b4c0428d94531b9f2add666642e6b/flavors/c3.2xlarge.2",
                       "rel": "self"
                   },
                   {
                       "href": "https://compute.region.example.com/743b4c0428d94531b9f2add666642e6b/flavors/c3.2xlarge.2",
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
           },
           {
               "name": "c3.2xlarge.4",
               "links": [
                   {
                       "href": "https://compute.region.example.com/v2.1/743b4c0428d94531b9f2add666642e6b/flavors/c3.2xlarge.4",
                       "rel": "self"
                   },
                   {
                       "href": "https://compute.region.example.com/743b4c0428d94531b9f2add666642e6b/flavors/c3.2xlarge.4",
                       "rel": "bookmark"
                   }
               ],
               "ram": 32768,
               "OS-FLV-DISABLED:disabled": false,
               "vcpus": 8,
               "swap": "",
               "os-flavor-access:is_public": true,
               "rxtx_factor": 1,
               "OS-FLV-EXT-DATA:ephemeral": 0,
               "disk": 0,
               "id": "c3.2xlarge.4"
           }
       ]
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
