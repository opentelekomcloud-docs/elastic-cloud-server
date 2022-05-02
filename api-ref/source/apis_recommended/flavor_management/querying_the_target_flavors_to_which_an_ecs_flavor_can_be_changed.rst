:original_name: en-us_topic_0110472767.html

.. _en-us_topic_0110472767:

Querying the Target Flavors to Which an ECS Flavor Can Be Changed
=================================================================

Function
--------

An ECS flavor cannot be changed to certain flavors. This API is used to query the target flavors to which a specified ECS flavor can be changed.

URI
---

GET /v2.1/{project_id}/resize_flavors?instance_uuid={instance_uuid}&source_flavor_id={source_flavor_id}&source_flavor_name={source_flavor_name}&sort_key={sort_key}&sort_dir={sort_dir}&limit={limit}&marker={marker}

:ref:`Table 1 <en-us_topic_0110472767__table46110007>` describes the parameters in the URI.

.. _en-us_topic_0110472767__table46110007:

.. table:: **Table 1** Path parameters

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

.. note::

   One of the **instance_uuid**, **source_flavor_id**, and **source_flavor_name** parameters must be configured. If multiple parameters are configured, the system processes the **instance_uuid**, **source_flavor_id**, and **source_flavor_name** parameters in descending order by default.

:ref:`Table 2 <en-us_topic_0110472767__table96861454162513>` describes the query parameters.

.. _en-us_topic_0110472767__table96861454162513:

