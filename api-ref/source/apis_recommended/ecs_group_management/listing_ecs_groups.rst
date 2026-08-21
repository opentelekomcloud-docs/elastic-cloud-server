:original_name: en-us_topic_0175597846.html

.. _en-us_topic_0175597846:

Listing ECS Groups
==================

Function
--------

This API is used to list ECS groups.

URI
---

GET /v1/{project_id}/cloudservers/os-server-groups

:ref:`Table 1 <en-us_topic_0175597846__table566015531780>` describes the parameters in the URI.

.. _en-us_topic_0175597846__table566015531780:

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

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                |
   +=================+=================+=================+============================================================================================================================+
   | limit           | No              | Integer         | **Definition**                                                                                                             |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | Specifies the maximum number of server groups that can be returned.                                                        |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | **Constraints**                                                                                                            |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | Maximum: 1000                                                                                                              |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | **Range**                                                                                                                  |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                        |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | **Default Value**                                                                                                          |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | **Definition**                                                                                                             |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | Specifies the marker that points to the ECS group. The query starts from the next piece of data indexed by this parameter. |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | **Constraints**                                                                                                            |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | Parameters marker and limit must be used together.                                                                         |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | **Range**                                                                                                                  |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                        |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | **Default Value**                                                                                                          |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 3 <en-us_topic_0175597846__table696924014912>` describes the response parameters.

.. _en-us_topic_0175597846__table696924014912:

.. table:: **Table 3** Response parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================================================================+
   | server_groups         | Array of objects      | **Definition**                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | Specifies ECS groups. For details, see :ref:`Table 4 <en-us_topic_0175597846__en-us_topic_0057973158_table47937085>`.                                                               |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | **Range**                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | N/A                                                                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | page_info             | Object                | **Definition**                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | If the pagination function is enabled, the UUID of the last ECS group on the current page is returned. For details, see :ref:`Table 5 <en-us_topic_0175597846__table139805663519>`. |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | **Range**                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | N/A                                                                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0175597846__en-us_topic_0057973158_table47937085:

.. table:: **Table 4** **server_groups** parameter information

   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                   |
   +=======================+=======================+===============================================================================+
   | id                    | String                | **Definition**                                                                |
   |                       |                       |                                                                               |
   |                       |                       | Specifies the ECS group UUID.                                                 |
   |                       |                       |                                                                               |
   |                       |                       | **Range**                                                                     |
   |                       |                       |                                                                               |
   |                       |                       | N/A                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | name                  | String                | **Definition**                                                                |
   |                       |                       |                                                                               |
   |                       |                       | Specifies the ECS group name.                                                 |
   |                       |                       |                                                                               |
   |                       |                       | **Range**                                                                     |
   |                       |                       |                                                                               |
   |                       |                       | N/A                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | members               | Array of strings      | **Definition**                                                                |
   |                       |                       |                                                                               |
   |                       |                       | Specifies the ECSs contained in an ECS group.                                 |
   |                       |                       |                                                                               |
   |                       |                       | **Range**                                                                     |
   |                       |                       |                                                                               |
   |                       |                       | N/A                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | metadata              | Object                | **Definition**                                                                |
   |                       |                       |                                                                               |
   |                       |                       | Specifies the ECS group metadata.                                             |
   |                       |                       |                                                                               |
   |                       |                       | **Range**                                                                     |
   |                       |                       |                                                                               |
   |                       |                       | N/A                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | policies              | Array of strings      | **Definition**                                                                |
   |                       |                       |                                                                               |
   |                       |                       | Specifies the policies associated with the ECS group.                         |
   |                       |                       |                                                                               |
   |                       |                       | **Range**                                                                     |
   |                       |                       |                                                                               |
   |                       |                       | -  **anti-affinity**: ECSs in this group must be deployed on different hosts. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+

.. _en-us_topic_0175597846__table139805663519:

.. table:: **Table 5** **page_info** field description

   +-----------------------+-----------------------+------------------------------+
   | Parameter             | Type                  | Description                  |
   +=======================+=======================+==============================+
   | next_marker           | String                | **Definition**               |
   |                       |                       |                              |
   |                       |                       | Specifies an ECS group UUID. |
   |                       |                       |                              |
   |                       |                       | **Range**                    |
   |                       |                       |                              |
   |                       |                       | N/A                          |
   +-----------------------+-----------------------+------------------------------+

Example Request
---------------

List ECS groups.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/cloudservers/os-server-groups

Example Response
----------------

.. code-block::

   {
      "server_groups": [
         {
            "members": [],
            "metadata": {},
            "id": "318b44a7-f7a6-4c0b-8107-e8bd618b28dd",
            "policies": [
                        "anti-affinity"
                        ],
            "name": "SvrGrp-b9d6"
     },
     {
            "members": [],
            "metadata": {},
            "id": "b8f4cfc4-9a59-498c-9b52-643ee6515cd0",
            "policies": [
                        "anti-affinity"
                        ],
            "name": "SvrGrp-10a1"
     }
    ]
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
