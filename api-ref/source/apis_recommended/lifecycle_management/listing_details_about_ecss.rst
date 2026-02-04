:original_name: en-us_topic_0094148850.html

.. _en-us_topic_0094148850:

Listing Details About ECSs
==========================

Function
--------

This API is used to list details about ECSs based on search criteria.

The information that can be queried includes the ECS billing mode and whether the ECS is frozen.

URI
---

GET /v1/{project_id}/cloudservers/detail?flavor={flavor}&name={name}&status={status}&limit={limit}&offset={offset}&not-tags={not-tags}&reservation_id={reservation_id}&&tags={tags}&ip={ip}

:ref:`Table 1 <en-us_topic_0094148850__table32475667>` describes the parameters in the URI.

.. _en-us_topic_0094148850__table32475667:

.. table:: **Table 1** Path parameters

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================================================================================+
   | offset          | No              | Integer         | **Definition**                                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | Specifies the page number.                                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | The value must be greater than or equal to **0** and the default value is **1**.                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | If the value is **0**, the first page is displayed, which is the same as the value **1**.                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | You are advised to set this parameter to a value greater than or equal to 1.                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Range**                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavor          | No              | String          | **Definition**                                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | Specifies the ECS flavor ID.                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | For details about the flavors that have been released, see "ECS Specifications and Types" in the *Elastic Cloud Server User Guide*.                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Range**                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | **Definition**                                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | Specifies the ECS name, which is fuzzy-matched.                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Range**                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | Periods (.) are supported to match any single characters except \\n and \\r. A period is equal to [^\\n\\r].                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | **Definition**                                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | Specifies the ECS status.                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Range**                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **ACTIVE**, **BUILD**, **ERROR**, **HARD_REBOOT**, **MIGRATING**, **REBOOT**, **REBUILD**, **RESIZE**, **REVERT_RESIZE**, **SHUTOFF**, **VERIFY_RESIZE**, **DELETED**, **SHELVED**, **SHELVED_OFFLOADED**, and **UNKNOWN** |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | For details, see :ref:`ECS Statuses <en-us_topic_0178420672>`.                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | .. note::                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 |    When an ECS is in an intermediate state, the statuses that can be obtained are as follows:                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 |    -  **ACTIVE**: **ACTIVE**, **REBOOT**, **HARD_REBOOT**, **REBUILD**, **MIGRATING**, or **RESIZE**                                                                                                                       |
   |                 |                 |                 |    -  **SHUTOFF**: **SHUTOFF**, **RESIZE**, or **REBUILD**                                                                                                                                                                 |
   |                 |                 |                 |    -  **ERROR**: **ERROR** or **REBUILD**                                                                                                                                                                                  |
   |                 |                 |                 |    -  **VERIFY_RESIZE**: **VERIFY_RESIZE** or **REVERT_RESIZE**                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | **Definition**                                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | Specifies the maximum number of ECSs on one page.                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | Each page contains 25 ECSs by default, and a maximum of 1,000 ECSs are returned. For large volumes of data, you are advised to set the value to **200**.                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Range**                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags            | No              | String          | **Definition**                                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | Queries ECSs with tags containing the specified value.                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Range**                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not-tags        | No              | String          | **Definition**                                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | Queries ECSs with tags not containing the specified value.                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | For example, if the queried ECS list should not contain BMSs, set this parameter as follows: not-tags=__type_baremetal                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Range**                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | reservation_id  | No              | String          | **Definition**                                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | Specifies the ID returned when ECSs are created in a batch by using OpenStack Nova API. This parameter is used to query ECSs created in a batch.                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Range**                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip              | No              | String          | **Definition**                                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | Specifies the filtering result for IPv4 addresses, which are fuzzy-matched.                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | These IP addresses are private IP addresses.                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Range**                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | N/A                                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 3 <en-us_topic_0094148850__en-us_topic_0057972909_table36183900>` describes the response parameters.

.. _en-us_topic_0094148850__en-us_topic_0057972909_table36183900:

.. table:: **Table 3** Response parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                        |
   +=======================+=======================+====================================================================================================================================+
   | servers               | Array of objects      | **Definition**                                                                                                                     |
   |                       |                       |                                                                                                                                    |
   |                       |                       | Specifies the list of ECS details. For details, see :ref:`Table 4 <en-us_topic_0094148850__en-us_topic_0057972887_table61673566>`. |
   |                       |                       |                                                                                                                                    |
   |                       |                       | **Range**                                                                                                                          |
   |                       |                       |                                                                                                                                    |
   |                       |                       | N/A                                                                                                                                |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | count                 | Integer               | **Definition**                                                                                                                     |
   |                       |                       |                                                                                                                                    |
   |                       |                       | Specifies the total number of ECSs.                                                                                                |
   |                       |                       |                                                                                                                                    |
   |                       |                       | **Range**                                                                                                                          |
   |                       |                       |                                                                                                                                    |
   |                       |                       | N/A                                                                                                                                |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0094148850__en-us_topic_0057972887_table61673566:

.. table:: **Table 4** **server** field description

   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                            | Type                          | Description                                                                                                                                                                                                                                           |
   +======================================+===============================+=======================================================================================================================================================================================================================================================+
   | status                               | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ECS status.                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **ACTIVE**, **BUILD**, **ERROR**, **HARD_REBOOT**, **MIGRATING**, **REBOOT**, **REBUILD**, **RESIZE**, **REVERT_RESIZE**, **SHUTOFF**, **VERIFY_RESIZE**, **DELETED**, **SHELVED**, **SHELVED_OFFLOADED**, and **UNKNOWN**                            |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | For details, see :ref:`ECS Statuses <en-us_topic_0178420672>`.                                                                                                                                                                                        |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated                              | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the last time when the ECS was updated, such as started, stopped, or restarted.                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | The time is in the format of "2019-05-22T03:30:52Z".                                                                                                                                                                                                  |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hostId                               | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the hash value of the host ID of the ECS.                                                                                                                                                                                                   |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-SRV-ATTR:host                 | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the name of the host where the ECS resides.                                                                                                                                                                                                 |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | addresses                            | Map<String, Array of objects> | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the network attribute of the ECS.                                                                                                                                                                                                           |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | -  The key indicates the network name, for example, **demo_net**.                                                                                                                                                                                     |
   |                                      |                               | -  The value indicates the network attribute specified in :ref:`Table 5 <en-us_topic_0094148850__en-us_topic_0057972887_table23553967>`.                                                                                                              |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_name                             | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the key pair that is used to authenticate an ECS.                                                                                                                                                                                           |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image                                | Object                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ECS image. For details, see :ref:`Table 6 <en-us_topic_0169494074__table173259974818>`.                                                                                                                                                 |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-STS:task_state                | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ECS task status. This is an extended attribute. For details, see :ref:`ECS Statuses <en-us_topic_0178420672>`.                                                                                                                          |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-STS:vm_state                  | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ECS status. This is an extended attribute. For details, see :ref:`ECS Statuses <en-us_topic_0178420672>`.                                                                                                                               |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-SRV-ATTR:instance_name        | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ECS alias. This is an extended attribute.                                                                                                                                                                                               |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-SRV-ATTR:hypervisor_hostname  | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the name of the virtualization host where the ECS resides. This is an extended attribute.                                                                                                                                                   |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavor                               | Object                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ECS flavor.                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | For details, see :ref:`Table 1 <en-us_topic_0169494074__en-us_topic_0057972887_table41869715>`.                                                                                                                                                       |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                                   | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ECS ID in UUID format.                                                                                                                                                                                                                  |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_groups                      | Array of objects              | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the security groups of the ECS.                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | For details, see :ref:`Table 2 <en-us_topic_0169494074__en-us_topic_0057972887_table38168783>`.                                                                                                                                                       |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-AZ:availability_zone          | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the AZ of an ECS. This is an extended attribute.                                                                                                                                                                                            |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_id                              | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ID of the user for creating the ECS. The value is in UUID format.                                                                                                                                                                       |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                                 | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ECS name.                                                                                                                                                                                                                               |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created                              | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the time when the ECS was created.                                                                                                                                                                                                          |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | The time is in the format of "2019-05-22T03:19:19Z".                                                                                                                                                                                                  |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id                            | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ID of the tenant that the ECS belongs to, which is the project ID in UUID format.                                                                                                                                                       |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-DCF:diskConfig                    | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the disk configuration mode. This is an extended attribute.                                                                                                                                                                                 |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | -  **MANUAL**: indicates that the image space of the system disk cannot be expanded.                                                                                                                                                                  |
   |                                      |                               | -  **AUTO**: indicates that the image space of the system disk can be automatically expanded to the same size as that specified in flavor.                                                                                                            |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | accessIPv4                           | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | This is a reserved attribute.                                                                                                                                                                                                                         |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | accessIPv6                           | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | This is a reserved attribute.                                                                                                                                                                                                                         |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fault                                | Object                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ECS failure cause.                                                                                                                                                                                                                      |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | -  If the ECS status is normal or abnormal, **NULL** is displayed.                                                                                                                                                                                    |
   |                                      |                               | -  If the ECS is not found, the fault "Instance *xxxx* could not be found" is returned.                                                                                                                                                               |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | progress                             | Integer                       | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ECS progress.                                                                                                                                                                                                                           |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | 0 to 100                                                                                                                                                                                                                                              |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-STS:power_state               | Integer                       | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the power status of the ECS. This is an extended attribute.                                                                                                                                                                                 |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | -  **0**: NOSTATE                                                                                                                                                                                                                                     |
   |                                      |                               | -  **1**: RUNNING                                                                                                                                                                                                                                     |
   |                                      |                               | -  **4**: SHUTDOWN                                                                                                                                                                                                                                    |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | config_drive                         | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the config drive.                                                                                                                                                                                                                           |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata                             | Map<String,String>            | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ECS metadata. For details, see :ref:`Table 4 <en-us_topic_0169494074__table537485761711>`.                                                                                                                                              |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | .. note::                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               |    Metadata includes system default fields and user-defined fields.                                                                                                                                                                                   |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-SRV-USG:launched_at               | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the time when the ECS was started. The time is in the format of "2019-05-22T03:23:59.000000".                                                                                                                                               |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-SRV-USG:terminated_at             | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the time when the ECS was deleted.                                                                                                                                                                                                          |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | The time is in the format of "2019-05-22T03:23:59.000000".                                                                                                                                                                                            |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-extended-volumes:volumes_attached | Array of objects              | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the disks attached to an ECS.                                                                                                                                                                                                               |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | For details, see :ref:`Table 3 <en-us_topic_0169494074__en-us_topic_0057972887_table33871262>`.                                                                                                                                                       |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                          | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ECS description.                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | host_status                          | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the status of the host where the ECS resides.                                                                                                                                                                                               |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | -  **UP**: The status is normal.                                                                                                                                                                                                                      |
   |                                      |                               | -  **UNKNOWN**: The status is unknown.                                                                                                                                                                                                                |
   |                                      |                               | -  **DOWN**: the status is abnormal.                                                                                                                                                                                                                  |
   |                                      |                               | -  **MAINTENANCE**: The status is maintenance.                                                                                                                                                                                                        |
   |                                      |                               | -  Empty string: There is no host information.                                                                                                                                                                                                        |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-SRV-ATTR:hostname             | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the hostname of the ECS.                                                                                                                                                                                                                    |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-SRV-ATTR:reservation_id       | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ID reserved for the ECS to be created in a batch. You can use this ID to obtain all the ECSs created in the same batch.                                                                                                                 |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-SRV-ATTR:launch_index         | Integer                       | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the startup sequence of all ECSs created in a batch. The value ranges from 0 to the number of ECSs created in the batch.                                                                                                                    |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-SRV-ATTR:kernel_id            | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the UUID of the kernel image when the AMI image is used. In other scenarios, leave this parameter blank.                                                                                                                                    |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-SRV-ATTR:ramdisk_id           | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the UUID of a RAM disk image when the AMI image is used. In other cases, leave this parameter blank.                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-SRV-ATTR:root_device_name     | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the device name of the ECS system disk. For example, if the device type of the system disk is VBD, the value of this parameter is **/dev/vda**. If the device type of the system disk is SCSI, the value of this parameter is **/dev/sda**. |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-SRV-ATTR:user_data            | String                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the user data (encoded) configured during ECS creation.                                                                                                                                                                                     |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | locked                               | Boolean                       | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies whether an ECS is locked.                                                                                                                                                                                                                   |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | -  **true**: The ECS is locked.                                                                                                                                                                                                                       |
   |                                      |                               | -  **false**: The ECS is not locked.                                                                                                                                                                                                                  |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                                 | Array of strings              | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the list of ECS tags.                                                                                                                                                                                                                       |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os:scheduler_hints                   | Object                        | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies the ECS scheduling information. For details, see :ref:`Table 11 <en-us_topic_0167957246__table3756175217341>`.                                                                                                                              |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sys_tags                             | Array of objects              | **Definition**                                                                                                                                                                                                                                        |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | Specifies ECS system tags.                                                                                                                                                                                                                            |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | For details, see :ref:`Table 5 <en-us_topic_0169494074__table6690227839>`.                                                                                                                                                                            |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | **Range**                                                                                                                                                                                                                                             |
   |                                      |                               |                                                                                                                                                                                                                                                       |
   |                                      |                               | N/A                                                                                                                                                                                                                                                   |
   +--------------------------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0094148850__en-us_topic_0057972887_table23553967:

.. table:: **Table 5** **addresses** field description

   +-------------------------+-----------------------+--------------------------------------------------------+
   | Parameter               | Type                  | Description                                            |
   +=========================+=======================+========================================================+
   | version                 | String                | **Definition**                                         |
   |                         |                       |                                                        |
   |                         |                       | Specifies the IP address version.                      |
   |                         |                       |                                                        |
   |                         |                       | **Range**                                              |
   |                         |                       |                                                        |
   |                         |                       | -  **4**: indicates IPv4.                              |
   |                         |                       | -  **6**: indicates IPv6.                              |
   +-------------------------+-----------------------+--------------------------------------------------------+
   | addr                    | String                | **Definition**                                         |
   |                         |                       |                                                        |
   |                         |                       | Specifies the IP address.                              |
   |                         |                       |                                                        |
   |                         |                       | **Range**                                              |
   |                         |                       |                                                        |
   |                         |                       | N/A                                                    |
   +-------------------------+-----------------------+--------------------------------------------------------+
   | OS-EXT-IPS:type         | String                | **Definition**                                         |
   |                         |                       |                                                        |
   |                         |                       | Specifies the IP address type.                         |
   |                         |                       |                                                        |
   |                         |                       | **Range**                                              |
   |                         |                       |                                                        |
   |                         |                       | -  **fixed**: indicates the private IP address.        |
   |                         |                       | -  **floating**: indicates the floating IP address.    |
   +-------------------------+-----------------------+--------------------------------------------------------+
   | OS-EXT-IPS-MAC:mac_addr | String                | **Definition**                                         |
   |                         |                       |                                                        |
   |                         |                       | Specifies the MAC address.                             |
   |                         |                       |                                                        |
   |                         |                       | **Range**                                              |
   |                         |                       |                                                        |
   |                         |                       | N/A                                                    |
   +-------------------------+-----------------------+--------------------------------------------------------+
   | OS-EXT-IPS:port_id      | String                | **Definition**                                         |
   |                         |                       |                                                        |
   |                         |                       | Specifies the port ID corresponding to the IP address. |
   |                         |                       |                                                        |
   |                         |                       | **Range**                                              |
   |                         |                       |                                                        |
   |                         |                       | N/A                                                    |
   +-------------------------+-----------------------+--------------------------------------------------------+

.. table:: **Table 6** **security_options** field description

   +-----------------+-----------------+-----------------+------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                |
   +=================+=================+=================+============================================================+
   | tpm_enabled     | Yes             | Boolean         | **Definition**                                             |
   |                 |                 |                 |                                                            |
   |                 |                 |                 | Specifies whether to enable TPM.                           |
   |                 |                 |                 |                                                            |
   |                 |                 |                 | **Constraints**                                            |
   |                 |                 |                 |                                                            |
   |                 |                 |                 | Currently, the following instance types support TPM: Pi5e. |
   |                 |                 |                 |                                                            |
   |                 |                 |                 | **Range**                                                  |
   |                 |                 |                 |                                                            |
   |                 |                 |                 | -  **true**: Enable TPM.                                   |
   |                 |                 |                 | -  **false**: Disable TPM.                                 |
   |                 |                 |                 |                                                            |
   |                 |                 |                 | **Default Value**                                          |
   |                 |                 |                 |                                                            |
   |                 |                 |                 | false                                                      |
   +-----------------+-----------------+-----------------+------------------------------------------------------------+

Example Request
---------------

List details about ECSs. Ten records are displayed on each page, starting from the first page.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/cloudservers/detail?offset=1&limit=10

Example Response
----------------

.. code-block::

   {
       "count":4,
       "servers":[
           {
               "fault":null,
               "id":"b37fd80e-ac67-4d02-b9f1-9891c9c0fabf",
               "name":"ecs-5e70",
               "addresses":{
                   "164489f6-cbf7-45b4-b6d0-d407c48cf7fc":[
                       {
                           "version":"4",
                           "addr":"192.168.0.206",
                           "OS-EXT-IPS-MAC:mac_addr":"fa:16:3e:95:88:3f",
                           "OS-EXT-IPS:port_id":"7b5d615c-186d-4646-9cb8-444addfe9b92",
                           "OS-EXT-IPS:type":"fixed"
                       },
                       {
                           "version":"4",
                           "addr":"192.168.0.8",
                           "OS-EXT-IPS-MAC:mac_addr":"fa:16:3e:1d:88:43",
                           "OS-EXT-IPS:port_id":"dda2027b-2f03-497b-8d42-620da2baacc3",
                           "OS-EXT-IPS:type":"fixed"
                       }
                   ]
               },
               "flavor":{
                   "disk":"0",
                   "vcpus":"2",
                   "ram":"1024",
                   "id":"c3.large.2",
                   "name":"c3.large.2"
               },
               "accessIPv4":"",
               "accessIPv6":"",
               "status":"SHUTOFF",
               "image":{
                   "id":"1ce5800a-e487-4c1b-b264-3353a39e2b4b"
               },
               "hostId":"f92345b97fd291f67a29ed735a82a8983f370175d2ba3d18d66893f4",
               "updated":"2018-08-14T07:26:49Z",
               "created":"2018-08-13T13:46:09Z",
               "metadata":{
                   "metering.image_id":"af60e0d5-6952-4f3d-b0ed-31bb19d4a692",
                   "metering.resourcespeccode":"c3.large.2.linux",
                   "image_name":"HEC_Public_Cloudinit_CentOS_7.4_64bit",
                   "metering.product_id":"00301-253164-0--0",
                   "os_bit":"64",
                   "lockSourceId":"",
                   "lockScene":"",
                   "metering.order_id":"CS1808132145NRVRE",
                   "lockCheckEndpoint":"",
                   "metering.imagetype":"gold",
                   "lockSource":"",
                   "metering.resourcetype":"1",
                   "vpc_id":"164489f6-cbf7-45b4-b6d0-d407c48cf7fc",
                   "os_type":"Linux",
                   "charging_mode":"1"
               },
               "tags":[

               ],
               "description":"ecs-4cff",
               "locked":false,
               "config_drive":"",
               "tenant_id":"edcb94a885a84ed3a3fdf8ea4d2741da",
               "user_id":"bb7f23e27e7e46f3aaceb5f53a158bdc",
               "os-extended-volumes:volumes_attached":[
                   {
                       "device":"/dev/sda",
                       "bootIndex":"0",
                       "id":"2edc879f-022e-4bd6-b079-95a27564d449",
                       "delete_on_termination":"false"
                   }
               ],
               "OS-EXT-STS:task_state":null,
               "OS-EXT-STS:power_state":4,
               "OS-EXT-STS:vm_state":"stopped",
               "OS-EXT-SRV-ATTR:host":"az1.dc1",
               "OS-EXT-SRV-ATTR:instance_name":"instance-00137941",
               "OS-EXT-SRV-ATTR:hypervisor_hostname":"nova001@248",
               "OS-DCF:diskConfig":"MANUAL",
               "OS-EXT-AZ:availability_zone":"az1-dc1",
               "os:scheduler_hints":{
               },
               "OS-EXT-SRV-ATTR:root_device_name":"/dev/sda",
               "OS-EXT-SRV-ATTR:ramdisk_id":"8999878c-4a62-4014-89be-1743ff3a5daf",
               "OS-EXT-SRV-ATTR:user_data":"IyEvYmluL2Jhc2gKZWNobyAncm9vdDokNiRKQ2FzUWQkbm5wVmhJUFZlNVMwc3pXbnJGLnZVZ1FCWk4xTEo5Vy8wd09WTmFZaWpBRXdtRnhuQmZaTllVZXhBWktVWFVTeVhEeERuSUMzV2JjZEJyQUVBZkZvLy8nIHwgY2hwYXNzd2QgLWU7",
               "OS-SRV-USG:launched_at":"2018-08-13T13:46:46.000000",
               "OS-EXT-SRV-ATTR:kernel_id":"",
               "OS-EXT-SRV-ATTR:launch_index":0,
               "host_status":"UP",
               "OS-EXT-SRV-ATTR:reservation_id":"r-a8mg9vwr",
               "OS-EXT-SRV-ATTR:hostname":"ecs-4cff",
               "sys_tags":[
                   {
                       "key":"_sys_enterprise_project_id",
                       "value":"441d5677-b76a-4dd4-a97a-ef7fd633c095"
                   }
               ],
               "security_groups":[
                   {
                       "id":"71846bf6-1cda-4515-8590-3707be295e76",
                       "name":"Sys-FullAccess"
                   },
                   {
                       "id":"b1786350-da65-11e7-b312-0255ac101b03",
                       "name":"default"
                   }
               ]
           },
           {
               "fault":null,
               "id":"8380dcc9-0eac-4407-9f9e-df8c9eddeacd",
               "name":"ecs-f680",
               "addresses":{
                   "164489f6-cbf7-45b4-b6d0-d407c48cf7fc":[
                       {
                           "version":"4",
                           "addr":"192.168.0.218",
                           "OS-EXT-IPS-MAC:mac_addr":"fa:16:3e:bb:b3:fe",
                           "OS-EXT-IPS:port_id":"240c696f-68d8-4f3f-941d-fecf2b375132",
                           "OS-EXT-IPS:type":"fixed"
                       }
                   ]
               },
               "flavor":{
                   "disk":"0",
                   "vcpus":"2",
                   "ram":"1024",
                   "id":"c3.large.2",
                   "name":"c3.large.2"
               },
               "accessIPv4":"",
               "accessIPv6":"",
               "status":"SHUTOFF",
               "image":{
                   "id":"1ce5800a-e487-4c1b-b264-3353a39e2b4b"
               },
               "hostId":"f92345b97fd291f67a29ed735a82a8983f370175d2ba3d18d66893f4",
               "updated":"2018-08-14T03:01:00Z",
               "created":"2018-08-13T13:38:29Z",
               "metadata":{
                   "metering.image_id":"af60e0d5-6952-4f3d-b0ed-31bb19d4a692",
                   "metering.imagetype":"gold",
                   "metering.resourcespeccode":"c3.large.2.linux",
                   "image_name":"HEC_Public_Cloudinit_CentOS_7.4_64bit",
                   "metering.resourcetype":"1",
                   "os_bit":"64",
                   "vpc_id":"164489f6-cbf7-45b4-b6d0-d407c48cf7fc",
                   "os_type":"Linux",
                   "charging_mode":"0"
               },
               "tags":[
                   "_sys_root_resource_id=9d81b37c-455f-4528-b0ab-a6abcd0a330b",
                   "_sys_root_resource_type=xxx.resource.type.vm"
               ],
               "description":"ecs-f680",
               "locked":false,
               "config_drive":"",
               "tenant_id":"edcb94a885a84ed3a3fdf8ea4d2741da",
               "user_id":"61ee747d36bf421fa25c51a3b9565046",
               "os-extended-volumes:volumes_attached":[
                   {
                       "device":"/dev/sda",
                       "bootIndex":"0",
                       "id":"3721b948-9c2f-4980-90ad-b2a16811f58c",
                       "delete_on_termination":"false"
                   }
               ],
               "OS-EXT-STS:task_state":null,
               "OS-EXT-STS:power_state":4,
               "OS-EXT-STS:vm_state":"stopped",
               "OS-EXT-SRV-ATTR:host":"az1.dc1",
               "OS-EXT-SRV-ATTR:instance_name":"instance-00137937",
               "OS-EXT-SRV-ATTR:hypervisor_hostname":"nova001@248",
               "OS-DCF:diskConfig":"MANUAL",
               "OS-EXT-AZ:availability_zone":"az1-dc1",
               "os:scheduler_hints":{
               },
               "OS-EXT-SRV-ATTR:root_device_name":"/dev/sda",
               "OS-EXT-SRV-ATTR:ramdisk_id":"8999878c-4a62-4026-92be-1743ff3a5daf",
               "OS-EXT-SRV-ATTR:user_data":"IyEvYmluL2Jhc2gKZWNobyAncm9vdDokNiR5aG9aeFIkVE00OWlwSGQ2OEFWcjlTMTFXNEZrZmFYTENVbEkvd0xVTmdSVjhOb0dCem5WOWFsU1lEN0ZNSHc0VmtwdU9GOERyLncudGUzVmRHLnVmY005elVZSDEnIHwgY2hwYXNzd2QgLWU7",
               "OS-SRV-USG:launched_at":"2018-08-13T13:38:53.000000",
               "OS-EXT-SRV-ATTR:kernel_id":"",
               "OS-EXT-SRV-ATTR:launch_index":0,
               "host_status":"UP",
               "OS-EXT-SRV-ATTR:reservation_id":"r-7e2g78rq",
               "OS-EXT-SRV-ATTR:hostname":"ecs-f680",
               "sys_tags":[
                   {
                       "key":"_sys_enterprise_project_id",
                       "value":"441d5677-b76a-4dd4-a97a-ef7fd633c095"
                   }
               ],
               "security_groups":[
                   {
                       "name":"test"
                   }
               ]
           },
           {
               "fault":null,
               "id":"fb70fed9-5774-44a7-ad4a-af3ea2c2da61",
               "name":"ecs-3993",
               "addresses":{
                   "00159d7d-b3c3-4108-8bc4-6658814e6422":[
                       {
                           "version":"4",
                           "addr":"192.168.20.83",
                           "OS-EXT-IPS-MAC:mac_addr":"fa:16:3e:a9:8d:88",
                           "OS-EXT-IPS:port_id":"579ab762-bf89-435e-80ad-a8bdd25119c5",
                           "OS-EXT-IPS:type":"fixed"
                       }
                   ]
               },
               "flavor":{
                   "disk":"0",
                   "vcpus":"2",
                   "ram":"1024",
                   "id":"c3.large.2",
                   "name":"c3.large.2"
               },
               "accessIPv4":"",
               "accessIPv6":"",
               "status":"SHUTOFF",
               "image":{
                   "id":"1ce5800a-e487-4c1b-b264-3353a39e2b4b"
               },
               "hostId":"f92345b97fd291f67a29ed735a82a8983f370175d2ba3d18d66893f4",
               "updated":"2018-08-14T03:01:03Z",
               "created":"2018-08-13T13:38:02Z",
               "metadata":{
                   "metering.image_id":"af60e0d5-6952-4f3d-b0ed-31bb19d4a692",
                   "metering.imagetype":"gold",
                   "metering.resourcespeccode":"c3.large.2.linux",
                   "image_name":"HEC_Public_Cloudinit_CentOS_7.4_64bit",
                   "metering.resourcetype":"1",
                   "os_bit":"64",
                   "vpc_id":"00159d7d-b3c3-4108-8bc4-6658814e6422",
                   "os_type":"Linux",
                   "charging_mode":"0"
               },
               "tags":[
                  "combined_order_id=CBRCS231010102024YL8962"
               ],
               "description":"ecs-3993",
               "locked":false,
               "config_drive":"",
               "tenant_id":"edcb94a885a84ed3a3fdf8ea4d2741da",
               "user_id":"eb4698fe015848e9a3e86cc9956e54fa",
               "key_name":"KeyPair-3b38",
               "os-extended-volumes:volumes_attached":[
                   {
                       "device":"/dev/sda",
                       "bootIndex":"0",
                       "id":"85bfbc4f-7733-419a-b171-c00585abf926",
                       "delete_on_termination":"false"
                   }
               ],
               "OS-EXT-STS:task_state":null,
               "OS-EXT-STS:power_state":4,
               "OS-EXT-STS:vm_state":"stopped",
               "OS-EXT-SRV-ATTR:host":"az1.dc1",
               "OS-EXT-SRV-ATTR:instance_name":"instance-00137936",
               "OS-EXT-SRV-ATTR:hypervisor_hostname":"nova001@248",
               "OS-DCF:diskConfig":"MANUAL",
               "OS-EXT-AZ:availability_zone":"az1-dc1",
               "os:scheduler_hints":{
               },
               "OS-EXT-SRV-ATTR:root_device_name":"/dev/sda",
               "OS-EXT-SRV-ATTR:ramdisk_id":"8999878c-4a25-4014-92be-1743ff3a5daf",
               "OS-SRV-USG:launched_at":"2018-08-13T13:38:24.000000",
               "OS-EXT-SRV-ATTR:kernel_id":"",
               "OS-EXT-SRV-ATTR:launch_index":0,
               "host_status":"UP",
               "OS-EXT-SRV-ATTR:reservation_id":"r-uzsewxii",
               "OS-EXT-SRV-ATTR:hostname":"ecs-3993",
               "sys_tags":[
                   {
                       "key":"_sys_enterprise_project_id",
                       "value":"441d5677-b76a-4dd4-a97a-ef7fd633c095"
                   }
               ],
               "security_groups":[
                   {
                       "name":"test"
                   },
                   {
                       "name":"default"
                   }
               ]
           },
           {
               "fault":null,
               "id":"e3d3f219-b445-4a7a-8f00-e31412481f8c",
               "name":"ecs-1f30",
               "addresses":{
                   "00159d7d-b3c3-4108-8bc4-6658814e6422":[
                       {
                           "version":"4",
                           "addr":"192.168.20.197",
                           "OS-EXT-IPS-MAC:mac_addr":"fa:16:3e:41:5a:32",
                           "OS-EXT-IPS:port_id":"cfa2e055-54fb-427a-bde4-128bda47ae5c",
                           "OS-EXT-IPS:type":"fixed"
                       }
                   ]
               },
               "flavor":{
                   "disk":"0",
                   "vcpus":"2",
                   "ram":"1024",
                   "id":"c3.large.2",
                   "name":"c3.large.2"
               },
               "accessIPv4":"",
               "accessIPv6":"",
               "status":"ACTIVE",
               "image":{
                   "id":"1ce5800a-e487-4c1b-b264-3353a39e2b4b"
               },
               "progress":0,
               "hostId":"f92345b97fd291f67a29ed735a82a8983f370175d2ba3d18d66893f4",
               "updated":"2018-08-15T08:16:01Z",
               "created":"2018-08-13T11:57:29Z",
               "metadata":{
                   "sadfasfasf":"sdffffd",
                   "metering.order_id":"CS180813193577ORO",
                   "metering.imagetype":"gold",
                   "metering.resourcespeccode":"c3.large.2.win",
                   "metering.image_id":"65cb40e6-f67e-4bef-a1e7-808166a5999d",
                   "image_name":"HEC_Public_Windows2008R2_Ent_64bit40G_English",
                   "aaaaaa":"0",
                   "metering.resourcetype":"1",
                   "aaaa":"0",
                   "metering.product_id":"00301-146042-0--0",
                   "os_bit":"64",
                   "vpc_id":"00159d7d-b3c3-4108-8bc4-6658814e6422",
                   "os_type":"Windows",
                   "charging_mode":"1"
               },
               "tags":[
                   "_sys_root_resource_id=4514d9b0-d611-4744-bdf9-60802fd5198a",
                   "_sys_root_resource_type=xxx.resource.type.vm"
               ],
               "description":"ecs-1f30",
               "locked":false,
               "config_drive":"",
               "tenant_id":"edcb94a885a84ed3a3fdf8ea4d2741da",
               "user_id":"bb7f23e27e7e46f3aaceb5f53a158bdc",
               "key_name":"Autotest_Init_TC_OriginalAPI_Create_Keypairs_02_keypair",
               "os-extended-volumes:volumes_attached":[
                   {
                       "device":"/dev/sda",
                       "bootIndex":"0",
                       "id":"5043f66b-a0d8-4eb2-8c48-49976bcdc253",
                       "delete_on_termination":"false"
                   }
               ],
               "OS-EXT-STS:task_state":null,
               "OS-EXT-STS:power_state":1,
               "OS-EXT-STS:vm_state":"active",
               "OS-EXT-SRV-ATTR:host":"az1.dc1",
               "OS-EXT-SRV-ATTR:instance_name":"instance-0013772d",
               "OS-EXT-SRV-ATTR:hypervisor_hostname":"nova001@248",
               "OS-DCF:diskConfig":"MANUAL",
               "OS-EXT-AZ:availability_zone":"az1-dc1",
               "os:scheduler_hints":{
               },
               "OS-EXT-SRV-ATTR:root_device_name":"/dev/sda",
               "OS-EXT-SRV-ATTR:ramdisk_id":"8999878c-4a62-4014-92be-1743ff3a5daf",
               "OS-SRV-USG:launched_at":"2018-08-13T11:57:53.576640",
               "OS-EXT-SRV-ATTR:kernel_id":"",
               "OS-EXT-SRV-ATTR:launch_index":0,
               "host_status":"UP",
               "OS-EXT-SRV-ATTR:reservation_id":"r-xmjj4pnm",
               "OS-EXT-SRV-ATTR:hostname":"ecs-1f30",
               "sys_tags":[
                   {
                       "key":"_sys_enterprise_project_id",
                       "value":"441d5677-b76a-4dd4-a97a-ef7fd633c095"
                   }
               ],
               "security_groups":[
                   {
                       "name":"default"
                   }
               ]
           }
       ]
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
