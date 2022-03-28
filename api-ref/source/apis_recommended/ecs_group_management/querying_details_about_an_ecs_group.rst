Querying Details About an ECS Group
===================================

Function
--------

This API is used to query details bout an ECS group.

URI
---

GET /v1/{project_id}/cloudservers/os-server-groups/{server_group_id}

`Table 1 <#enustopic0175597847table050833691012>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0175597847table050833691012:

.. table:: **Table 1** Parameter description

   =============== ========= ============================
   Parameter       Mandatory Description
   =============== ========= ============================
   project_id      Yes       Specifies the project ID.
   server_group_id Yes       Specifies an ECS group UUID.
   =============== ========= ============================

Request
-------

None

Response
--------

`Table 2 <#enustopic0175597847table4683214181116>`__ describes the response parameters.



.. _ENUSTOPIC0175597847table4683214181116:

.. table:: **Table 2** Response parameters

   +--------------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Type   | Description                                                                                                              |
   +==============+========+==========================================================================================================================+
   | server_group | Object | Specifies the ECS group information. For details, see `Table 3 <#enustopic0175597847enustopic0057973159table5520021>`__. |
   +--------------+--------+--------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0175597847enustopic0057973159table5520021:

.. table:: **Table 3** **server_group** parameters

   +-----------+------------------+-------------------------------------------------------+
   | Parameter | Type             | Description                                           |
   +===========+==================+=======================================================+
   | id        | String           | Specifies an ECS group UUID.                          |
   +-----------+------------------+-------------------------------------------------------+
   | name      | String           | Specifies the ECS group name.                         |
   +-----------+------------------+-------------------------------------------------------+
   | policies  | Array of strings | Specifies the policies associated with the ECS group. |
   +-----------+------------------+-------------------------------------------------------+
   | members   | Array of strings | Specifies the ECS contained in an ECS group.          |
   +-----------+------------------+-------------------------------------------------------+
   | metadata  | Object           | Specifies the ECS group metadata.                     |
   +-----------+------------------+-------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v1/{project_id}/cloudservers/os-server-groups/{server_group_id}

Example Response
----------------

.. code-block::

   {
       "server_group": {
           "id": "5bbcc3c4-1da2-4437-a48a-66f15b1b13f9",
           "name": "test",
           "policies": ["anti-affinity"],
           "members": [],
           "metadata": {}
          }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


