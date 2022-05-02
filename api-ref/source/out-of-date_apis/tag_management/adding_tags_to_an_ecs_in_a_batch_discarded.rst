:original_name: en-us_topic_0000001252143577.html

.. _en-us_topic_0000001252143577:

Adding Tags to an ECS in a Batch (Discarded)
============================================

Function
--------

-  This API is used to add tags to a specified ECS in a batch.
-  The Tag Management Service (TMS) uses this API to batch manage the tags of an ECS.

.. note::

   This API has been discarded. Use the API described in :ref:`Adding Tags to an ECS in a Batch <en-us_topic_0167811963>`.

Constraints
-----------

-  An ECS allows a maximum of 10 tags.

-  This API is idempotent.

   During tag creation, if a tag exists (both the key and value are the same as those of an existing tag), the tag is successfully processed by default.

-  A new tag will overwrite the original one if their keys are the same and values are different.

URI
---

POST /v1/{project_id}/servers/{server_id}/tags/action

:ref:`Table 1 <en-us_topic_0000001252143577__table19484740133714>` lists the parameters.

.. _en-us_topic_0000001252143577__table19484740133714:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0000001252143577__table1349994618388>` describes the request parameters.

.. _en-us_topic_0000001252143577__table1349994618388:

.. table:: **Table 2** Request parameters

   +-----------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                                               |
   +===========+===========+==================+===========================================================================================================================+
   | tags      | Yes       | Array of objects | Specifies tags.                                                                                                           |
   +-----------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | action    | Yes       | String           | Specifies the operation (only lowercase letters are supported). For example, **create** indicates the creation operation. |
   +-----------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** **resource_tag** field description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                         |
   +=================+=================+=================+=====================================================================+
   | key             | Yes             | String          | Specifies the tag key.                                              |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | -  Cannot be left blank.                                            |
   |                 |                 |                 | -  Must be unique for each resource.                                |
   |                 |                 |                 | -  Contains a maximum of 36 characters.                             |
   |                 |                 |                 | -  Contains only digits, letters, hyphens (-), and underscores (_). |
   |                 |                 |                 | -  Must be unique and cannot be left blank.                         |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | value           | Yes             | String          | Specifies the tag value.                                            |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | -  Contains a maximum of 43 characters.                             |
   |                 |                 |                 | -  Contains only digits, letters, hyphens (-), and underscores (_). |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+

Response
--------

None

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/servers/{server_id}/tags/action

.. code-block::

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
