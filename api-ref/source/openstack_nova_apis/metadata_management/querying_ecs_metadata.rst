Querying ECS Metadata
=====================

Function
--------

This API is used to query ECS metadata.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/metadata

GET /v2/{project_id}/servers/{server_id}/metadata

`Table 1 <#enustopic0065817713enustopic0057973165table32475667>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817713enustopic0057973165table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

.. note::

   Pagination query is not supported.

Request
-------

None

Response
--------

`Table 2 <#enustopic0065817713enustopic0057973165table48538422>`__ describes the response parameters.



.. _ENUSTOPIC0065817713enustopic0057973165table48538422:

.. table:: **Table 2** Response parameters

   +-----------+-----------+--------+-----------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                         |
   +===========+===========+========+=====================================================+
   | metadata  | Yes       | Object | Specifies the user-defined metadata key-value pair. |
   +-----------+-----------+--------+-----------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/servers/998af54b-5762-4041-abc1-f98a2c27b3a2/metadata
   GET https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/servers/998af54b-5762-4041-abc1-f98a2c27b3a2/metadata

Example Response
----------------

.. code-block::

   {
       "metadata": {
           "wj": "True"
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


