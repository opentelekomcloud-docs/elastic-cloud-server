Configuring ECS Metadata
========================

Function
--------

This API is used to configure ECS metadata.

When you call this API, all the metadata of this ECS will be deleted, and the ECS uses the value configured in the request.

Constraints
-----------

An ECS must be in active, stopped, paused, or suspended state, which is specified by **OS-EXT-STS:vm_state**.

URI
---

PUT /v2.1/{project_id}/servers/{server_id}/metadata

PUT /v2/{project_id}/servers/{server_id}/metadata

`Table 1 <#enustopic0077847902enustopic0057973166table32475667>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0077847902enustopic0057973166table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0077847902enustopic0057973166table58874912>`__ describes the request parameters.



.. _ENUSTOPIC0077847902enustopic0057973166table58874912:

.. table:: **Table 2** Request

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================================================================================+
   | metadata        | Object          | Yes             | Specifies the user-defined metadata key-value pair.                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                      |
   |                 |                 |                 | For a metadata key:                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                      |
   |                 |                 |                 | A key contains a maximum of 255 Unicode characters and cannot be empty. A key can contain uppercase letters (A-Z), lowercase letters (a-z), digits (0-9), hyphens (-), underscores (_), colons (:), and periods (.). |
   |                 |                 |                 |                                                                                                                                                                                                                      |
   |                 |                 |                 | For a metadata value:                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                      |
   |                 |                 |                 | A value contains a maximum of 255 Unicode characters.                                                                                                                                                                |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

`Table 3 <#enustopic0077847902enustopic0057973166table52843024>`__ describes the response parameters.



.. _ENUSTOPIC0077847902enustopic0057973166table52843024:

.. table:: **Table 3** Response parameters

   ========= ====== ===================================================
   Parameter Type   Description
   ========= ====== ===================================================
   metadata  Object Specifies the user-defined metadata key-value pair.
   ========= ====== ===================================================

Example Request
---------------

.. code-block::

   PUT https://{endpoint}/v2/{project_id}/servers/{server_id}/metadata
   PUT https://{endpoint}/v2.1/{project_id}/servers/{server_id}/metadata

.. code-block::

   {
       "metadata": {
               "key1": "value1",
               "key2": "value2"
       }
   }

Example Response
----------------

.. code-block::

   {
       "metadata": {
               "key1": "value1",
               "key2": "value2"
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


