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

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                      |
   +=======================+=======================+==================================================================================================+
   | absolute              | Object                | **Definition**                                                                                   |
   |                       |                       |                                                                                                  |
   |                       |                       | Specifies tenant quotas. For details, see :ref:`Table 3 <en-us_topic_0020212674__table7714075>`. |
   |                       |                       |                                                                                                  |
   |                       |                       | **Range**                                                                                        |
   |                       |                       |                                                                                                  |
   |                       |                       | N/A                                                                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212674__table7714075:

.. table:: **Table 3** **absolute** field description

   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | Parameter               | Type                  | Description                                                                                      |
   +=========================+=======================+==================================================================================================+
   | maxTotalInstances       | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the maximum number of ECSs that can be requested.                                      |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxTotalCores           | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the maximum number of CPU cores that the current tenant can apply for.                 |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxTotalRAMSize         | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the maximum memory size (MiB) allowed.                                                 |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxTotalKeypairs        | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the maximum number of SSH key pairs you can use.                                       |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxServerMeta           | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the maximum length of the metadata you can use.                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxPersonality          | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the maximum number of files that can be injected.                                      |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxPersonalitySize      | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the maximum size (byte) of the file to be injected.                                    |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxServerGroups         | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the maximum number of server groups.                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxServerGroupMembers   | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the maximum number of ECSs in an ECS group.                                            |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | totalServerGroupsUsed   | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the number of used server groups.                                                      |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxSecurityGroups       | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the maximum number of security groups you can use.                                     |
   |                         |                       |                                                                                                  |
   |                         |                       | .. note::                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       |    The quota complies with the VPC quota limit.                                                  |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxSecurityGroupRules   | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the maximum number of security group rules that you can configure in a security group. |
   |                         |                       |                                                                                                  |
   |                         |                       | .. note::                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       |    The quota complies with the VPC quota limit.                                                  |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxTotalFloatingIps     | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the maximum number of floating IP addresses you can use.                               |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | maxImageMeta            | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the maximum length of the image metadata.                                              |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | totalInstancesUsed      | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the number of used ECSs.                                                               |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | totalCoresUsed          | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the number of the used CPU cores.                                                      |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | totalRAMUsed            | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the used memory size (MiB).                                                            |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | totalSecurityGroupsUsed | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the number of used security groups.                                                    |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | totalFloatingIpsUsed    | Integer               | **Definition**                                                                                   |
   |                         |                       |                                                                                                  |
   |                         |                       | Specifies the number of used floating IP addresses.                                              |
   |                         |                       |                                                                                                  |
   |                         |                       | **Range**                                                                                        |
   |                         |                       |                                                                                                  |
   |                         |                       | N/A                                                                                              |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Example Request
---------------

Query the quotas of all resources in a project for a tenant.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/cloudservers/limits

Example Response
----------------

Example response

.. code-block::

   {
       "absolute":{
           "maxServerMeta":128,
           "maxPersonality":5,
           "maxImageMeta":128,
           "maxPersonalitySize":10240,
           "maxSecurityGroupRules":20,
           "maxTotalKeypairs":-1,
           "totalRAMUsed":75776,
           "totalInstancesUsed":21,
           "maxSecurityGroups":10,
           "totalFloatingIpsUsed":0,
           "maxTotalCores":20480,
           "totalSecurityGroupsUsed":1,
           "maxTotalFloatingIps":10,
           "maxTotalInstances":2048,
           "totalCoresUsed":40,
           "maxTotalRAMSize":25165824,
           "maxServerGroups":10,
           "maxServerGroupMembers":16,
           "totalServerGroupsUsed":2
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
