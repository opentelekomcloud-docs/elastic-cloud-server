Querying Project Tags
=====================

Function
--------

Projects are used to group and isolate OpenStack resources, which include computing, storage, and network resources. A project can be a department or a team. Multiple projects can be created under one account.

This API is used to query all tags used by a user in a specified project.

URI
---

GET /v1/{project_id}/cloudservers/tags

`Table 1 <#enustopic0167811966table1169019216279>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0167811966table1169019216279:

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

`Table 2 <#enustopic0167811966table14618153352714>`__ describes the response parameters.



.. _ENUSTOPIC0167811966table14618153352714:

.. table:: **Table 2** Response parameters

   +-----------+------------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                                         |
   +===========+==================+=====================================================================================================================+
   | tags      | Array of objects | Specifies the tag list. For details, see `Table 3 <#enustopic0167811966enustopic0102606094table207611141174713>`__. |
   +-----------+------------------+---------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0167811966enustopic0102606094table207611141174713:

.. table:: **Table 3** **tag** field description

   +-----------------------+-----------------------+---------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                               |
   +=======================+=======================+===========================================================================+
   | key                   | String                | Specifies the tag key.                                                    |
   |                       |                       |                                                                           |
   |                       |                       | -  Contains a maximum of 36 Unicode characters.                           |
   |                       |                       | -  Can only consist of digits, letters, hyphens (-), and underscores (_). |
   +-----------------------+-----------------------+---------------------------------------------------------------------------+
   | values                | Array of strings      | Specifies the tag value.                                                  |
   |                       |                       |                                                                           |
   |                       |                       | -  Contains a maximum of 43 Unicode characters.                           |
   |                       |                       | -  Can be left blank.                                                     |
   |                       |                       | -  Can only consist of digits, letters, hyphens (-), and underscores (_). |
   +-----------------------+-----------------------+---------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

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

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


