:original_name: en-us_topic_0031169058.html

.. _en-us_topic_0031169058:

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

:ref:`Table 1 <en-us_topic_0031169058__table60562285165259>` describes the parameters in the URI.

.. _en-us_topic_0031169058__table60562285165259:

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

:ref:`Table 2 <en-us_topic_0031169058__table53480673143936>` describes the response parameters.

.. _en-us_topic_0031169058__table53480673143936:

.. table:: **Table 2** Response parameters

   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                              |
   +===========+===========+========+==========================================================================================================================+
   | addresses | Yes       | Object | Specifies the network address of the ECS. For details, see :ref:`Table 3 <en-us_topic_0031169058__table56891490143956>`. |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0031169058__table56891490143956:

.. table:: **Table 3** **addresses** parameter structure description

   +----------------------------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                  | Mandatory | Type             | Description                                                                                                                                              |
   +============================+===========+==================+==========================================================================================================================================================+
   | Network address of the ECS | Yes       | Array of objects | Specifies the network where the ECS accesses. For details about the network parameter, see :ref:`Table 4 <en-us_topic_0031169058__table22651992144025>`. |
   +----------------------------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0031169058__table22651992144025:

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

Query the networks of a specified ECS.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/servers/{server_id}/ips
   GET https://{endpoint}/v2.1/{project_id}/servers/{server_id}/ips

Example Response
----------------

.. code-block::

   {
       "addresses": {
           "Network address of the ECS": [
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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
