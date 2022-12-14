:original_name: en-us_topic_0031169059.html

.. _en-us_topic_0031169059:

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

:ref:`Table 1 <en-us_topic_0031169059__table60562285165259>` describes the parameters in the URI.

.. _en-us_topic_0031169059__table60562285165259:

.. table:: **Table 1** Path parameters

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

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

:ref:`Table 3 <en-us_topic_0031169059__table56891490143956>` describes the response parameters.

.. _en-us_topic_0031169059__table56891490143956:

.. table:: **Table 3** Response parameters

   +--------------------------------------------+------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                  | Type       | Description                                                                                                                                    |
   +============================================+============+================================================================================================================================================+
   | Name of the network where the ECS accesses | List(Dict) | Specifies the network where the ECS accesses. For details about the network, see :ref:`Table 4 <en-us_topic_0031169059__table22651992144025>`. |
   +--------------------------------------------+------------+------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0031169059__table22651992144025:

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

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/servers/{server_id}/ips/{networkName}
   GET https://{endpoint}/v2.1/{project_id}/servers/{server_id}/ips/{networkName}

Example Response
----------------

.. code-block::

   {
       "Name of the network where the ECS accesses": [
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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
