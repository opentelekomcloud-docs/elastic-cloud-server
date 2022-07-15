:original_name: en-us_topic_0065817688.html

.. _en-us_topic_0065817688:

Rebuilding an ECS
=================

Function
--------

This API is used to rebuild an ECS.

You can use the original image or another image to rebuild an ECS. This API supports different OSs.

This API is native from the community for defcore tests.

If you are required to reinstall or change an ECS OS, ECS APIs are recommended. For details, see "Reinstalling an ECS OS (Using an Image with Cloud-Init Installed)" and "Changing an OS (Using an Image with Cloud-Init Installed)".

Constraints
-----------

-  ECSs in the error state cannot be rebuilt.
-  The password cannot be set during the rebuilding.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

:ref:`Table 1 <en-us_topic_0065817688__en-us_topic_0058745339_table46110007>` describes the parameters in the URI.

.. _en-us_topic_0065817688__en-us_topic_0058745339_table46110007:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0065817688__en-us_topic_0058745339_table44724688204850>` describes the request parameters.

.. _en-us_topic_0065817688__en-us_topic_0058745339_table44724688204850:

.. table:: **Table 2** Request parameter

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                            |
   +===========+===========+========+========================================================================================================================+
   | rebuild   | Yes       | Object | Rebuilds an ECS. For details, see :ref:`Table 3 <en-us_topic_0065817688__en-us_topic_0058745339_table59377750205027>`. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817688__en-us_topic_0058745339_table59377750205027:

.. table:: **Table 3** **rebuild** parameters

   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                                                         |
   +====================+=================+=================+=====================================================================================================================================+
   | name               | No              | String          | Specifies the name of the rebuilt ECS.                                                                                              |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 | The value contains 1 to 254 characters.                                                                                             |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | metadata           | No              | Object          | Specifies the metadata of the rebuilt ECS.                                                                                          |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | imageRef           | Yes             | String          | Specifies the image ID or URL.                                                                                                      |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | adminPass          | No              | String          | Specifies the password for logging in to the rebuilt ECS. This parameter does not take effect.                                      |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | OS-DCF:diskConfig  | No              | String          | Not supported                                                                                                                       |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | preserve_ephemeral | No              | Boolean         | Specifies whether to retain the temporary disk. This parameter is not supported.                                                    |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | key_name           | No              | String          | Specifies the key pair name. If the value is null, the existing key pair is left blank.                                             |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 | This parameter is supported in microversion 2.54 and later.                                                                         |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | user_data          | No              | String          | Specifies the user data to be injected during the ECS creation. This is an extended attribute. Text and text files can be injected. |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 | .. note::                                                                                                                           |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 |    -  The content of **user_data** must be encoded with base64.                                                                     |
   |                    |                 |                 |    -  The maximum size of the content to be injected (before encoding) is 32 KB.                                                    |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 | For more information about the user data to be injected, see "Injecting User Data into ECSs" in *Elastic Cloud Server User Guide*.  |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 | Examples                                                                                                                            |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 | Before base64 encoding:                                                                                                             |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 | -  Linux                                                                                                                            |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 |    .. code-block::                                                                                                                  |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 |       #! /bin/bash                                                                                                                  |
   |                    |                 |                 |       echo user_test >> /home/user.txt                                                                                              |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 | -  Windows                                                                                                                          |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 |    .. code-block::                                                                                                                  |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 |       rem cmd                                                                                                                       |
   |                    |                 |                 |       echo 111 > c:\aaa.txt                                                                                                         |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 | After base64 encoding:                                                                                                              |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 | -  Linux                                                                                                                            |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 |    .. code-block::                                                                                                                  |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 |       IyEgL2Jpbi9iYXNoDQplY2hvIHVzZXJfdGVzdCAmZ3Q7Jmd0OyAvaG9tZS91c2VyLnR4dA==                                                      |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 | -  Windows                                                                                                                          |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 |    .. code-block::                                                                                                                  |
   |                    |                 |                 |                                                                                                                                     |
   |                    |                 |                 |       cmVtIGNtZAplY2hvIDExMSA+IGM6XGFhYS50eHQ=                                                                                      |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 4 <en-us_topic_0065817688__en-us_topic_0058745339_table49173801205341>` describes the response parameters.

.. _en-us_topic_0065817688__en-us_topic_0058745339_table49173801205341:

