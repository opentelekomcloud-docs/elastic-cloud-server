Starting an ECS
===============

Function
--------

This API is used to start a single ECS.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

`Table 1 <#enustopic0020212648table48630964>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212648table48630964:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0020212648table48180537>`__ describes the request parameters. 

.. _ENUSTOPIC0020212648table48180537:

.. table:: **Table 2** Request parameters

   +-----------+-----------+------+------------------------------------------------------------------------+
   | Parameter | Mandatory | Type | Description                                                            |
   +===========+===========+======+========================================================================+
   | os-start  | Yes       | Null | Specifies the operation to start the ECS. The data structure is empty. |
   +-----------+-----------+------+------------------------------------------------------------------------+

Response
--------

None

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

.. code-block::

   {
       "os-start": {}
                       }

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


