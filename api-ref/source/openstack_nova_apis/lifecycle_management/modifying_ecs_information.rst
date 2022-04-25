:original_name: en-us_topic_0020212692.html

.. _en-us_topic_0020212692:

Modifying ECS Information
=========================

Function
--------

This API is used to modify ECS information. Only the name and description of an ECS can be modified.

URI
---

PUT /v2.1/{project_id}/servers/{server_id}

PUT /v2/{project_id}/servers/{server_id}

:ref:`Table 1 <en-us_topic_0020212692__table44564854>` describes the parameters in the URI.

.. _en-us_topic_0020212692__table44564854:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0020212692__table13100926>` describes the request parameters.

.. _en-us_topic_0020212692__table13100926:

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                      |
   +===========+===========+========+==================================================================================================================+
   | server    | Yes       | Object | Specifies the ECS data structure. For details, see :ref:`Table 3 <en-us_topic_0020212692__table26827213163326>`. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212692__table26827213163326:

.. table:: **Table 3** **server** field description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                   |
   +=================+=================+=================+===============================================================+
   | name            | No              | String          | Specifies the name of the modified ECS.                       |
   |                 |                 |                 |                                                               |
   |                 |                 |                 | The length is greater than 0 and less than 256                |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------+
   | description     | No              | String          | Describes the ECS. The value contains a maximum of 255 bytes. |
   |                 |                 |                 |                                                               |
   |                 |                 |                 | This parameter is supported in microversion 2.19 and later.   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------+

Response
--------

:ref:`Table 4 <en-us_topic_0020212692__table44736746>` describes the response parameters.

.. _en-us_topic_0020212692__table44736746:

.. table:: **Table 4** Response parameters

   +-----------+--------+-----------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                         |
   +===========+========+=====================================================================================================+
   | server    | Object | Specifies ECS information. For details, see :ref:`Table 5 <en-us_topic_0020212692__table11253402>`. |
   +-----------+--------+-----------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212692__table11253402:

.. table:: **Table 5** **server** field description

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================================================================+
   | tenant_id             | String                | Specifies the tenant or project ID.                                                                                                                                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image                 | String                | Specifies the image ID.                                                                                                                                                                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | accessIPv4            | String                | Reserved                                                                                                                                                                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | addresses             | Object                | Specifies the attributed network information of the ECS.                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | The structure is Map<String, Object>.                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | For details, see :ref:`Table 6 <en-us_topic_0020212692__table1656029015527>`.                                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata              | Object                | Specifies the ECS metadata.                                                                                                                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | accessIPv6            | String                | Reserved                                                                                                                                                                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created               | String                | Specifies the time when the ECS was created. The time is in the format of "2019-05-22T03:19:19Z".                                                                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hostId                | String                | Specifies the host ID of the ECS.                                                                                                                                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavor                | Object                | Specifies the ECS flavor. For details, see :ref:`Table 7 <en-us_topic_0020212692__table19588408>`.                                                                                               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-DCF:diskConfig     | String                | Specifies the disk configuration mode. This is an extended attribute. This field is valid for the ECS started using an image.                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_id               | String                | Specifies the ID of the user to which an ECS belongs.                                                                                                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the modified name of the ECS.                                                                                                                                                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | progress              | Integer               | Reserved                                                                                                                                                                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | links                 | Array of Object       | Specifies ECS shortcut links. For details, see :ref:`Table 8 <en-us_topic_0020212692__table64121649>`.                                                                                           |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | Specifies the unique ID of an ECS.                                                                                                                                                               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated               | String                | Specifies the time when the ECS was updated last time.                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | The time is in the format of "2019-05-22T03:19:19Z".                                                                                                                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | locked                | Boolean               | Specifies the ECS lock status, which is **True** when the ECS is locked and **False** when the ECS is unlocked.                                                                                  |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | This parameter is supported in microversion 2.9 and later.                                                                                                                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Describes the ECS.                                                                                                                                                                               |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | This parameter is supported in microversion 2.19 and later.                                                                                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Array of strings      | Specifies ECS tags.                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | This parameter is supported in microversion 2.26 and later. If the microversion is not used for query, the response does not contain the **tags** field.                                         |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | Tag functions have been upgraded on the public cloud. After the upgrade, the tag values returned by the system comply with the following rules:                                                  |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | -  The key and value of a tag are connected using an equal sign (=), for example, key=value.                                                                                                     |
   |                       |                       | -  If the value is empty, only the key is returned.                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | -  The key and value of a tag are connected using an equal sign (=), for example, key=value.                                                                                                     |
   |                       |                       | -  If the value is empty, only the key is returned.                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | For more details about upgraded tag functions, see :ref:`Tag Types <en-us_topic_0065817686>`.                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                | Specifies the ECS status.                                                                                                                                                                        |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | Options:                                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | **ACTIVE**, **BUILD**, **ERROR**, **HARD_REBOOT**, **MIGRATING**, **REBOOT**, **RESIZE**, **REVERT_RESIZE**, **SHELVED**, **SHELVED_OFFLOADED**, **SHUTOFF**, **UNKNOWN**, and **VERIFY_RESIZE** |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | For details, see :ref:`ECS Statuses <en-us_topic_0178420672>`.                                                                                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212692__table1656029015527:

.. table:: **Table 6** Data structure of the network which an ECS accesses

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                             |
   +=======================+=======================+=========================================================================================+
   | addr                  | String                | Specifies the IP address.                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | version               | Integer               | Specifies the type of an IP address. The value of this parameter can be **4** or **6**. |
   |                       |                       |                                                                                         |
   |                       |                       | -  **4**: The type of the IP address is IPv4.                                           |
   |                       |                       | -  **6**: The type of the IP address is IPv6.                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+

.. _en-us_topic_0020212692__table19588408:

.. table:: **Table 7** **flavor** field description

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                     |
   +=======================+=======================+=================================================================================================================================+
   | id                    | String                | Specifies the ECS ID.                                                                                                           |
   |                       |                       |                                                                                                                                 |
   |                       |                       | This parameter is not supported in microversion 2.47 and later.                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | links                 | Array of objects      | Specifies shortcut links for ECS types. For details, see :ref:`Table 8 <en-us_topic_0020212692__table64121649>`.                |
   |                       |                       |                                                                                                                                 |
   |                       |                       | This parameter is not supported in microversion 2.47 and later.                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | vcpus                 | Integer               | Specifies the number of vCPUs in the ECS flavor.                                                                                |
   |                       |                       |                                                                                                                                 |
   |                       |                       | This parameter is supported in microversion 2.47 and later.                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | ram                   | Integer               | Specifies the memory size (MB) in the ECS flavor.                                                                               |
   |                       |                       |                                                                                                                                 |
   |                       |                       | This parameter is supported in microversion 2.47 and later.                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | disk                  | Integer               | Specifies the system disk size in the ECS flavor. Value **0** indicates that the disk size is not limited.                      |
   |                       |                       |                                                                                                                                 |
   |                       |                       | This parameter is supported in microversion 2.47 and later.                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | ephemeral             | Integer               | Reserved                                                                                                                        |
   |                       |                       |                                                                                                                                 |
   |                       |                       | This parameter is supported in microversion 2.47 and later.                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | swap                  | Integer               | Reserved                                                                                                                        |
   |                       |                       |                                                                                                                                 |
   |                       |                       | This parameter is supported in microversion 2.47 and later.                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | original_name         | String                | Specifies the name of the ECS flavor.                                                                                           |
   |                       |                       |                                                                                                                                 |
   |                       |                       | This parameter is supported in microversion 2.47 and later.                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | extra_specs           | Object                | Indicates an extended flavor field. For details, see :ref:`os_extra_specs (flavor) Field Description <en-us_topic_0170710254>`. |
   |                       |                       |                                                                                                                                 |
   |                       |                       | This parameter is supported in microversion 2.47 and later.                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212692__table64121649:

.. table:: **Table 8** **links** field description

   ========= ====== ========================================
   Parameter Type   Description
   ========= ====== ========================================
   rel       String Specifies the shortcut link marker name.
   href      String Specifies the shortcut link.
   ========= ====== ========================================

Example Request
---------------

.. code-block::

   PUT https://{endpoint}/v2/{project_id}/servers/{server_id}
   PUT https://{endpoint}/v2.1/{project_id}/servers/{server_id}

.. code-block::

   {
       "server": {
           "name": "new-server-test"
       }
   }

Example Response
----------------

.. code-block::

   {
     "server": {
       "tenant_id": "7910a6e50b80402ba028c8d96c1b31fe",
       "image": "",
       "accessIPv4": "",
       "addresses": {
         "03be5c1e-e05d-4905-a105-c3bd9b730bdc": [
           {
             "addr": "192.168.0.72",
             "version": 4
           }
         ]
       },
       "metadata": {},
       "accessIPv6": "",
       "created": "2018-05-17T03:15:48Z",
       "hostId": "7dc82f6b1d406200fc63e395cf4829cbffcb49de0e9c75c5773f201f",
       "flavor": {
         "links": [
           {
             "rel": "bookmark",
             "href": "https://None/7910a6e50b80402ba028c8d96c1b31fe/flavors/c3.1U1G"
           }
         ],
         "id": "c3.1U1G"
       },
       "OS-DCF:diskConfig": "MANUAL",
       "user_id": "d698a78532ca430f8daec1858f2b500e",
       "name": "new-server-test",
       "progress": 0,
       "links": [
         {
           "rel": "self",
           "href": "https://None/v2/7910a6e50b80402ba028c8d96c1b31fe/servers/1a19ef4f-be0a-4526-bf2f-14b4464d536a"
         },
         {
           "rel": "bookmark",
           "href": "https://None/7910a6e50b80402ba028c8d96c1b31fe/servers/1a19ef4f-be0a-4526-bf2f-14b4464d536a"
         }
       ],
       "id": "1a19ef4f-be0a-4526-bf2f-14b4464d536a",
       "updated": "2018-05-21T00:36:27Z",
       "status": "ACTIVE"
     }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
