.. _en-us_topic_0065817716:

Querying Default Quotas
=======================

Function
--------

This API is used to query default quotas.

URI
---

GET /v2.1/{project_id}/os-quota-sets/{project_id}/defaults

GET /v2/{project_id}/os-quota-sets/{project_id}/defaults

:ref:`Table 1 <en-us_topic_0065817716__en-us_topic_0057973201_table258804192629>` describes the parameters in the URI.

.. _en-us_topic_0065817716__en-us_topic_0057973201_table258804192629:

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

:ref:`Table 2 <en-us_topic_0065817716__en-us_topic_0057973201_en-us_topic_0057973197_table62068690>` describes the response parameters.

.. _en-us_topic_0065817716__en-us_topic_0057973201_en-us_topic_0057973197_table62068690:

.. table:: **Table 2** Response parameters

   +-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                         |
   +===========+========+=====================================================================================================================================+
   | quota_set | Object | Specifies the **quota_set** object. For details, see :ref:`Table 3 <en-us_topic_0065817716__en-us_topic_0057973201_table29589013>`. |
   +-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817716__en-us_topic_0057973201_table29589013:

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
   |                             |                       | This parameter is not supported in microversion 2.57 and later.                         |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | injected_file_path_bytes    | Integer               | Specifies the size quota (bytes) of the path for the files to be injected.              |
   |                             |                       |                                                                                         |
   |                             |                       | This parameter is not supported in microversion 2.57 and later.                         |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | injected_files              | Integer               | Specifies the quantity quota of the files to be injected.                               |
   |                             |                       |                                                                                         |
   |                             |                       | This parameter is not supported in microversion 2.57 and later.                         |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | instances                   | Integer               | Specifies the quantity quota of ECSs.                                                   |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | key_pairs                   | Integer               | Specifies the quota of key pairs. This parameter is not supported.                      |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | metadata_items              | Integer               | Specifies the metadata quantity quota.                                                  |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | ram                         | Integer               | Specifies the memory quota (MB).                                                        |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | security_group_rules        | Integer               | Specifies the quota of security group rules. This parameter is not supported.           |
   |                             |                       |                                                                                         |
   |                             |                       | This parameter is not supported in microversion 2.36 and later.                         |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | security_groups             | Integer               | Specifies the quota of security groups. This parameter is not supported.                |
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

   GET https://{endpoint}/v2/d9ebe43510414ef590a4aa158605329e/os-quota-sets/d9ebe43510414ef590a4aa158605329e/defaults
   GET https://{endpoint}/v2.1/d9ebe43510414ef590a4aa158605329e/os-quota-sets/d9ebe43510414ef590a4aa158605329e/defaults

Example Response
----------------

.. code-block::

   {
       "quota_set": {
       "injected_file_content_bytes": 10240,
           "metadata_items": 128,
           "server_group_members": 10,
           "server_groups": 10,
           "ram": 51200,
           "floating_ips": 10,
           "key_pairs": 100,
           "injected_file_path_bytes": 255,
           "instances": 10,
           "security_group_rules": 20,
           "injected_files": 5,
           "cores": 20,
           "fixed_ips": -1,
           "id": "474eff20eee84b2e87b5717cc7f34dd8",
           "security_groups": 10
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
