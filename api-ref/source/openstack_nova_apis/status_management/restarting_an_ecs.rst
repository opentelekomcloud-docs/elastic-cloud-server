Restarting an ECS
=================

Function
--------

This API is used to restart a single ECS.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

`Table 1 <#enustopic0020212650table62669527>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212650table62669527:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0020212650table37818817>`__ describes the request parameters. 

.. _ENUSTOPIC0020212650table37818817:

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                         |
   +===========+===========+========+=====================================================================================================================+
   | reboot    | Yes       | Object | Specifies the operation to restart the ECS. For details, see `Table 3 <#enustopic0020212650table10346346162744>`__. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212650table10346346162744:

.. table:: **Table 3** **reboot** field description

   +-----------------+-----------------+-----------------+----------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                  |
   +=================+=================+=================+==============================================+
   | type            | Yes             | String          | Specifies the type of the restart operation. |
   |                 |                 |                 |                                              |
   |                 |                 |                 | -  **SOFT**: soft restart                    |
   |                 |                 |                 | -  **HARD**: forcible restart (hard restart) |
   +-----------------+-----------------+-----------------+----------------------------------------------+

Response
--------

None

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

.. code-block::

   {
       "reboot": {
           "type": "SOFT"
       }
   }

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


