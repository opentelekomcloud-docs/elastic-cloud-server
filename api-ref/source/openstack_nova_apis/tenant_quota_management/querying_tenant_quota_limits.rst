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

`Table 1 <#enustopic0065817717enustopic0057973197table258804192629>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817717enustopic0057973197table258804192629:

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

`Table 2 <#enustopic0065817717enustopic0057973197table62068690>`__ describes the response parameters.



.. _ENUSTOPIC0065817717enustopic0057973197table62068690:

.. table:: **Table 2** Response parameters

   +-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                   |
   +===========+========+===============================================================================================================+
   | limits    | Object | Specifies tenant limits. For details, see `Table 3 <#enustopic0065817717enustopic0057973197table35022095>`__. |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817717enustopic0057973197table35022095:

.. table:: **Table 3** **limits** parameter information

   +-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                         |
   +===========+========+=====================================================================================================================+
   | rate      | List   | The value is empty.                                                                                                 |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | absolute  | Object | Specifies tenant quota limits. For details, see `Table 4 <#enustopic0065817717enustopic0057973197table37171349>`__. |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817717enustopic0057973197table37171349:

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

.. code-block::

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

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


