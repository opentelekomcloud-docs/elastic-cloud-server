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

   +-----------------------+-----------------------+---------------------------+
   | Parameter             | Mandatory             | Description               |
   +=======================+=======================+===========================+
   | project_id            | Yes                   | **Definition**            |
   |                       |                       |                           |
   |                       |                       | Specifies the project ID. |
   |                       |                       |                           |
   |                       |                       | **Constraints**           |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Range**                 |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Default Value**         |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   +-----------------------+-----------------------+---------------------------+

.. note::

   One of the **instance_uuid**, **source_flavor_id**, and **source_flavor_name** parameters must be configured. If multiple parameters are configured, the system processes the **instance_uuid**, **source_flavor_id**, and **source_flavor_name** parameters in descending order by default.

:ref:`Table 2 <en-us_topic_0110472767__table96861454162513>` describes the request parameters.

.. _en-us_topic_0110472767__table96861454162513:

.. table:: **Table 2** Query parameters

   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                             |
   +====================+=================+=================+=========================================================================+
   | instance_uuid      | No              | String          | **Definition**                                                          |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | Specifies the ID, in UUID format, of the target ECS.                    |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Constraints**                                                         |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Range**                                                               |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Default Value**                                                       |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------+
   | source_flavor_id   | No              | String          | **Definition**                                                          |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | Specifies the source flavor ID.                                         |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Constraints**                                                         |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Range**                                                               |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Default Value**                                                       |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------+
   | source_flavor_name | No              | String          | **Definition**                                                          |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | Specifies the source flavor name.                                       |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Constraints**                                                         |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Range**                                                               |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Default Value**                                                       |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------+
   | sort_key           | No              | String          | **Definition**                                                          |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | Indicates the field for sorting.                                        |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Constraints**                                                         |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Range**                                                               |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | -  **flavorid**: indicates the flavor ID.                               |
   |                    |                 |                 | -  **name**: indicates the flavor name.                                 |
   |                    |                 |                 | -  **memory_mb**: indicates the memory size.                            |
   |                    |                 |                 | -  **vcpus**: indicates the number of vCPUs.                            |
   |                    |                 |                 | -  **root_gb**: indicates the system disk size.                         |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Default Value**                                                       |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | flavorid                                                                |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------+
   | sort_dir           | No              | String          | **Definition**                                                          |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | Specifies the ascending or descending sorting order.                    |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Constraints**                                                         |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Range**                                                               |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | -  **asc**: indicates the ascending order.                              |
   |                    |                 |                 | -  **desc**: indicates the descending order.                            |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Default Value**                                                       |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | asc                                                                     |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------+
   | limit              | No              | Integer         | **Definition**                                                          |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | Specifies the maximum number of flavors that can be displayed per page. |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Constraints**                                                         |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Range**                                                               |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Default Value**                                                       |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | 1000                                                                    |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------+
   | marker             | No              | String          | **Definition**                                                          |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | Uses the ID of the last flavor on one page as the paging marker.        |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Constraints**                                                         |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Range**                                                               |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | **Default Value**                                                       |
   |                    |                 |                 |                                                                         |
   |                    |                 |                 | N/A                                                                     |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 3 <en-us_topic_0110472767__table23477058>` describes the response parameters.

.. _en-us_topic_0110472767__table23477058:

.. table:: **Table 3** Response parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                    |
   +=======================+=======================+================================================================================+
   | flavors               | Array of objects      | **Definition**                                                                 |
   |                       |                       |                                                                                |
   |                       |                       | Specifies ECS flavors.                                                         |
   |                       |                       |                                                                                |
   |                       |                       | For details, see :ref:`Table 4 <en-us_topic_0110472767__table68941918122818>`. |
   |                       |                       |                                                                                |
   |                       |                       | **Range**                                                                      |
   |                       |                       |                                                                                |
   |                       |                       | N/A                                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------+

.. _en-us_topic_0110472767__table68941918122818:

.. table:: **Table 4** **flavors** field description

   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | Parameter                  | Type                  | Description                                                                              |
   +============================+=======================+==========================================================================================+
   | id                         | String                | **Definition**                                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | Specifies the ECS flavor ID.                                                             |
   |                            |                       |                                                                                          |
   |                            |                       | **Range**                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       | N/A                                                                                      |
   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | name                       | String                | **Definition**                                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | Specifies the name of the ECS flavor.                                                    |
   |                            |                       |                                                                                          |
   |                            |                       | **Range**                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       | N/A                                                                                      |
   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | vcpus                      | Integer               | **Definition**                                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | Specifies the number of vCPUs in the ECS flavor.                                         |
   |                            |                       |                                                                                          |
   |                            |                       | **Range**                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       | N/A                                                                                      |
   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | ram                        | Integer               | **Definition**                                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | Specifies the memory size (MiB) in the ECS flavor.                                       |
   |                            |                       |                                                                                          |
   |                            |                       | **Range**                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       | N/A                                                                                      |
   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | disk                       | Integer               | **Definition**                                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | Specifies the system disk size in the ECS flavor.                                        |
   |                            |                       |                                                                                          |
   |                            |                       | This parameter has not been used. Its default value is **0**.                            |
   |                            |                       |                                                                                          |
   |                            |                       | **Range**                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       | N/A                                                                                      |
   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | swap                       | String                | **Definition**                                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | Specifies the swap partition size required by the ECS flavor.                            |
   |                            |                       |                                                                                          |
   |                            |                       | This parameter has not been used. Its default value is **""**.                           |
   |                            |                       |                                                                                          |
   |                            |                       | **Range**                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       | N/A                                                                                      |
   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | OS-FLV-EXT-DATA:ephemeral  | Integer               | **Definition**                                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | Specifies the temporary disk size. This is an extended attribute.                        |
   |                            |                       |                                                                                          |
   |                            |                       | This parameter has not been used. Its default value is **0**.                            |
   |                            |                       |                                                                                          |
   |                            |                       | **Range**                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       | N/A                                                                                      |
   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | OS-FLV-DISABLED:disabled   | Boolean               | **Definition**                                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | This is an extended attribute, specifying whether a flavor is available.                 |
   |                            |                       |                                                                                          |
   |                            |                       | .. note::                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       |    This parameter is not used.                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | **Range**                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       | -  **true**: indicates that a flavor is unavailable.                                     |
   |                            |                       | -  **false**: indicates that a flavor is available.                                      |
   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | rxtx_factor                | Float                 | **Definition**                                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | This is an extended attribute.                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | .. note::                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       |    This parameter is not used.                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | **Range**                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       | N/A                                                                                      |
   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | rxtx_quota                 | String                | **Definition**                                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | Specifies the software constraints of the network bandwidth that can be used by the ECS. |
   |                            |                       |                                                                                          |
   |                            |                       | This parameter has not been used. Its default value is **null**.                         |
   |                            |                       |                                                                                          |
   |                            |                       | **Range**                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       | N/A                                                                                      |
   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | rxtx_cap                   | String                | **Definition**                                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | Specifies the hardware constraints of the network bandwidth that can be used by the ECS. |
   |                            |                       |                                                                                          |
   |                            |                       | This parameter has not been used. Its default value is **null**.                         |
   |                            |                       |                                                                                          |
   |                            |                       | **Range**                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       | N/A                                                                                      |
   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | os-flavor-access:is_public | Boolean               | **Definition**                                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | Specifies whether a flavor is available to all tenants. This is an extended attribute.   |
   |                            |                       |                                                                                          |
   |                            |                       | Default value: **true**                                                                  |
   |                            |                       |                                                                                          |
   |                            |                       | **Range**                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       | -  **true**: indicates that a flavor is available to all tenants.                        |
   |                            |                       | -  **false**: indicates that a flavor is available only to certain tenants.              |
   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | links                      | Array of objects      | **Definition**                                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | Specifies the shortcut link of the ECS flavor.                                           |
   |                            |                       |                                                                                          |
   |                            |                       | For details, see :ref:`Table 5 <en-us_topic_0110472767__table15913898194628>`.           |
   |                            |                       |                                                                                          |
   |                            |                       | **Range**                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       | N/A                                                                                      |
   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | extra_specs                | Array of objects      | **Definition**                                                                           |
   |                            |                       |                                                                                          |
   |                            |                       | Specifies the extended field of the ECS specifications.                                  |
   |                            |                       |                                                                                          |
   |                            |                       | For details, see :ref:`Table 6 <en-us_topic_0020212656__table59078165>`.                 |
   |                            |                       |                                                                                          |
   |                            |                       | **Range**                                                                                |
   |                            |                       |                                                                                          |
   |                            |                       | N/A                                                                                      |
   +----------------------------+-----------------------+------------------------------------------------------------------------------------------+

.. _en-us_topic_0110472767__table15913898194628:

.. table:: **Table 5** **links** field description

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                        |
   +=================+=================+=================+====================================================================================================+
   | rel             | Yes             | String          | **Definition**                                                                                     |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | Specifies the shortcut link marker name.                                                           |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | **Range**                                                                                          |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | N/A                                                                                                |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | href            | Yes             | String          | **Definition**                                                                                     |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | Specifies the shortcut link.                                                                       |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | **Range**                                                                                          |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | N/A                                                                                                |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | type            | Yes             | String          | **Definition**                                                                                     |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | Specifies the shortcut link type. This parameter has not been used. Its default value is **null**. |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | **Range**                                                                                          |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | N/A                                                                                                |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+

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
                       "href": "https://compute-ext.region.example.com/v1.0/743b4c0428d94531b9f2add666642e6b/flavors/c3.15xlarge.2",
                       "type": null
                   },
                   {
                       "rel": "bookmark",
                       "href": "https://compute-ext.region.example.com/743b4c0428d94531b9f2add666642e6b/flavors/c3.15xlarge.2",
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
