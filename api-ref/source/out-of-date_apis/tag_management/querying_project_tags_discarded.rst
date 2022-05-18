:original_name: en-us_topic_0000001207623588.html

.. _en-us_topic_0000001207623588:

Querying Project Tags (Discarded)
=================================

Function
--------

Projects are used to group and isolate OpenStack resources, which include computing, storage, and network resources. A project can be a department or a team. Multiple projects can be created under one account.

This API is used to query all tags used by a user in a specified project.

.. note::

   This API has been discarded. Use the API described in :ref:`Querying Project Tags <en-us_topic_0167811966>`.

URI
---

GET /v1/{project_id}/servers/tags

:ref:`Table 1 <en-us_topic_0000001207623588__table144382516421>` lists the parameter.

.. _en-us_topic_0000001207623588__table144382516421:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0000001207623588__table725495518449>` describes the response parameter.

.. _en-us_topic_0000001207623588__table725495518449:

.. table:: **Table 2** Response parameter

   ========= ================ ===============
   Parameter Type             Description
   ========= ================ ===============
   tags      Array of objects Specifies tags.
   ========= ================ ===============

.. table:: **Table 3** **tag** field description

   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                         |
   +=======================+=======================+=====================================================================+
   | key                   | String                | Specifies the tag key.                                              |
   |                       |                       |                                                                     |
   |                       |                       | -  The key can contain a maximum of 36 Unicode characters.          |
   |                       |                       | -  Contains only digits, letters, hyphens (-), and underscores (_). |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | values                | Array of strings      | Specifies the tag value.                                            |
   |                       |                       |                                                                     |
   |                       |                       | -  Each value contains a maximum of 43 Unicode characters.          |
   |                       |                       | -  This field can be left blank.                                    |
   |                       |                       | -  Contains only digits, letters, hyphens (-), and underscores (_). |
   +-----------------------+-----------------------+---------------------------------------------------------------------+

Examples
--------

-  Example Request

   .. code-block:: text

      GET https://{endpoint}/v1/{project_id}/servers/tags

-  Example Response

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
