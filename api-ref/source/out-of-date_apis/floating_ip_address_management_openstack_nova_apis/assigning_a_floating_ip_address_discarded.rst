:original_name: en-us_topic_0065820816.html

.. _en-us_topic_0065820816:

Assigning a Floating IP Address (Discarded)
===========================================

Function
--------

This API is used to assign a floating IP address.

This API has been discarded. Use the API described in "Assigning a Floating IP Address".

Constraints
-----------

You need to obtain a network resource pool that provides floating IP addresses. To do so, run **GET /v2.0/networks?router:external=True** or **neutron net-external-list**.

URI
---

POST /v2/{project_id}/os-floating-ips

POST /v2.1/{project_id}/os-floating-ips

:ref:`Table 1 <en-us_topic_0065820816__en-us_topic_0057972670_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0065820816__en-us_topic_0057972670_table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0065820816__en-us_topic_0057972670_table62287048>` describes the request parameters.

.. _en-us_topic_0065820816__en-us_topic_0057972670_table62287048:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================+
   | tenant_id       | String          | Yes             | Specifies the tenant ID specified in the URI.                                                                                       |
   |                 |                 |                 |                                                                                                                                     |
   |                 |                 |                 | The value is in UUID format.                                                                                                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | pool            | String          | No              | Specifies the network resource pool that provides floating IP addresses. If it is not specified, the default resource pool is used. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 3 <en-us_topic_0065820816__en-us_topic_0057972670_table56026474>` describes the response parameters.

.. _en-us_topic_0065820816__en-us_topic_0057972670_table56026474:

.. table:: **Table 3** Response parameters

   +-------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                        |
   +=============+===========+========+====================================================================================================================================+
   | floating_ip | Yes       | Object | Specifies the floating IP address. For details, see :ref:`Table 4 <en-us_topic_0065820816__en-us_topic_0057972670_table55642234>`. |
   +-------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065820816__en-us_topic_0057972670_table55642234:

.. table:: **Table 4** **floating_ip** objects

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

   POST https://{endpoint}/v2/e73621affb8f44e1bc01898747ca09d4/os-floating-ips
   POST https://{endpoint}/v2.1/e73621affb8f44e1bc01898747ca09d4/os-floating-ips

.. code-block::

   {
       "pool": "external"
   }

Example Response
----------------

.. code-block::

   {
     "floating_ip": {
       "id": "7aa2aa63-3097-4cfe-a2e4-596c301d3b1b",
       "pool": "external",
       "ip": "10.154.53.184",
       "fixed_ip": null,
       "instance_id": null
     }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
