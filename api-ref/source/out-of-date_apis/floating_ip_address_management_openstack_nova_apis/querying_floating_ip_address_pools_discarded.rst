:original_name: en-us_topic_0065820820.html

.. _en-us_topic_0065820820:

Querying Floating IP Address Pools (Discarded)
==============================================

Function
--------

This API is used to query floating IP address pools.

There is only one network resource pool that can be queried through this API by tenants in Open Telekom Cloud live network environment.

This API has been discarded. Use the API described in "Querying Networks".

Constraints
-----------

The API parameter is as follows: router:external=True

.. code-block:: text

   GET /networks?router:external=True //Name in the result is returned.

URI
---

GET /v2/{project_id}/os-floating-ip-pools

GET /v2.1/{project_id}/os-floating-ip-pools

:ref:`Table 1 <en-us_topic_0065820820__en-us_topic_0057972835_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0065820820__en-us_topic_0057972835_table32475667:

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

:ref:`Table 2 <en-us_topic_0065820820__en-us_topic_0057972835_table54779151>` describes the response parameters.

.. _en-us_topic_0065820820__en-us_topic_0057972835_table54779151:

.. table:: **Table 2** Response parameters

   +-------------------+-----------+------------------+-----------------------------------------------------+
   | Parameter         | Mandatory | Type             | Description                                         |
   +===================+===========+==================+=====================================================+
   | floating_ip_pools | Yes       | Array of objects | Specifies the floating IP address pool.             |
   +-------------------+-----------+------------------+-----------------------------------------------------+
   | name              | Yes       | String           | Specifies the name of the floating IP address pool. |
   +-------------------+-----------+------------------+-----------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v2/e73621affb8f44e1bc01898747ca09d4/os-floating-ip-pools
   GET https://{endpoint}/v2.1/e73621affb8f44e1bc01898747ca09d4/os-floating-ip-pools

Example Response
----------------

.. code-block::

   {
       "floating_ip_pools": [
           {
               "name": "pool1"
           },
           {
               "name": "pool2"
           }
       ]
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
