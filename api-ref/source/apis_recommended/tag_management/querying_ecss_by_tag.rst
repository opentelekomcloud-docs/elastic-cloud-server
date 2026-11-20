:original_name: en-us_topic_0102606095.html

.. _en-us_topic_0102606095:

Querying ECSs by Tag
====================

Function
--------

This API is used to filter ECSs by tag and obtain all tags of an ECS.

URI
---

POST /v1/{project_id}/servers/resource_instances/action

:ref:`Table 1 <en-us_topic_0102606095__table10820175118131>` describes the parameters in the URI.

.. _en-us_topic_0102606095__table10820175118131:

.. table:: **Table 1** Parameter description

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

Request
-------

:ref:`Table 2 <en-us_topic_0102606095__table195321356132718>` describes the request parameters.

.. _en-us_topic_0102606095__table195321356132718:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                                   |
   +=================+=================+==================+===============================================================================================================================================================================================================================+
   | tags            | No              | Array of objects | **Definition**                                                                                                                                                                                                                |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | Displays the ECSs with all the specified tags. For details, see :ref:`Table 3 <en-us_topic_0102606095__table8638721112919>`.                                                                                                  |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Constraints**                                                                                                                                                                                                               |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | -  The structure body must be included.                                                                                                                                                                                       |
   |                 |                 |                  | -  This field cannot be left blank.                                                                                                                                                                                           |
   |                 |                 |                  | -  A key must be unique.                                                                                                                                                                                                      |
   |                 |                 |                  | -  Values of the same key must be unique.                                                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Range**                                                                                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | N/A                                                                                                                                                                                                                           |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Default Value**                                                                                                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | N/A                                                                                                                                                                                                                           |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags        | No              | Array of strings | **Definition**                                                                                                                                                                                                                |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | Displays the ECSs with none of specified tags.                                                                                                                                                                                |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Constraints**                                                                                                                                                                                                               |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | -  The structure body must be included.                                                                                                                                                                                       |
   |                 |                 |                  | -  This field cannot be left blank.                                                                                                                                                                                           |
   |                 |                 |                  | -  Keys must be unique.                                                                                                                                                                                                       |
   |                 |                 |                  | -  Values of the same key must be unique.                                                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Range**                                                                                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | N/A                                                                                                                                                                                                                           |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Default Value**                                                                                                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | N/A                                                                                                                                                                                                                           |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | String           | **Definition**                                                                                                                                                                                                                |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | Limits the number of returned ECSs.                                                                                                                                                                                           |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Constraints**                                                                                                                                                                                                               |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | The maximum value is **1000**. The value cannot be a negative number.                                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Range**                                                                                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | -  If the **action** value is **count**, this parameter is invalid.                                                                                                                                                           |
   |                 |                 |                  | -  If the **action** value is **filter**, the default value is **1,000**.                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Default Value**                                                                                                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | N/A                                                                                                                                                                                                                           |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | String           | **Definition**                                                                                                                                                                                                                |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | Specifies the index position. The query starts from the next piece of data indexed by this parameter.                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Constraints**                                                                                                                                                                                                               |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | The value must be a number and cannot be a negative number.                                                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | This parameter is not required when data on the first page is queried. When you query the subsequent page data, the value in the response body for the query of the data on the previous page is contained in this parameter. |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Range**                                                                                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | -  If the **action** value is **count**, this parameter is invalid.                                                                                                                                                           |
   |                 |                 |                  | -  If the **action** value is **filter**, the default value is **0**.                                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Default Value**                                                                                                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | N/A                                                                                                                                                                                                                           |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action          | Yes             | String           | **Definition**                                                                                                                                                                                                                |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | Specifies the operation, which can be **filter** or **count**.                                                                                                                                                                |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Constraints**                                                                                                                                                                                                               |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | N/A                                                                                                                                                                                                                           |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Range**                                                                                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | -  **filter**: filters ECSs by tag. The ECSs that meet the filter criteria are displayed on pages.                                                                                                                            |
   |                 |                 |                  | -  **count**: searches ECSs by tag. The number of ECSs that meet the search criteria is displayed.                                                                                                                            |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Default Value**                                                                                                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | N/A                                                                                                                                                                                                                           |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | matches         | No              | Array of objects | **Definition**                                                                                                                                                                                                                |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | Specifies the search field, which is used to search for ECSs.                                                                                                                                                                 |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Constraints**                                                                                                                                                                                                               |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | Currently, only **resource_name** can be used for search. For more information, see :ref:`Table 4 <en-us_topic_0102606095__table2075564419352>`.                                                                              |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Range**                                                                                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | N/A                                                                                                                                                                                                                           |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | **Default Value**                                                                                                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | N/A                                                                                                                                                                                                                           |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0102606095__table8638721112919:

