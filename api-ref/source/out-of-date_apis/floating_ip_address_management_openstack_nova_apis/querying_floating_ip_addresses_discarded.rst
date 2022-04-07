.. _en-us_topic_0065820817:

Querying Floating IP Addresses (Discarded)
==========================================

Function
--------

This API is used to query floating IP addresses.

This API has been discarded. Use the API described in "Querying Floating IP Addresses".

URI
---

GET /v2/{project_id}/os-floating-ips

GET /v2.1/{project_id}/os-floating-ips

:ref:`Table 1 <en-us_topic_0065820817__en-us_topic_0057972671_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0065820817__en-us_topic_0057972671_table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0065820817__en-us_topic_0057972671_table49535170>` describes the response parameters.

.. _en-us_topic_0065820817__en-us_topic_0057972671_table49535170:

.. table:: **Table 2** Response parameters

   +--------------+-----------+------------------+--------------------------------------+
   | Parameter    | Mandatory | Type             | Description                          |
   +==============+===========+==================+======================================+
   | floating_ips | Yes       | Array of objects | Specifies the floating IP addresses. |
   +--------------+-----------+------------------+--------------------------------------+

.. table:: **Table 3** **floating_ip** objects

   =========== ========= ====== ==================================
   Parameter   Mandatory Type   Description
   =========== ========= ====== ==================================
   floating_ip Yes       Object Specifies the floating IP address.
   =========== ========= ====== ==================================

.. table:: **Table 4** **floating_ip** attributes

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

   GET https://{endpoint}/v2/e73621affb8f44e1bc01898747ca09d4/os-floating-ips
   GET https://{endpoint}/v2.1/e73621affb8f44e1bc01898747ca09d4/os-floating-ips

Example Response
----------------

.. code-block::

   {
     "floating_ips": [
       {
         "id": "05f71f43-f3c9-47ef-ac8d-9f02aef66418",
         "pool": "external",
         "ip": "10.154.51.235",
         "fixed_ip": "192.168.1.2",
         "instance_id": "8b380f68-5057-4aa2-a33a-170b37218fa8"
       },
       {
         "id": "a25236cf-dd76-4adc-916a-f0b4a24048d3",
         "pool": "external",
         "ip": "10.154.51.237",
         "fixed_ip": null,
         "instance_id": null
       }
     ]
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
