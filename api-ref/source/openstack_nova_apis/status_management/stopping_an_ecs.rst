Stopping an ECS
===============

Function
--------

This API is used to stop a single ECS.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

`Table 1 <#enustopic0020212652table52155720>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212652table52155720:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0020212652table54550461>`__ describes the request parameters. 

.. _ENUSTOPIC0020212652table54550461:

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                      |
   +===========+===========+========+==================================================================================================================+
   | os-stop   | Yes       | Object | Specifies the operation to stop the ECS. For details, see `Table 3 <#enustopic0020212652table10346346162744>`__. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212652table10346346162744:

.. table:: **Table 3** **os-stop** field description

   +-----------------+-----------------+-----------------+------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                |
   +=================+=================+=================+============================================================+
   | type            | No              | String          | Specifies an ECS stop type. The default value is **SOFT**. |
   |                 |                 |                 |                                                            |
   |                 |                 |                 | -  **SOFT**: normal ECS stop                               |
   |                 |                 |                 | -  **HARD**: forcible ECS stop                             |
   +-----------------+-----------------+-----------------+------------------------------------------------------------+

Response
--------

None

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

.. code-block::

   {
       "os-stop": {}
   }

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