.. table:: **Table 4** Response parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                |
   +=======================+=======================+============================================================================================================================+
   | status                | String                | Specifies the ECS status.                                                                                                  |
   |                       |                       |                                                                                                                            |
   |                       |                       | Values:                                                                                                                    |
   |                       |                       |                                                                                                                            |
   |                       |                       | -  **ACTIVE**                                                                                                              |
   |                       |                       | -  **REBOOT**                                                                                                              |
   |                       |                       | -  **HARD_REBOOT**                                                                                                         |
   |                       |                       | -  **REBUILD**                                                                                                             |
   |                       |                       | -  **MIGRATING**                                                                                                           |
   |                       |                       | -  **BUILD**                                                                                                               |
   |                       |                       | -  **SHUTOFF**                                                                                                             |
   |                       |                       | -  **RESIZE**                                                                                                              |
   |                       |                       | -  **VERIFY_RESIZE**                                                                                                       |
   |                       |                       | -  **ERROR**                                                                                                               |
   |                       |                       | -  **DELETED**                                                                                                             |
   |                       |                       |                                                                                                                            |
   |                       |                       | For details, see :ref:`ECS Statuses <en-us_topic_0178420672>`.                                                             |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | updated               | String                | Specifies the time when the ECS was updated last time.                                                                     |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | hostId                | String                | Specifies the ID of the host on which the ECS is deployed.                                                                 |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | addresses             | Array of objects      | Specifies the network attribute of the ECS.                                                                                |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | links                 | Array of objects      | Describes the ECS.                                                                                                         |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | image                 | Object                | Specifies the ECS image information. For the ECS that boots from a volume, the value is left blank.                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | flavor                | Object                | Specifies the ECS flavor.                                                                                                  |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | Specifies the ECS ID in UUID format.                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | user_id               | String                | Specifies the user UUID of the ECS.                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the ECS name.                                                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                | Specifies the UUID of the tenant who owns the ECS.                                                                         |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | OS-DCF:diskConfig     | String                | Specifies the diskConfig type. It is an extended attributed.                                                               |
   |                       |                       |                                                                                                                            |
   |                       |                       | -  **MANUAL**: The image space cannot be expanded.                                                                         |
   |                       |                       | -  **AUTO**: The image space on the system disk will be automatically expanded to keep the same as that set in the flavor. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | accessIPv4            | String                | Discarded                                                                                                                  |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | accessIPv6            | String                | Discarded                                                                                                                  |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | progress              | String                | Specifies the ECS creation progress.                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | metadata              | Object                | Specifies the ECS metadata.                                                                                                |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/servers/{server_id}/action
   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

.. code-block::

   {
       "rebuild" : {
           "imageRef" : "3ed456f5-3d8f-4383-a6c9-312032afcd1a",
           "name" : "rebuildName",
          "metadata" : {
               "rebuild" : "rebuild vm"
           }
       }
   }

Example Response
----------------

.. code-block::

   {
       "server": {
           "tenant_id": "7459f9935ed2422eb9800fea1d4d9378",
           "image": {
               "links": [
                   {
                       "rel": "bookmark",
                       "href": "https://xxx/7459f9935ed2422eb9800fea1d4d9378/images/3ed456f5-3d8f-4383-a6c9-312032afcd1a"
                   }
               ],
               "id": "3ed456f5-3d8f-4383-a6c9-312032afcd1a"
           },
           "accessIPv4": "",
           "addresses": {
               "443dd9e3-c165-4764-ad92-b17fcf12a3eb": [
                   {
                       "addr": "192.168.0.119",
                       "version": 4
                   }
               ]
           },
           "metadata": {
               "name": "rebuildName"
           },
           "accessIPv6": "",
           "created": "2016-09-19T01:13:26Z",
           "hostId": "fd16ebd9c2629e8595875cc1e1400fa67f392431d7937fcc9cf37671",
           "adminPass": "qGVjnEjY3ZoY",
           "flavor": {
               "links": [
                   {
                       "rel": "bookmark",
                       "href": "https://xxx/7459f9935ed2422eb9800fea1d4d9378/flavors/normal1"
                   }
               ],
               "id": "normal1"
           },
           "OS-DCF:diskConfig": "MANUAL",
           "user_id": "ed2965d80d394be0b41e56f50ac650ca",
           "name": "rebuildName",
           "progress": 0,
           "links": [
               {
                   "rel": "self",
                   "href": "https://xxx/v2/7459f9935ed2422eb9800fea1d4d9378/servers/ea681a24-9b24-4f49-98ef-8e1f73acf19e"
               },
               {
                   "rel": "bookmark",
                   "href": "https://xxx/7459f9935ed2422eb9800fea1d4d9378/servers/ea681a24-9b24-4f49-98ef-8e1f73acf19e"
               }
           ],
           "id": "ea681a24-9b24-4f49-98ef-8e1f73acf19e",
           "updated": "2016-09-19T07:22:05Z",
           "status": "REBUILD"
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
