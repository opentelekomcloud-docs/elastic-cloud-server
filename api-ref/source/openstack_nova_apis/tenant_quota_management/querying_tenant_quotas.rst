Querying Tenant Quotas
======================

Function
--------

This API is used to query quotas, including ECSs, vCPUs, and memory.

This API provides the **user_id** parameter for obtaining the quota configuration of a specified user.

URI
---

GET /v2.1/{project_id}/os-quota-sets/{project_id}?user_id={user_id}

GET /v2/{project_id}/os-quota-sets/{project_id}?user_id={user_id}

`Table 1 <#enustopic0067298110enustopic0057973199table12637461156>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0067298110enustopic0057973199table12637461156:

.. table:: **Table 1** Parameter description

   +------------+-----------+-----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Description                                                                                                     |
   +============+===========+=================================================================================================================+
   | project_id | Yes       | Specifies the project ID. If the specified project does not exist, the default quota in the system is returned. |
   +------------+-----------+-----------------------------------------------------------------------------------------------------------------+
   | user_id    | No        | Specifies the user ID. If the specified user does not exist, the default quota in the system is returned.       |
   +------------+-----------+-----------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

`Table 2 <#enustopic0067298110enustopic0057973199enustopic0057973197table62068690>`__ describes the response parameters.



.. _ENUSTOPIC0067298110enustopic0057973199enustopic0057973197table62068690:

.. table:: **Table 2** Response parameters

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                              |
   +===========+========+==========================================================================================================================+
   | quota_set | Object | Specifies the **quota_set** object. For details, see `Table 3 <#enustopic0067298110enustopic0057973199table30231561>`__. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0067298110enustopic0057973199table30231561:

.. table:: **Table 3** **quota_set** parameter description

   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | Parameter                   | Type                  | Description                                                                             |
   +=============================+=======================+=========================================================================================+
   | cores                       | Integer               | Specifies the quantity quota of vCPUs.                                                  |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | fixed_ips                   | Integer               | Specifies the quantity quota of fixed IP addresses. This parameter is not supported.    |
   |                             |                       |                                                                                         |
   |                             |                       | This parameter is not supported in microversion 2.36 and later.                         |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | floating_ips                | Integer               | Specifies the quantity quota of floating IP addresses. This parameter is not supported. |
   |                             |                       |                                                                                         |
   |                             |                       | This parameter is not supported in microversion 2.36 and later.                         |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | id                          | String                | Specifies the project UUID.                                                             |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | injected_file_content_bytes | Integer               | Specifies the size quota (bytes) of the files to be injected.                           |
   |                             |                       |                                                                                         |
   |                             |                       | This parameter is not supported in microversion 2.56 and later.                         |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | injected_file_path_bytes    | Integer               | Specifies the size quota (bytes) of the path for the files to be injected.              |
   |                             |                       |                                                                                         |
   |                             |                       | This parameter is not supported in microversion 2.56 and later.                         |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | injected_files              | Integer               | Specifies the quantity quota of the files to be injected.                               |
   |                             |                       |                                                                                         |
   |                             |                       | This parameter is not supported in microversion 2.56 and later.                         |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | instances                   | Integer               | Specifies the quantity quota of ECSs.                                                   |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | key_pairs                   | Integer               | Specifies the quantity quota of key pairs. This parameter is not supported.             |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | metadata_items              | Integer               | Specifies the metadata quantity quota.                                                  |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | ram                         | Integer               | Specifies the memory quota (MB).                                                        |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | security_group_rules        | Integer               | Specifies the quota of security group rules. This parameter is not supported.           |
   |                             |                       |                                                                                         |
   |                             |                       | This parameter is not supported in microversion 2.36 and later.                         |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | security_groups             | Integer               | Specifies the quantity quota of security groups. This parameter is not supported.       |
   |                             |                       |                                                                                         |
   |                             |                       | This parameter is not supported in microversion 2.36 and later.                         |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | server_groups               | Integer               | Specifies the quantity quota of ECS groups.                                             |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | server_group_members        | Integer               | Specifies the size quota of ECS groups.                                                 |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/d9ebe43510414ef590a4aa158605329e/os-quota-sets/d9ebe43510414ef590a4aa158605329e
   GET https://{endpoint}/v2.1/d9ebe43510414ef590a4aa158605329e/os-quota-sets/d9ebe43510414ef590a4aa158605329e

Example Response
----------------

.. code-block::

   {
       "quota_set": {
           "cores": 20,
           "fixed_ips": 40,
           "floating_ips": 10,
           "id": "d9ebe43510414ef590a4aa158605329e",
           "injected_file_content_bytes": 10240,
           "injected_file_path_bytes": 255,
           "injected_files": 5,
           "instances": 20,
           "key_pairs": 100,
           "metadata_items": 128,
           "ram": 51200,
           "security_group_rules": 20,
           "security_groups": 50,
           "server_group_members": 10,
           "server_groups": 10
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


