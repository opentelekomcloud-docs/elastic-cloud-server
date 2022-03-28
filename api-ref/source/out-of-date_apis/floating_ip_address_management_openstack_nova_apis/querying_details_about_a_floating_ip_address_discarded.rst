Querying Details About a Floating IP Address (Discarded)
========================================================

Function
--------

This API is used to query the details about a floating IP address based on the ID of the IP address.

This API has been discarded. Use the API described in "Querying a Floating IP Address".

URI
---

GET /v2/{project_id}/os-floating-ips/{floating_ip_id}

GET /v2.1/{project_id}/os-floating-ips/{floating_ip_id}

`Table 1 <#enustopic0065820818enustopic0057972673table32475667>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065820818enustopic0057972673table32475667:

.. table:: **Table 1** Parameter description

   ============== ========= ============================================
   Parameter      Mandatory Description
   ============== ========= ============================================
   project_id     Yes       Specifies the project ID.
   floating_ip_id Yes       Specifies the ID of the floating IP address.
   ============== ========= ============================================

Request
-------

None

Response
--------

`Table 2 <#enustopic0065820818enustopic0057972673table38246063>`__ describes the response parameters.



.. _ENUSTOPIC0065820818enustopic0057972673table38246063:

.. table:: **Table 2** Response parameters

   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                             |
   +=============+===========+========+=========================================================================================================================+
   | floating_ip | Yes       | Object | Specifies the floating IP address. For details, see `Table 3 <#enustopic0065820818enustopic0057972673table65314517>`__. |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065820818enustopic0057972673table65314517:

.. table:: **Table 3** **floating_ip** objects

   +-------------+-----------+--------+------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                        |
   +=============+===========+========+====================================================================================+
   | fixed_ip    | Yes       | String | Specifies a private IP address.                                                    |
   +-------------+-----------+--------+------------------------------------------------------------------------------------+
   | id          | Yes       | String | Specifies the floating IP address ID in UUID format.                               |
   +-------------+-----------+--------+------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Specifies the ID of a bound ECS in UUID format.                                    |
   +-------------+-----------+--------+------------------------------------------------------------------------------------+
   | ip          | Yes       | String | Specifies the floating IP address.                                                 |
   +-------------+-----------+--------+------------------------------------------------------------------------------------+
   | pool        | Yes       | String | Specifies the name of a network resource pool that provides floating IP addresses. |
   +-------------+-----------+--------+------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/e73621affb8f44e1bc01898747ca09d4/os-floating-ips/05f71f43-f3c9-47ef-ac8d-9f02aef66418
   GET https://{endpoint}/v2.1/e73621affb8f44e1bc01898747ca09d4/os-floating-ips/05f71f43-f3c9-47ef-ac8d-9f02aef66418

Example Response
----------------

.. code-block::

   {
     "floating_ip":{
         "id": "05f71f43-f3c9-47ef-ac8d-9f02aef66418",
         "pool": "external",
         "ip": "10.154.51.235",
         "fixed_ip": "192.168.1.2",
         "instance_id": "8b380f68-5057-4aa2-a33a-170b37218fa8"
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


