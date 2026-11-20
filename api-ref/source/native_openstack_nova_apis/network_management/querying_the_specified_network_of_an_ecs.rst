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

   +----------------------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                  | Type             | Description                                                                                                                                  |
   +============================+==================+==============================================================================================================================================+
   | Network address of the ECS | Array of objects | Specifies the network where the ECS resides. For details about the network, see :ref:`Table 4 <en-us_topic_0031169059__table1972725101724>`. |
   +----------------------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0031169059__table1972725101724:

.. table:: **Table 4** ECS network parameter structure description

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                     |
   +=================+=================+=================+=================================================================+
   | addr            | No              | String          | Specifies the IP address.                                       |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
   | version         | No              | Integer         | Specifies the IP address type. The value can be **4** or **6**. |
   |                 |                 |                 |                                                                 |
   |                 |                 |                 | -  **4**: IPv4                                                  |
   |                 |                 |                 | -  **6**: IPv6                                                  |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------+

Example Request
---------------

Query the specified network of a specified ECS.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/servers/{server_id}/ips/{networkName}
   GET https://{endpoint}/v2.1/{project_id}/servers/{server_id}/ips/{networkName}

Example Response
----------------

.. code-block::

   {
       "Network address of the ECS": [
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
