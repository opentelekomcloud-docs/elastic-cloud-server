Querying the Networks of a Specified ECS
========================================

Function
--------

This API is used to query the networks of an ECS.

Constraints
-----------

None

URI
---

GET /v2.1/{project_id}/servers/{server_id}/ips

GET /v2/{project_id}/servers/{server_id}/ips

`Table 1 <#enustopic0031169058table60562285165259>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0031169058table60562285165259:

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

`Table 2 <#enustopic0031169058table53480673143936>`__ describes the response parameters.



.. _ENUSTOPIC0031169058table53480673143936:

.. table:: **Table 2** Response parameters

   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                       |
   +===========+===========+========+===================================================================================================================+
   | addresses | Yes       | Object | Specifies the network address of the ECS. For details, see `Table 3 <#enustopic0031169058table56891490143956>`__. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0031169058table56891490143956:

.. table:: **Table 3** **addresses** parameter structure description

   +--------------------------------------------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                  | Mandatory | Type             | Description                                                                                                                                       |
   +============================================+===========+==================+===================================================================================================================================================+
   | Name of the network where the ECS accesses | Yes       | Array of objects | Specifies the network where the ECS accesses. For details about the network parameter, see `Table 4 <#enustopic0031169058table22651992144025>`__. |
   +--------------------------------------------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0031169058table22651992144025:

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

   GET https://{endpoint}/v2/{project_id}/servers/{server_id}/ips
   GET https://{endpoint}/v2.1/{project_id}/servers/{server_id}/ips

Example Response
----------------

.. code-block::

   {
       "addresses": {
           "demo_net": [
               {
                   "version": 4,
                   "addr": "10.0.0.4"
               },
               {
                   "version": 4,
                   "addr": "192.150.73.132"
               }
           ],
           "private_net": [
               {
                   "version": 4,
                   "addr": "10.176.42.16"
               },
               {
                   "version": 6,
                   "addr": "::babe:10.176.42.16"
               }
           ]
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


