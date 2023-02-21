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

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0102606095__table195321356132718>` describes the request parameters.

.. _en-us_topic_0102606095__table195321356132718:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                                   |
   +=================+=================+==================+===============================================================================================================================================================================================================================+
   | tags            | No              | Array of objects | Displays the ECSs with all the specified tags. For details, see :ref:`Table 3 <en-us_topic_0102606095__table8638721112919>`.                                                                                                  |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | -  The structure body must be included.                                                                                                                                                                                       |
   |                 |                 |                  | -  This field cannot be left blank.                                                                                                                                                                                           |
   |                 |                 |                  | -  A key must be unique.                                                                                                                                                                                                      |
   |                 |                 |                  | -  Values of the same key must be unique.                                                                                                                                                                                     |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags        | No              | Array of strings | Displays the ECSs with none of specified tags.                                                                                                                                                                                |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | -  The structure body must be included.                                                                                                                                                                                       |
   |                 |                 |                  | -  This field cannot be left blank.                                                                                                                                                                                           |
   |                 |                 |                  | -  Keys must be unique.                                                                                                                                                                                                       |
   |                 |                 |                  | -  Values of the same key must be unique.                                                                                                                                                                                     |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | String           | Limits the maximum number of queried ECSs. The value cannot be a negative number. The maximum value is 1000.                                                                                                                  |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | -  If the **action** value is **count**, this parameter is invalid.                                                                                                                                                           |
   |                 |                 |                  | -  If the **action** value is **filter**, the default value is **1000**.                                                                                                                                                      |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | String           | Specifies index position. The query starts from the next piece of data indexed by this parameter. The value must be a number and cannot be a negative number.                                                                 |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | This parameter is not required when data on the first page is queried. When you query the subsequent page data, the value in the response body for the query of the data on the previous page is contained in this parameter. |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | -  If the **action** value is **count**, this parameter is invalid.                                                                                                                                                           |
   |                 |                 |                  | -  If the **action** value is **filter**, the default value is **0**.                                                                                                                                                         |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action          | Yes             | String           | Specifies the operation, which can be **filter** or **count**.                                                                                                                                                                |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | -  **filter**: filters ECSs by tag. The ECSs that meet the filter criteria are displayed on pages.                                                                                                                            |
   |                 |                 |                  | -  **count**: searches ECSs by tag. The number of ECSs that meet the search criteria is displayed.                                                                                                                            |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | matches         | No              | Array of objects | Specifies the search field, which is used to search for ECSs.                                                                                                                                                                 |
   |                 |                 |                  |                                                                                                                                                                                                                               |
   |                 |                 |                  | Currently, only **resource_name** can be used for search. For more information, see :ref:`Table 4 <en-us_topic_0102606095__table2075564419352>`.                                                                              |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0102606095__table8638721112919:

.. table:: **Table 3** **tag** field description

   +-----------------+-----------------+------------------+---------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                   |
   +=================+=================+==================+===============================================================+
   | key             | Yes             | String           | Specifies the tag key.                                        |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | -  A key contains a maximum of 127 Unicode characters.        |
   |                 |                 |                  | -  This field cannot be left blank.                           |
   +-----------------+-----------------+------------------+---------------------------------------------------------------+
   | values          | No              | Array of strings | Specifies the tag value.                                      |
   |                 |                 |                  |                                                               |
   |                 |                 |                  | -  Values of the same tag must be unique.                     |
   |                 |                 |                  | -  Each value contains a maximum of 255 Unicode characters.   |
   |                 |                 |                  | -  If this parameter is not specified, any value can be used. |
   |                 |                 |                  | -  The values are in the OR relationship.                     |
   +-----------------+-----------------+------------------+---------------------------------------------------------------+

.. _en-us_topic_0102606095__table2075564419352:

.. table:: **Table 4** **match** field description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                               |
   +=================+=================+=================+===========================================================================================+
   | key             | Yes             | String          | Specifies the key field to be matched.                                                    |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | The tag key can only be **resource_name**. In such a case, the tag value is the ECS name. |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | -  The key must be unique, and the value is used for matching.                            |
   |                 |                 |                 | -  This field is a fixed dictionary value.                                                |
   |                 |                 |                 | -  This field cannot be left blank.                                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | value           | Yes             | String          | Specifies the tag value.                                                                  |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | The tag key can only be **resource_name**. In such a case, the tag value is the ECS name. |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | -  Each value contains a maximum of 255 Unicode characters.                               |
   |                 |                 |                 | -  This field cannot be left blank.                                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 5 <en-us_topic_0102606095__table725495518449>` describes the response parameters.

.. _en-us_topic_0102606095__table725495518449:

.. table:: **Table 5** Response parameters

   +-------------+------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter   | Type             | Description                                                                                           |
   +=============+==================+=======================================================================================================+
   | resources   | Array of objects | Specifies returned ECSs. For details, see :ref:`Table 6 <en-us_topic_0102606095__table790793515528>`. |
   +-------------+------------------+-------------------------------------------------------------------------------------------------------+
   | total_count | Integer          | Specifies the total number of queried ECSs.                                                           |
   +-------------+------------------+-------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0102606095__table790793515528:

.. table:: **Table 6** **resource** field description

   +-----------------+------------------+-----------------------------------------------------+
   | Parameter       | Type             | Description                                         |
   +=================+==================+=====================================================+
   | resource_id     | String           | Specifies the ECS ID.                               |
   +-----------------+------------------+-----------------------------------------------------+
   | resource_detail | String           | Queries ECS details.                                |
   +-----------------+------------------+-----------------------------------------------------+
   | tags            | Array of objects | Specifies tags.                                     |
   +-----------------+------------------+-----------------------------------------------------+
   | resource_name   | String           | Specifies the resource name, which is the ECS name. |
   +-----------------+------------------+-----------------------------------------------------+

.. table:: **Table 7** **resource_tag** field description

   +-----------------------+-----------------------+---------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                               |
   +=======================+=======================+===========================================================================+
   | key                   | String                | Specifies the tag key.                                                    |
   |                       |                       |                                                                           |
   |                       |                       | -  It contains a maximum of 36 Unicode characters.                        |
   |                       |                       | -  This field cannot be left blank.                                       |
   |                       |                       | -  Can only consist of digits, letters, hyphens (-), and underscores (_). |
   +-----------------------+-----------------------+---------------------------------------------------------------------------+
   | value                 | String                | Specifies the tag value.                                                  |
   |                       |                       |                                                                           |
   |                       |                       | -  Each value contains a maximum of 43 Unicode characters.                |
   |                       |                       | -  This field can be left blank.                                          |
   |                       |                       | -  Can only consist of digits, letters, hyphens (-), and underscores (_). |
   +-----------------------+-----------------------+---------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/servers/resource_instances/action

.. code-block::

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