.. table:: **Table 3** **tag** field description

   +-----------------+-----------------+------------------+---------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                   |
   +=================+=================+==================+===============================================================+
   | key             | Yes             | String           | **Definition**                                                |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | Specifies the tag key.                                        |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | **Constraints**                                               |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | -  A key contains a maximum of 36 Unicode characters.         |
   |                 |                 |                  | -  This field cannot be left blank.                           |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | **Range**                                                     |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | N/A                                                           |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | **Default Value**                                             |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | N/A                                                           |
   +-----------------+-----------------+------------------+---------------------------------------------------------------+
   | values          | No              | Array of strings | **Definition**                                                |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | Specifies the tag value.                                      |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | **Constraints**                                               |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | -  Values of the same tag must be unique.                     |
   |                 |                 |                  | -  Each value contains a maximum of 43 Unicode characters.    |
   |                 |                 |                  | -  If this parameter is not specified, any value can be used. |
   |                 |                 |                  | -  The values are in the OR relationship.                     |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | **Range**                                                     |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | N/A                                                           |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | **Default Value**                                             |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | N/A                                                           |
   +-----------------+-----------------+------------------+---------------------------------------------------------------+

.. _en-us_topic_0102606095__table2075564419352:

.. table:: **Table 4** **match** field description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                               |
   +=================+=================+=================+===========================================================================================+
   | key             | Yes             | String          | **Definition**                                                                            |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | Specifies the key field to be matched.                                                    |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | **Constraints**                                                                           |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | The tag key can only be **resource_name**. In such a case, the tag value is the ECS name. |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | -  The key must be unique, and the value is used for matching.                            |
   |                 |                 |                 | -  This field is a fixed dictionary value.                                                |
   |                 |                 |                 | -  This field cannot be left blank.                                                       |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | **Range**                                                                                 |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | N/A                                                                                       |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | **Default Value**                                                                         |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | N/A                                                                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | value           | Yes             | String          | **Definition**                                                                            |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | Specifies the tag value.                                                                  |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | **Constraints**                                                                           |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | The tag key can only be **resource_name**. In such a case, the tag value is the ECS name. |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | -  Each value contains a maximum of 255 Unicode characters.                               |
   |                 |                 |                 | -  This field cannot be left blank.                                                       |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | **Range**                                                                                 |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | N/A                                                                                       |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | **Default Value**                                                                         |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | N/A                                                                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 5 <en-us_topic_0102606095__table725495518449>` describes the response parameters.

.. _en-us_topic_0102606095__table725495518449:

.. table:: **Table 5** Response parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                           |
   +=======================+=======================+=======================================================================================================+
   | resources             | Array of objects      | **Definition**                                                                                        |
   |                       |                       |                                                                                                       |
   |                       |                       | Specifies returned ECSs. For details, see :ref:`Table 6 <en-us_topic_0102606095__table790793515528>`. |
   |                       |                       |                                                                                                       |
   |                       |                       | **Range**                                                                                             |
   |                       |                       |                                                                                                       |
   |                       |                       | N/A                                                                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | total_count           | Integer               | **Definition**                                                                                        |
   |                       |                       |                                                                                                       |
   |                       |                       | Specifies the total number of returned ECSs.                                                          |
   |                       |                       |                                                                                                       |
   |                       |                       | **Range**                                                                                             |
   |                       |                       |                                                                                                       |
   |                       |                       | N/A                                                                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0102606095__table790793515528:

.. table:: **Table 6** **resource** field description

   +-----------------------+-----------------------+-----------------------------------------------------+
   | Parameter             | Type                  | Description                                         |
   +=======================+=======================+=====================================================+
   | resource_id           | String                | **Definition**                                      |
   |                       |                       |                                                     |
   |                       |                       | Specifies the ECS ID.                               |
   |                       |                       |                                                     |
   |                       |                       | **Range**                                           |
   |                       |                       |                                                     |
   |                       |                       | N/A                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | resource_detail       | String                | **Definition**                                      |
   |                       |                       |                                                     |
   |                       |                       | Queries ECS details.                                |
   |                       |                       |                                                     |
   |                       |                       | **Range**                                           |
   |                       |                       |                                                     |
   |                       |                       | N/A                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | tags                  | Array of objects      | **Definition**                                      |
   |                       |                       |                                                     |
   |                       |                       | Specifies tags.                                     |
   |                       |                       |                                                     |
   |                       |                       | **Range**                                           |
   |                       |                       |                                                     |
   |                       |                       | N/A                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | resource_name         | String                | **Definition**                                      |
   |                       |                       |                                                     |
   |                       |                       | Specifies the resource name, which is the ECS name. |
   |                       |                       |                                                     |
   |                       |                       | **Range**                                           |
   |                       |                       |                                                     |
   |                       |                       | N/A                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------+

.. table:: **Table 7** **resource_tag** field description

   +-----------------------+-----------------------+---------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                               |
   +=======================+=======================+===========================================================================+
   | key                   | String                | **Definition**                                                            |
   |                       |                       |                                                                           |
   |                       |                       | Specifies the tag key.                                                    |
   |                       |                       |                                                                           |
   |                       |                       | **Range**                                                                 |
   |                       |                       |                                                                           |
   |                       |                       | -  A key contains a maximum of 36 Unicode characters.                     |
   |                       |                       | -  This field cannot be left blank.                                       |
   |                       |                       | -  Can only consist of digits, letters, hyphens (-), and underscores (_). |
   +-----------------------+-----------------------+---------------------------------------------------------------------------+
   | value                 | String                | **Definition**                                                            |
   |                       |                       |                                                                           |
   |                       |                       | Specifies the tag value.                                                  |
   |                       |                       |                                                                           |
   |                       |                       | **Range**                                                                 |
   |                       |                       |                                                                           |
   |                       |                       | -  Each value contains a maximum of 43 Unicode characters.                |
   |                       |                       | -  This field can be left blank.                                          |
   |                       |                       | -  Can only consist of digits, letters, hyphens (-), and underscores (_). |
   +-----------------------+-----------------------+---------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/servers/resource_instances/action

   {
       "offset": "100",
       "limit": "100",
       "action": "filter",
       "matches":[
       {
           "key": "resource_name",
           "value": "ecs_test"
        }],
       "tags": [
       {
           "key": "key1",
           "values": [
               "value1",
               "value2"
           ]
       }]
   }

Example Response
----------------

-  Response body when **action** is set to **filter**

   .. code-block::

      {
            "resources": [
               {
                  "resource_detail": null,
                  "resource_id": "cdfs_cefs_wesas_12_dsad",
                  "resource_name": "ecs_test",
                  "tags": [
                      {
                         "key": "key1",
                         "value": "value1"
                      }
                   ]
               }
             ],
            "total_count": 1000
      }

-  Response body when **action** is set to **count**

   .. code-block::

      {
             "total_count": 1000
      }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
