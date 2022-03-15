Updating ECS Metadata
=====================

Function
--------

This API is used to update ECS metadata.

-  If the metadata does not contain the target field, the field is automatically added.
-  If the metadata contains the target field, the field value is automatically updated.
-  If the field in the metadata is not requested, the field value remains unchanged.

Constraints
-----------

An ECS must be in active, stopped, paused, or suspended state, which is specified by **OS-EXT-STS:vm_state**.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/metadata

POST /v2/{project_id}/servers/{server_id}/metadata

`Table 1 <#enustopic0025560298table18618337185333>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0025560298table18618337185333:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0025560298table52485804185333>`__ describes the request parameters. 

.. _ENUSTOPIC0025560298table52485804185333:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================================+
   | metadata        | Yes             | Object          | Specifies the user-defined metadata key-value pair.                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | For a metadata key:                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | It contains a maximum of 255 Unicode characters and cannot be left blank. A key can contain uppercase letters (A-Z), lowercase letters (a-z), digits (0-9), hyphens (-), underscores (_), colons (:), and periods (.). |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | For a metadata value:                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | A value contains a maximum of 255 Unicode characters.                                                                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

`Table 3 <#enustopic0025560298table48150236185333>`__ describes the response parameters. 

.. _ENUSTOPIC0025560298table48150236185333:

.. table:: **Table 3** Response parameters

   ========= ====== ===================================================
   Parameter Type   Description
   ========= ====== ===================================================
   metadata  Object Specifies the user-defined metadata key-value pair.
   ========= ====== ===================================================

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2/{project_id}/servers/{server_id}/metadata
   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/metadata

.. code-block::

   {
       "metadata": {
           "key": "value"
       }
   }

Example Response
----------------

.. code-block::

   {
       "metadata":{
           "key":"value"
       }
   } 

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