.. table:: **Table 2** Query parameters

   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                               |
   +====================+=================+=================+===========================================================================================================+
   | instance_uuid      | No              | String          | Specifies the ID, in UUID format, of the target ECS.                                                      |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | source_flavor_id   | No              | String          | Specifies the source flavor ID.                                                                           |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | source_flavor_name | No              | String          | Specifies the source flavor name.                                                                         |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | sort_key           | No              | String          | Indicates the field for sorting.                                                                          |
   |                    |                 |                 |                                                                                                           |
   |                    |                 |                 | Options:                                                                                                  |
   |                    |                 |                 |                                                                                                           |
   |                    |                 |                 | -  **flavorid**: indicates the flavor ID. The default value is **flavorid**.                              |
   |                    |                 |                 | -  **name**: indicates the flavor name.                                                                   |
   |                    |                 |                 | -  **memory_mb**: indicates the memory size.                                                              |
   |                    |                 |                 | -  **vcpus**: indicates the number of vCPUs.                                                              |
   |                    |                 |                 | -  **root_gb**: indicates the system disk size.                                                           |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | sort_dir           | No              | String          | Specifies the ascending or descending sorting.                                                            |
   |                    |                 |                 |                                                                                                           |
   |                    |                 |                 | Options:                                                                                                  |
   |                    |                 |                 |                                                                                                           |
   |                    |                 |                 | -  **asc**: indicates the ascending order.                                                                |
   |                    |                 |                 | -  **desc**: indicates the descending order.                                                              |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | limit              | No              | Integer         | Specifies the maximum number of flavors that can be displayed on one page. The default value is **1000**. |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | marker             | No              | String          | Uses the ID of the last flavor on one page as the paging marker.                                          |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 3 <en-us_topic_0110472767__table23477058>` describes the response parameters.

.. _en-us_topic_0110472767__table23477058:

.. table:: **Table 3** Response parameters

   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                    |
   +=================+=================+==================+================================================================================+
   | flavors         | Yes             | Array of objects | Specifies ECS flavors.                                                         |
   |                 |                 |                  |                                                                                |
   |                 |                 |                  | For details, see :ref:`Table 4 <en-us_topic_0110472767__table68941918122818>`. |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------+

.. _en-us_topic_0110472767__table68941918122818:

.. table:: **Table 4** **flavors** field description

   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+
   | Parameter                  | Mandatory       | Type             | Description                                                                              |
   +============================+=================+==================+==========================================================================================+
   | id                         | Yes             | String           | Specifies the ECS flavor ID.                                                             |
   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+
   | name                       | Yes             | String           | Specifies the name of the ECS flavor.                                                    |
   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+
   | vcpus                      | Yes             | Integer          | Specifies the number of vCPUs in the ECS flavor.                                         |
   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+
   | ram                        | Yes             | Integer          | Specifies the memory size (MB) in the ECS flavor.                                        |
   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+
   | disk                       | Yes             | Integer          | Specifies the system disk size in the ECS flavor.                                        |
   |                            |                 |                  |                                                                                          |
   |                            |                 |                  | This parameter has not been used. Its default value is **0**.                            |
   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+
   | swap                       | No              | String           | Specifies the swap partition size required by the ECS flavor.                            |
   |                            |                 |                  |                                                                                          |
   |                            |                 |                  | This parameter has not been used. Its default value is **""**.                           |
   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+
   | OS-FLV-EXT-DATA:ephemeral  | Yes             | Integer          | Specifies the temporary disk size. This is an extended attribute.                        |
   |                            |                 |                  |                                                                                          |
   |                            |                 |                  | This parameter has not been used. Its default value is **0**.                            |
   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+
   | OS-FLV-DISABLED:disabled   | Yes             | Boolean          | This is an extended attribute, specifying whether a flavor is available.                 |
   |                            |                 |                  |                                                                                          |
   |                            |                 |                  | -  **true**: indicates that a flavor is available.                                       |
   |                            |                 |                  | -  **false**: indicates that a flavor is unavailable.                                    |
   |                            |                 |                  |                                                                                          |
   |                            |                 |                  | .. note::                                                                                |
   |                            |                 |                  |                                                                                          |
   |                            |                 |                  |    This parameter is not used.                                                           |
   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+
   | rxtx_factor                | Yes             | Float            | This is an extended attribute.                                                           |
   |                            |                 |                  |                                                                                          |
   |                            |                 |                  | .. note::                                                                                |
   |                            |                 |                  |                                                                                          |
   |                            |                 |                  |    This parameter is not used.                                                           |
   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+
   | rxtx_quota                 | Yes             | String           | Specifies the software constraints of the network bandwidth that can be used by the ECS. |
   |                            |                 |                  |                                                                                          |
   |                            |                 |                  | This parameter has not been used. Its default value is **null**.                         |
   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+
   | rxtx_cap                   | Yes             | String           | Specifies the hardware constraints of the network bandwidth that can be used by the ECS. |
   |                            |                 |                  |                                                                                          |
   |                            |                 |                  | This parameter has not been used. Its default value is **null**.                         |
   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+
   | os-flavor-access:is_public | Yes             | Boolean          | Specifies whether a flavor is available to all tenants. This is an extended attribute.   |
   |                            |                 |                  |                                                                                          |
   |                            |                 |                  | -  **true**: indicates that a flavor is available to all tenants.                        |
   |                            |                 |                  | -  **false**: indicates that a flavor is available only to certain tenants.              |
   |                            |                 |                  |                                                                                          |
   |                            |                 |                  | Default value: **true**                                                                  |
   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+
   | links                      | Yes             | Array of objects | Specifies the shortcut link of the ECS flavor.                                           |
   |                            |                 |                  |                                                                                          |
   |                            |                 |                  | For details, see :ref:`Table 5 <en-us_topic_0110472767__table15913898194628>`.           |
   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+
   | extra_specs                | Yes             | Array of objects | Specifies the extended field of the ECS specifications.                                  |
   |                            |                 |                  |                                                                                          |
   |                            |                 |                  | For details, see :ref:`Table 6 <en-us_topic_0020212656__table59078165>`.                 |
   +----------------------------+-----------------+------------------+------------------------------------------------------------------------------------------+

.. _en-us_topic_0110472767__table15913898194628:

.. table:: **Table 5** **links** field description

   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                        |
   +===========+===========+========+====================================================================================================+
   | rel       | Yes       | String | Specifies the shortcut link marker name.                                                           |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------+
   | href      | Yes       | String | Specifies the shortcut link.                                                                       |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------+
   | type      | Yes       | String | Specifies the shortcut link type. This parameter has not been used. Its default value is **null**. |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/cloudservers/resize_flavors?source_flavor_id=c3.xlarge.2

Example Response
----------------

.. code-block::

   {
       "flavors": [
           {
               "id": "c3.15xlarge.2",
               "name": "c3.15xlarge.2",
               "vcpus": "60",
               "ram": 131072,
               "disk": "0",
               "swap": "",
               "links": [
                   {
                       "rel": "self",
                       "href": "https://compute-ext.region.xxx.com/v1.0/743b4c0428d94531b9f2add666642e6b/flavors/c3.15xlarge.2",
                       "type": null
                   },
                   {
                       "rel": "bookmark",
                       "href": "https://compute-ext.region.xxx.com/743b4c0428d94531b9f2add666642e6b/flavors/c3.15xlarge.2",
                       "type": null
                   }
               ],
               "OS-FLV-EXT-DATA:ephemeral": 0,
               "rxtx_factor": 1,
               "OS-FLV-DISABLED:disabled": false,
               "rxtx_quota": null,
               "rxtx_cap": null,
               "os-flavor-access:is_public": true,
               "extra_specs": {
                   "ecs:virtualization_env_types": "CloudCompute",
                   "ecs:generation": "c3",
                   "ecs:performancetype": "computingv3",
                   "resource_type": "IOoptimizedC3_2"
                }
           }
       ]
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
