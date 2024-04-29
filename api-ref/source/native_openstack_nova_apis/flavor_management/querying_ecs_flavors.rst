:original_name: en-us_topic_0065817705.html

.. _en-us_topic_0065817705:

Querying ECS Flavors
====================

Function
--------

This API is used to query available ECS flavors. After receiving the request, Nova uses nova-api to view the flavors from the database.

URI
---

GET /v2.1/{project_id}/flavors?minDisk={minDisk}&minRam={minRam}&sort_key={sort_key}&sort_dir={sort_dir}

GET /v2/{project_id}/flavors?minDisk={minDisk}&minRam={minRam}&sort_key={sort_key}&sort_dir={sort_dir}

:ref:`Table 1 <en-us_topic_0065817705__en-us_topic_0057973030_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0065817705__en-us_topic_0057973030_table32475667:

.. table:: **Table 1** Path parameters

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Parameters in the following table can be used as URI parameters to filter query results. Usage: /v2/{project_id}/flavors?minDisk={minDisk}&minRam={minRam}

:ref:`Table 2 <en-us_topic_0065817705__en-us_topic_0057973030_table714692>` describes the query parameters.

.. _en-us_topic_0065817705__en-us_topic_0057973030_table714692:

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================================================+
   | minDisk         | No              | Integer         | Specifies the minimum disk specification in the unit of GB. Only the ECSs with the disk specification greater than or equal to the minimum specification can be queried. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | minRam          | No              | Integer         | Specifies the minimum RAM in the unit of MB. Only the ECSs with the RAM specification greater than or equal to the minimum specification can be queried.                 |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_key        | No              | String          | Indicates a sorting field, the default value of which is **flavorid**.                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                          |
   |                 |                 |                 | The value of this parameter can also be **name**, **memory_mb**, **vcpus**, **root_gb**, or **flavorid**.                                                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_dir        | No              | String          | Specifies the ascending (**asc**) or descending (**desc**) sorting. The default value is **asc**.                                                                        |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 4 <en-us_topic_0065817705__en-us_topic_0057973030_table56222540>` describes the response parameters.

.. table:: **Table 3** Response parameters

   +---------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type             | Description                                                                                                                                                                 |
   +===============+==================+=============================================================================================================================================================================+
   | flavors       | Array of objects | Specifies ECS flavors. For details, see :ref:`Table 4 <en-us_topic_0065817705__en-us_topic_0057973030_table56222540>`.                                                      |
   +---------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavors_links | Array of objects | Specifies data links for querying the next pages in pagination query. For details, see :ref:`Table 5 <en-us_topic_0065817705__en-us_topic_0057973030_table15913898194628>`. |
   +---------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817705__en-us_topic_0057973030_table56222540:

.. table:: **Table 4** **flavors** field description

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                           |
   +=======================+=======================+=======================================================================================================+
   | id                    | String                | Specifies the flavor ID.                                                                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | links                 | Array of objects      | Specifies the shortcut link of the ECS flavor.                                                        |
   |                       |                       |                                                                                                       |
   |                       |                       | For details, see :ref:`Table 5 <en-us_topic_0065817705__en-us_topic_0057973030_table15913898194628>`. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the flavor name.                                                                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817705__en-us_topic_0057973030_table15913898194628:

.. table:: **Table 5** **links** field description

   ========= ====== ========================================
   Parameter Type   Description
   ========= ====== ========================================
   rel       String Specifies the shortcut link marker name.
   href      String Specifies the shortcut link.
   ========= ====== ========================================

Example Request
---------------

Query available ECS flavors.

.. code-block:: text

   GET https://{endpoint}/v2/743b4c0428d94531b9f2add666642e6b/flavors
   GET https://{endpoint}/v2.1/743b4c0428d94531b9f2add666642e6b/flavors

Example Response
----------------

.. code-block::

   {
       "flavors": [
           {
               "id": "c3.medium",
               "links": [
                   {
                       "href": "https://compute.region.xxx.com/v2.1/743b4c0428d94531b9f2add666642e6b/flavors/c3.medium",
                       "rel": "self"
                   },
                   {
                       "href": "https://compute.region.xxx.com/743b4c0428d94531b9f2add666642e6b/flavors/c3.medium",
                       "rel": "bookmark"
                   }
               ],
               "name": "c3.medium"
           },
           {
               "id": "c3.xlarge",
               "links": [
                   {
                       "href": "https://compute.region.xxx.com/v2.1/743b4c0428d94531b9f2add666642e6b/flavors/c3.xlarge",
                       "rel": "self"
                   },
                   {
                       "href": "https://compute.region.x.com/743b4c0428d94531b9f2add666642e6b/flavors/c3.xlarge",
                       "rel": "bookmark"
                   }
               ],
               "name": "c3.xlarge"
           }
       ]
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
