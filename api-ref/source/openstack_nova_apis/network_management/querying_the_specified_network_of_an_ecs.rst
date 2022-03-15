Querying the Specified Network of an ECS
========================================

Function
--------

This API is used to query the specified network of an ECS.

Constraints
-----------

None

URI
---

GET /v2.1/{project_id}/servers/{server_id}/ips/{networkName}

GET /v2/{project_id}/servers/{server_id}/ips/{networkName}

`Table 1 <#enustopic0031169059table60562285165259>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0031169059table60562285165259:

.. table:: **Table 1** Path parameters

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================



.. _ENUSTOPIC0031169059table1051945864112:

.. table:: **Table 2** Request parameters

   =========== ========= ====== ===============================
   Parameter   Mandatory Type   Description
   =========== ========= ====== ===============================
   server_id   Yes       String Specifies the ECS ID.
   networkName Yes       String Specifies the ECS network name.
   =========== ========= ====== ===============================

Request
-------

None

Response
--------

`Table 3 <#enustopic0031169059table56891490143956>`__ describes the response parameters.



.. _ENUSTOPIC0031169059table56891490143956:

.. table:: **Table 3** Response parameters

   +--------------------------------------------+------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                  | Type       | Description                                                                                                                             |
   +============================================+============+=========================================================================================================================================+
   | Name of the network where the ECS accesses | List(Dict) | Specifies the network where the ECS accesses. For details about the network, see `Table 4 <#enustopic0031169059table22651992144025>`__. |
   +--------------------------------------------+------------+-----------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0031169059table22651992144025:

.. table:: **Table 4** ECS network parameter structure description

   +-----------+---------+------+---------------+-------------------+--------------------------------------------------------------------------------------+
   | Attribute | Type    | CRUD | Default Value | Constraint        | Remarks                                                                              |
   +===========+=========+======+===============+===================+======================================================================================+
   | version   | Integer | R    | N/A           | 4 or 6            | Specifies the IP address version. The value of this parameter can be **4** or **6**. |
   +-----------+---------+------+---------------+-------------------+--------------------------------------------------------------------------------------+
   | addr      | String  | R    | N/A           | IP address format | Specifies the IP address.                                                            |
   +-----------+---------+------+---------------+-------------------+--------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/{project_id}/servers/{server_id}/ips/{networkName}
   GET https://{endpoint}/v2.1/{project_id}/servers/{server_id}/ips/{networkName}

Example Response
----------------

.. code-block::

   {
       "demo_net": [
           {
               "version": 4,
               "addr": "10.0.0.4"
           },
           {
               "version": 4,
               "addr": "192.150.73.132"
           }
       ]
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


