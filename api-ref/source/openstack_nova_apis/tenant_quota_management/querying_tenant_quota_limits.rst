:original_name: en-us_topic_0065817717.html

.. _en-us_topic_0065817717:

Querying Tenant Quota Limits
============================

Function
--------

This API is used to query tenant quota limits.

Tenants are only allowed to query their own quota limits.

URI
---

GET /v2.1/{project_id}/limits?project_id={project_id}

GET /v2/{project_id}/limits?project_id={project_id}

:ref:`Table 1 <en-us_topic_0065817717__en-us_topic_0057973197_table258804192629>` describes the parameters in the URI.

.. _en-us_topic_0065817717__en-us_topic_0057973197_table258804192629:

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

:ref:`Table 2 <en-us_topic_0065817717__en-us_topic_0057973197_table62068690>` describes the response parameters.

.. _en-us_topic_0065817717__en-us_topic_0057973197_table62068690:

.. table:: **Table 2** Response parameters

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                              |
   +===========+========+==========================================================================================================================+
   | limits    | Object | Specifies tenant limits. For details, see :ref:`Table 3 <en-us_topic_0065817717__en-us_topic_0057973197_table35022095>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817717__en-us_topic_0057973197_table35022095:

.. table:: **Table 3** **limits** parameter information

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                    |
   +===========+========+================================================================================================================================+
   | rate      | List   | The value is empty.                                                                                                            |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------+
   | absolute  | Object | Specifies tenant quota limits. For details, see :ref:`Table 4 <en-us_topic_0065817717__en-us_topic_0057973197_table37171349>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817717__en-us_topic_0057973197_table37171349:

.. table:: **Table 4** **absolute** parameter information

   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | Parameter               | Type                  | Description                                                     |
   +=========================+=======================+=================================================================+
   | maxServerMeta           | String                | Specifies the limit of ECS metadata quantity.                   |
   |                         |                       |                                                                 |
   |                         |                       | If the value is **-1**, there is no quantity limit.             |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | maxPersonality          | String                | Specifies the quantity limit of injected files.                 |
   |                         |                       |                                                                 |
   |                         |                       | If the value is **-1**, there is no quantity limit.             |
   |                         |                       |                                                                 |
   |                         |                       | This parameter is not supported in microversion 2.56 and later. |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | totalServerGroupsUsed   | String                | Specifies the number of used ECS groups.                        |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | maxImageMeta            | String                | Specifies the limit of the image metadata quantity.             |
   |                         |                       |                                                                 |
   |                         |                       | If the value is **-1**, there is no quantity limit.             |
   |                         |                       |                                                                 |
   |                         |                       | This parameter is not supported in microversion 2.38 and later. |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | maxPersonalitySize      | String                | Specifies the size limit of injected files.                     |
   |                         |                       |                                                                 |
   |                         |                       | If the value is **-1**, there is no size limit.                 |
   |                         |                       |                                                                 |
   |                         |                       | This parameter is not supported in microversion 2.56 and later. |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | maxTotalRAMSize         | String                | Specifies the total memory size limit.                          |
   |                         |                       |                                                                 |
   |                         |                       | If the value is **-1**, there is no size limit.                 |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | maxTotalKeypairs        | String                | Specifies the limit of key pair quantity.                       |
   |                         |                       |                                                                 |
   |                         |                       | If the value is **-1**, there is no quantity limit.             |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | maxSecurityGroupRules   | String                | Specifies the maximum number of security group rules.           |
   |                         |                       |                                                                 |
   |                         |                       | If the value is **-1**, there is no quantity limit.             |
   |                         |                       |                                                                 |
   |                         |                       | This parameter is not supported in microversion 2.35 and later. |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | maxServerGroups         | String                | Specifies the maximum number of ECS groups.                     |
   |                         |                       |                                                                 |
   |                         |                       | If the value is **-1**, there is no quantity limit.             |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | totalCoresUsed          | String                | Specifies the number of used cores.                             |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | totalRAMUsed            | String                | Specifies the size of used memory.                              |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | maxSecurityGroups       | String                | Specifies the maximum number of security groups.                |
   |                         |                       |                                                                 |
   |                         |                       | If the value is **-1**, there is no quantity limit.             |
   |                         |                       |                                                                 |
   |                         |                       | This parameter is not supported in microversion 2.35 and later. |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | totalFloatingIpsUsed    | String                | Specifies the number of used floating IP addresses.             |
   |                         |                       |                                                                 |
   |                         |                       | This parameter is not supported in microversion 2.35 and later. |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | totalInstancesUsed      | String                | Specifies the number of used ECSs.                              |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | totalSecurityGroupsUsed | String                | Specifies the number of used security groups.                   |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | maxTotalFloatingIps     | String                | Specifies the maximum number of floating IP addresses.          |
   |                         |                       |                                                                 |
   |                         |                       | If the value is **-1**, there is no quantity limit.             |
   |                         |                       |                                                                 |
   |                         |                       | This parameter is not supported in microversion 2.35 and later. |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | maxTotalInstances       | String                | Specifies the maximum number of ECSs.                           |
   |                         |                       |                                                                 |
   |                         |                       | If the value is **-1**, there is no quantity limit.             |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | maxTotalCores           | String                | Specifies the maximum number of cores.                          |
   |                         |                       |                                                                 |
   |                         |                       | If the value is **-1**, there is no quantity limit.             |
   +-------------------------+-----------------------+-----------------------------------------------------------------+
   | maxServerGroupMembers   | String                | Specifies the maximum number of members in an ECS group.        |
   |                         |                       |                                                                 |
   |                         |                       | If the value is **-1**, there is no quantity limit.             |
   +-------------------------+-----------------------+-----------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v2/d9ebe43510414ef590a4aa158605329e/limits
   GET https://{endpoint}/v2.1/d9ebe43510414ef590a4aa158605329e/limits

Example Response
----------------

.. code-block::

   {
     "limits": {
       "rate": [],
       "absolute": {
         "maxServerMeta": 128,
         "maxPersonality": 5,
         "totalServerGroupsUsed": 0,
         "maxImageMeta": 128,
         "maxPersonalitySize": 10240,
         "maxTotalRAMSize": 25165824,
         "maxTotalKeypairs": -1,
         "maxSecurityGroupRules": 20,
         "maxServerGroups": -1,
         "totalCoresUsed": 0,
         "totalRAMUsed": 0,
         "maxSecurityGroups": 10,
         "totalFloatingIpsUsed": 0,
         "totalInstancesUsed": 0,
         "totalSecurityGroupsUsed": 0,
         "maxTotalFloatingIps": 10,
         "maxTotalInstances": 2048,
         "maxTotalCores": 20480,
         "maxServerGroupMembers": -1
       }
     }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
