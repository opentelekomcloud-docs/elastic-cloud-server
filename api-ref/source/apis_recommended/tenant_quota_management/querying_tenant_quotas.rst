:original_name: en-us_topic_0020212674.html

.. _en-us_topic_0020212674:

Querying Tenant Quotas
======================

Function
--------

This API is used to query the quotas of all resources for a specified tenant, including used quotas.

URI
---

GET /v1/{project_id}/cloudservers/limits

:ref:`Table 1 <en-us_topic_0020212674__table23262209>` describes the parameters in the URI.

.. _en-us_topic_0020212674__table23262209:

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

:ref:`Table 2 <en-us_topic_0020212674__table6147620>` describes the response parameters.

.. _en-us_topic_0020212674__table6147620:

.. table:: **Table 2** Response parameters

   +-----------+--------+--------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                      |
   +===========+========+==================================================================================================+
   | absolute  | Object | Specifies tenant quotas. For details, see :ref:`Table 3 <en-us_topic_0020212674__table7714075>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212674__table7714075:

.. table:: **Table 3** **absolute** field description

   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | Parameter               | Type                  | Description                                                                                      |
   +=========================+=======================+==================================================================================================+
   | maxTotalInstances       | Integer               | Specifies the maximum number of ECSs you can use.                                                |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxTotalCores           | Integer               | Specifies the maximum number of CPU cores you can use.                                           |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxTotalRAMSize         | Integer               | Specifies the maximum memory space (MB) you can use.                                             |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxTotalKeypairs        | Integer               | Specifies the maximum number of SSH key pairs you can use.                                       |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxServerMeta           | Integer               | Specifies the maximum length of the metadata you can use.                                        |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxPersonality          | Integer               | Specifies the maximum number of files that can be injected.                                      |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxPersonalitySize      | Integer               | Specifies the maximum size (byte) of the file to be injected.                                    |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxServerGroups         | Integer               | Specifies the maximum number of server groups.                                                   |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxServerGroupMembers   | Integer               | Specifies the maximum number of ECSs in an ECS group.                                            |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | totalServerGroupsUsed   | Integer               | Specifies the number of used server groups.                                                      |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxSecurityGroups       | Integer               | Specifies the maximum number of security groups you can use.                                     |
   |                         |                       |                                                                                                  |
   |                         |                       | .. note::                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       |    The quota complies with the VPC quota limit.                                                  |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxSecurityGroupRules   | Integer               | Specifies the maximum number of security group rules that you can configure in a security group. |
   |                         |                       |                                                                                                  |
   |                         |                       | .. note::                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       |    The quota complies with the VPC quota limit.                                                  |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxTotalFloatingIps     | Integer               | Specifies the maximum number of floating IP addresses you can use.                               |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxImageMeta            | Integer               | Specifies the maximum length of the image metadata.                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | totalInstancesUsed      | Integer               | Specifies the number of used ECSs.                                                               |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | totalCoresUsed          | Integer               | Specifies the number of the used CPU cores.                                                      |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | totalRAMUsed            | Integer               | Specifies the used memory size (MB).                                                             |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | totalSecurityGroupsUsed | Integer               | Specifies the number of used security groups.                                                    |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | totalFloatingIpsUsed    | Integer               | Specifies the number of used floating IP addresses.                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v1/{project_id}/cloudservers/limits

Example Response
----------------

Example response

.. code-block::

   {
       "absolute": {
           "maxServerMeta": 128,
           "maxPersonality": 5,
           "maxImageMeta": 128,
           "maxPersonalitySize": 10240,
           "maxSecurityGroupRules": 20,
           "maxTotalKeypairs": -1,
           "totalRAMUsed": 75776,
           "totalInstancesUsed": 21,
           "maxSecurityGroups": 10,
           "totalFloatingIpsUsed": 0,
           "maxTotalCores": 20480,
           "totalSecurityGroupsUsed": 1,
           "maxTotalFloatingIps": 10,
           "maxTotalInstances": 2048,
           "totalCoresUsed": 40,
           "maxTotalRAMSize": 25165824,
           "maxServerGroups": 10,
           "maxServerGroupMembers": 16,
           "totalServerGroupsUsed": 2
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
