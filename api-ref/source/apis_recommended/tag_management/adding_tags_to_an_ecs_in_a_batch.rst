:original_name: en-us_topic_0167811963.html

.. _en-us_topic_0167811963:

Adding Tags to an ECS in a Batch
================================

Function
--------

-  This API is used to add tags to a specified ECS in a batch.
-  The Tag Management Service (TMS) uses this API to batch manage the tags of an ECS.

Constraints
-----------

-  An ECS allows a maximum of 10 tags.

-  This API is idempotent.

   During tag creation, if a tag exists (both the key and value are the same as those of an existing tag), the tag is successfully processed by default.

-  A new tag will overwrite the original one if their keys are the same and values are different.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/tags/action

:ref:`Table 1 <en-us_topic_0167811963__table73051127201915>` describes the parameters in the URI.

.. _en-us_topic_0167811963__table73051127201915:

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
   | server_id             | Yes                   | **Definition**            |
   |                       |                       |                           |
   |                       |                       | Specifies the ECS ID.     |
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

:ref:`Table 2 <en-us_topic_0167811963__table69204518218>` describes the request parameters.

.. _en-us_topic_0167811963__table69204518218:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                   |
   +=================+=================+==================+===============================================================================================+
   | tags            | Yes             | Array of objects | **Definition**                                                                                |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | Specifies tags. For details, see :ref:`Table 3 <en-us_topic_0167811963__table1534514266207>`. |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | **Constraints**                                                                               |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | N/A                                                                                           |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | **Range**                                                                                     |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | N/A                                                                                           |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | **Default Value**                                                                             |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | N/A                                                                                           |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------+
   | action          | Yes             | String           | **Definition**                                                                                |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | Specifies the operation identifier.                                                           |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | **Constraints**                                                                               |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | Only lowercase letters are supported.                                                         |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | **Range**                                                                                     |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | create                                                                                        |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | **Default Value**                                                                             |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | N/A                                                                                           |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------+

.. _en-us_topic_0167811963__table1534514266207:

.. table:: **Table 3** **tags** field description

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                              |
   +=================+=================+=================+==========================================================================+
   | key             | Yes             | String          | **Definition**                                                           |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | Specifies the tag key.                                                   |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | **Constraints**                                                          |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | N/A                                                                      |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | **Range**                                                                |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | -  A maximum of 36 characters are supported.                             |
   |                 |                 |                 | -  Only letters, digits, hyphens (-), and underscores (_) are supported. |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | **Default Value**                                                        |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | N/A                                                                      |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+
   | value           | No              | String          | **Definition**                                                           |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | Specifies the tag value.                                                 |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | **Constraints**                                                          |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | N/A                                                                      |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | **Range**                                                                |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | -  A maximum of 43 characters are supported.                             |
   |                 |                 |                 | -  Only letters, digits, hyphens (-), and underscores (_) are supported. |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | **Default Value**                                                        |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | N/A                                                                      |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+

Response
--------

None

Example Request
---------------

Batch add two pairs of tags to a specified ECS.

.. code-block:: text

   POST  https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/tags/action

   {
       "action": "create",
       "tags": [
           {
               "key": "key1",
               "value": "value1"
           },
           {
               "key": "key2",
               "value": "value3"
           }
       ]
   }

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
