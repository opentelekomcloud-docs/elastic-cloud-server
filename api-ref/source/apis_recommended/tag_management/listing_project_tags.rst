:original_name: en-us_topic_0167811966.html

.. _en-us_topic_0167811966:

Listing Project Tags
====================

Function
--------

Projects are used to group and isolate OpenStack resources, which include computing, storage, and network resources. A project can be a department or a team. Multiple projects can be created for the same account.

This API is used to list all tags attached to a specified project.

URI
---

GET /v1/{project_id}/cloudservers/tags

:ref:`Table 1 <en-us_topic_0167811966__table1169019216279>` describes the parameters in the URI.

.. _en-us_topic_0167811966__table1169019216279:

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

None

Response
--------

:ref:`Table 2 <en-us_topic_0167811966__table14618153352714>` describes the response parameters.

.. _en-us_topic_0167811966__table14618153352714:

.. table:: **Table 2** Response parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                    |
   +=======================+=======================+================================================================================================================================+
   | tags                  | Array of objects      | **Definition**                                                                                                                 |
   |                       |                       |                                                                                                                                |
   |                       |                       | Specifies the tag list. For details, see :ref:`Table 3 <en-us_topic_0167811966__en-us_topic_0102606094_table207611141174713>`. |
   |                       |                       |                                                                                                                                |
   |                       |                       | **Range**                                                                                                                      |
   |                       |                       |                                                                                                                                |
   |                       |                       | A maximum of 10 tags are supported. They cannot start with \_sys_.                                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0167811966__en-us_topic_0102606094_table207611141174713:

.. table:: **Table 3** **tag** field description

   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                              |
   +=======================+=======================+==========================================================================+
   | key                   | String                | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Specifies the tag key.                                                   |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | -  It cannot be left blank.                                              |
   |                       |                       | -  It must be unique for each resource.                                  |
   |                       |                       | -  A maximum of 36 characters are supported.                             |
   |                       |                       | -  Only letters, digits, hyphens (-), and underscores (_) are supported. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | values                | Array of strings      | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Specifies the tag value.                                                 |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | -  Can be left blank.                                                    |
   |                       |                       | -  A maximum of 43 characters are supported.                             |
   |                       |                       | -  Only letters, digits, hyphens (-), and underscores (_) are supported. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+

Example Request
---------------

List all tags attached to a specified project.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/cloudservers/tags

Example Response
----------------

.. code-block::

   {
         "tags": [
           {
               "key": "key1",
               "values": [
                   "value1",
                   "value2"
               ]
           },
           {
               "key": "key2",
               "values": [
                   "value1",
                   "value2"
               ]
           }
       ]
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
