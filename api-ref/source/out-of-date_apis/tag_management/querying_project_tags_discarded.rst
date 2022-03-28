Querying Project Tags (Discarded)
=================================

Function
--------

Projects are used to group and isolate OpenStack resources, which include computing, storage, and network resources. A project can be a department or a team. Multiple projects can be created under one account.

This API is used to query all tags used by a user in a specified project.

.. note::

   This API has been discarded. Use the API described in `Querying Project Tags <../../apis_recommended/tag_management/querying_project_tags.html>`__.

URI
---

GET /v1/{project_id}/servers/tags

`Table 1 <#enustopic0000001207623588table144382516421>`__ lists the parameter. 

.. _ENUSTOPIC0000001207623588table144382516421:

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

`Table 2 <#enustopic0000001207623588table725495518449>`__ describes the response parameter.



.. _ENUSTOPIC0000001207623588table725495518449:

.. table:: **Table 2** Response parameter

   ========= ================ ===============
   Parameter Type             Description
   ========= ================ ===============
   tags      Array of objects Specifies tags.
   ========= ================ ===============



.. _ENUSTOPIC0000001207623588table207611141174713:

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

   .. code-block::

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

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


