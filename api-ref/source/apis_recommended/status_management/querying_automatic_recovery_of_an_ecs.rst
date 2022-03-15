Querying Automatic Recovery of an ECS
=====================================

Function
--------

This API is used to query automatic recovery configured for an ECS.

URI
---

GET /v1/{project_id}/cloudservers/{server_id}/autorecovery

`Table 1 <#enustopic0067600148table32475667>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0067600148table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

None

Response
--------

`Table 2 <#enustopic0067600148enustopic0057973216table30138413>`__ describes the response parameters.



.. _ENUSTOPIC0067600148enustopic0057973216table30138413:

.. table:: **Table 2** Response parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                   |
   +=======================+=======================+===============================================================================+
   | support_auto_recovery | String                | Queries automatic recovery configured for an ECS.                             |
   |                       |                       |                                                                               |
   |                       |                       | -  **true**: indicates that automatic recovery is configured for an ECS.      |
   |                       |                       | -  **false**: indicates that automatic recovery is not configured for an ECS. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+

Example Request
---------------

None

Example Response
----------------

.. code-block::

   GET https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/autorecovery

.. code-block::

   { 
      "support_auto_recovery": "true"
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


