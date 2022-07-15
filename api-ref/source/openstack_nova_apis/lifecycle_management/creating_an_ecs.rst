:original_name: en-us_topic_0068473331.html

.. _en-us_topic_0068473331:

Creating an ECS
===============

Function
--------

This API is used to create ECS.

This API does not support automatic rollback after creating an ECS failed. If automatic rollback is required, call the API POST /v1/{project_id}/cloudservers. For details, see :ref:`Creating an ECS <en-us_topic_0020212668>`.

URI
---

POST /v2.1/{project_id}/servers

POST /v2/{project_id}/servers

:ref:`Table 1 <en-us_topic_0068473331__en-us_topic_0057972661_table47145209>` describes the parameters in the URI.

.. _en-us_topic_0068473331__en-us_topic_0057972661_table47145209:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

.. note::

   Alias of the API for creating ECSs: /v2/{project_id}/os-volumes_boot

   This calling mode can only be used in OpenStack client.

Constraints
-----------

#. This API is native, which does not support the creation of ECSs using full-ECS images. To use full-ECS images to create ECSs, refer to :ref:`Creating an ECS <en-us_topic_0020212668>`.

#. During the creation of an ECS using this API, you cannot bind an EIP to the ECS. If you want to create an ECS and bind an EIP to it, refer to :ref:`Creating an ECS <en-us_topic_0020212668>`.

#. Parameter **port** in the three network parameters (**port**, **uuid**, and **fixed_ip**) has the highest priority. If parameter **fixed_ip** is set, you must specify the UUID.

#. A file injection failure will result in the ECS creation failure.

#. The following restrictions apply when you create ECSs using an image:

   a. You cannot create an ECS on a specified host.
   b. If a tenant backs up a disk in an ECS, the disk can be deleted only after the tenant deletes all the snapshots of the disk.
   c. The flavors with different resource types cannot be adjusted if you adjust the specifications of an ECS created using an image.

#. Native APIs /v2/{project_id}/servers and /v2.1/{project_id}/servers provided by the public cloud platform is developed based on and compatible with the community-version native OpenStack API.

   Compared with the community-version native API, this API has the following restrictions when you create an ECS using a specified image:

   -  Community-version native OpenStack API: creates an ECS using the local disk by default.
   -  Native API provided by the public cloud platform: creates an ECS using the shared storage as the system disk.

   Specifically, when you use the native API to create an ECS:

   a. You can query information about the disks attached to the ECS.
   b. The ECS system disk uses the EVS disk quota.
   c. You cannot query ECSs created based on a specified image using the image filtering function.

#. When you create an ECS with a specified disk, ensure that the disk and the ECS are in the same AZ.

#. The **device_name** field configured in **block_device_mapping_v2** during the ECS creation does not take effect. The system generates a device name by default.

#. ECSs cannot be created in networks with **provider:network_type** set to **geneve**.

   .. note::

      **provider:network_type** being set to **geneve** indicates the internal high-speed network for BMSs.

#. If your ECS is remotely logged in using a key, use the **key_name** parameter. If your ECS is remotely logged in using a password, use the **adminPass** parameter. Linux ECSs support **user_data** for injection. Windows ECSs support **admin_pass** for injection.

#. If the image based on which the ECS is created uses the native OpenStack API, ensure that the specified AZ and system disk capacity and type used when the ECS is created are the same as those used when the image is created. Otherwise, the ECS creation will fail.

Request
-------

:ref:`Table 2 <en-us_topic_0068473331__en-us_topic_0057972661_table40519951>` describes the request parameters.

.. _en-us_topic_0068473331__en-us_topic_0057972661_table40519951:

.. table:: **Table 2** Request parameters

   +--------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory | Type   | Description                                                                                                                                                                               |
   +====================+===========+========+===========================================================================================================================================================================================+
   | server             | Yes       | Object | Specifies the ECS information. For details, see :ref:`Table 3 <en-us_topic_0068473331__en-us_topic_0057972661_table64008488102639>`.                                                      |
   +--------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os:scheduler_hints | No        | Object | Specifies the ECS scheduling information. For details, see :ref:`Table 8 <en-us_topic_0068473331__en-us_topic_0057972661_table12534817105641>`. This parameter is not available for BMSs. |
   +--------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0068473331__en-us_topic_0057972661_table64008488102639:

.. table:: **Table 3** **server** parameters

   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Mandatory       | Type               | Description                                                                                                                                                                                                                                                                                                                                                                 |
   +=========================+=================+====================+=============================================================================================================================================================================================================================================================================================================================================================================+
   | imageRef                | No              | String             | Specifies the ECS image ID or URL.                                                                                                                                                                                                                                                                                                                                          |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | -  Example image ID: 3b8d6fef-af77-42ab-b8b7-5a7f0f0af8f2                                                                                                                                                                                                                                                                                                                   |
   |                         |                 |                    | -  Example image URL: http://glance.openstack.example.com/images/3b8d6fef-af77-42ab-b8b7-5a7f0f0af8f2                                                                                                                                                                                                                                                                       |
   |                         |                 |                    | -  If you use a specified disk as the system disk to create an ECS, this parameter is not required. If you do not use a disk to create an ECS, you must set a valid UUID. Otherwise, the API will return error code **400**.                                                                                                                                                |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | .. note::                                                                                                                                                                                                                                                                                                                                                                   |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |    -  Certain ECS flavors cannot support all public images provided on the public cloud platform. To obtain the images supported by an ECS flavor, log in to the management console, view the images displayed on the **Create ECS** page, and obtain the image IDs on the **Image Management Service** page.                                                               |
   |                         |                 |                    |    -  If the creation fails, modify the parameter settings.                                                                                                                                                                                                                                                                                                                 |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavorRef               | Yes             | String             | Specifies the flavor ID or URL.                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | For example: c3.2xlarge                                                                                                                                                                                                                                                                                                                                                     |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                    | Yes             | String             | Specifies the ECS name. The value contains 1 to 255 characters.                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | .. note::                                                                                                                                                                                                                                                                                                                                                                   |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |    ECS hostnames comply with `RFC952 <https://tools.ietf.org/html/rfc952>`__ and `RFC1123 <https://tools.ietf.org/html/rfc1123>`__ naming rules. It is recommended that you configure hostnames using digits, letters (case sensitive), and hyphens (-). Underscores (_) are converted into hyphens (-) by default.                                                         |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata                | No              | Map<String,String> | Specifies the ECS metadata. For details, see :ref:`Table 4 <en-us_topic_0068473331__en-us_topic_0057972661_table2373623012315>`.                                                                                                                                                                                                                                            |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | -  The key contains 1 to 255 characters.                                                                                                                                                                                                                                                                                                                                    |
   |                         |                 |                    | -  The value contains 0 to 255 characters.                                                                                                                                                                                                                                                                                                                                  |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | adminPass               | No              | String             | Specifies the initial login password of the administrator account for logging in to an ECS using password authentication. The Linux administrator is **root**, and the Windows administrator is **Administrator**.                                                                                                                                                          |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | block_device_mapping_v2 | No              | Array of objects   | Indicates the V2 API for specifying the ECS storage device. This is an extended attribute. This is the storage resource API of the new version. You are not allowed to create ECSs in batches when the volume is specified. For details, see :ref:`Table 5 <en-us_topic_0068473331__en-us_topic_0057972661_table15044407105358>`. This parameter is not available for BMSs. |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | config_drive            | No              | String             | Specifies the config_drive disk to be attached to the ECS during the ECS creation for transferring information to the ECS. This is an extended attribute.                                                                                                                                                                                                                   |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | This function is not supported.                                                                                                                                                                                                                                                                                                                                             |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_groups         | No              | Array of objects   | Specifies the security group that the ECS belongs to. This parameter is an extended attribute. The default parameter value is **default**.                                                                                                                                                                                                                                  |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | This parameter is valid when you create an ECS on a specified network. For an existing port, the requested security groups are invalid. For details, see :ref:`Table 6 <en-us_topic_0068473331__en-us_topic_0057972661_table16920677105453>`.                                                                                                                               |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | networks                | Yes             | Array of objects   | Specifies information about the ECS NIC. This parameter is an extended attribute. This parameter must be specified if multiple tenant networks are used. For details, see :ref:`Table 7 <en-us_topic_0068473331__en-us_topic_0057972661_table9995892105551>`.                                                                                                               |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_name                | No              | String             | Specifies the name of a key pair. This parameter is an extended attribute.                                                                                                                                                                                                                                                                                                  |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_data               | No              | String             | Specifies the user data to be injected to the ECS during the creation. Text and text files can be injected.                                                                                                                                                                                                                                                                 |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | .. note::                                                                                                                                                                                                                                                                                                                                                                   |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |    -  The content of **user_data** must be encoded with base64.                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |    -  The maximum size of the content to be injected (before encoding) is 32 KB.                                                                                                                                                                                                                                                                                            |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | For more information about the user data to be injected, see "Injecting User Data into ECSs" in *Elastic Cloud Server User Guide*.                                                                                                                                                                                                                                          |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | Examples                                                                                                                                                                                                                                                                                                                                                                    |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | Before base64 encoding:                                                                                                                                                                                                                                                                                                                                                     |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | -  Linux                                                                                                                                                                                                                                                                                                                                                                    |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |    .. code-block::                                                                                                                                                                                                                                                                                                                                                          |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |       #! /bin/bash                                                                                                                                                                                                                                                                                                                                                          |
   |                         |                 |                    |       echo user_test >> /home/user.txt                                                                                                                                                                                                                                                                                                                                      |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | -  Windows                                                                                                                                                                                                                                                                                                                                                                  |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |    .. code-block::                                                                                                                                                                                                                                                                                                                                                          |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |       rem cmd                                                                                                                                                                                                                                                                                                                                                               |
   |                         |                 |                    |       echo 111 > c:\aaa.txt                                                                                                                                                                                                                                                                                                                                                 |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | After base64 encoding:                                                                                                                                                                                                                                                                                                                                                      |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | -  Linux                                                                                                                                                                                                                                                                                                                                                                    |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |    .. code-block::                                                                                                                                                                                                                                                                                                                                                          |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |       IyEgL2Jpbi9iYXNoDQplY2hvIHVzZXJfdGVzdCAmZ3Q7Jmd0OyAvaG9tZS91c2VyLnR4dA==                                                                                                                                                                                                                                                                                              |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | -  Windows                                                                                                                                                                                                                                                                                                                                                                  |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |    .. code-block::                                                                                                                                                                                                                                                                                                                                                          |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |       cmVtIGNtZAplY2hvIDExMSA+IGM6XGFhYS50eHQ=                                                                                                                                                                                                                                                                                                                              |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone       | No              | String             | Specifies the AZ of a specified ECS. This is an extended attribute.                                                                                                                                                                                                                                                                                                         |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | This parameter is mandatory when you create an ECS.                                                                                                                                                                                                                                                                                                                         |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | return_reservation_id   | No              | Boolean            | Specifies whether the reservation IDs of the ECSs created in a batch are returned. This is an extended attribute. You can query the ECSs created this time based on the returned reservation IDs.                                                                                                                                                                           |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | -  **true**: The reservation IDs are returned.                                                                                                                                                                                                                                                                                                                              |
   |                         |                 |                    | -  **false**: The ECS information is returned.                                                                                                                                                                                                                                                                                                                              |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |    .. note::                                                                                                                                                                                                                                                                                                                                                                |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |       When you create ECSs in a batch, this parameter is available.                                                                                                                                                                                                                                                                                                         |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_count               | No              | Integer            | Specifies the minimum number of ECSs that can be created. This is an extended attribute.                                                                                                                                                                                                                                                                                    |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | The default value is **1**.                                                                                                                                                                                                                                                                                                                                                 |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | .. note::                                                                                                                                                                                                                                                                                                                                                                   |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |    When you use a specified image to create ECSs, this parameter is available.                                                                                                                                                                                                                                                                                              |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | max_count               | No              | Integer            | Specifies the maximum number of ECSs that can be created.                                                                                                                                                                                                                                                                                                                   |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | The default value of **max_count** is the same as that of **min_count**.                                                                                                                                                                                                                                                                                                    |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | Note:                                                                                                                                                                                                                                                                                                                                                                       |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | -  The **max_count** value must be greater than or equal to the **min_count** value.                                                                                                                                                                                                                                                                                        |
   |                         |                 |                    | -  If both **min_count** and **max_count** are specified, the number of ECSs that can be created depends on host resources. If host resources permit, you can create a maximum number of ECSs ranging from **min_count** to **max_count** values.                                                                                                                           |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | .. note::                                                                                                                                                                                                                                                                                                                                                                   |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |    When you use a specified image to create ECSs, this parameter is available.                                                                                                                                                                                                                                                                                              |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-DCF:diskConfig       | No              | String             | Specifies the disk configuration mode. The value can be **AUTO** or **MANUAL**.                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | -  **MANUAL**: indicates that the image space of the system disk cannot be expanded.                                                                                                                                                                                                                                                                                        |
   |                         |                 |                    | -  **AUTO**: indicates that the image space of the system disk can be automatically expanded to a value same as that specified in flavor.                                                                                                                                                                                                                                   |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | This function is not supported.                                                                                                                                                                                                                                                                                                                                             |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description             | No              | String             | Specifies the description of an ECS, which is a null string by default. This is an extended attribute.                                                                                                                                                                                                                                                                      |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | This parameter is supported in microversion 2.19 and later.                                                                                                                                                                                                                                                                                                                 |
   |                         |                 |                    |                                                                                                                                                                                                                                                                                                                                                                             |
   |                         |                 |                    | -  Can contain a maximum of 85 characters.                                                                                                                                                                                                                                                                                                                                  |
   |                         |                 |                    | -  Cannot contain special characters, such as < and >.                                                                                                                                                                                                                                                                                                                      |
   +-------------------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0068473331__en-us_topic_0057972661_table2373623012315:

.. table:: **Table 4** **metadata** field description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                 |
   +=================+=================+=================+=============================================================================================+
   | admin_pass      | No              | String          | Specifies the password of user **Administrator** for logging in to a Windows ECS.           |
   |                 |                 |                 |                                                                                             |
   |                 |                 |                 | .. note::                                                                                   |
   |                 |                 |                 |                                                                                             |
   |                 |                 |                 |    This parameter is mandatory when a Windows ECS using password authentication is created. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------+

.. _en-us_topic_0068473331__en-us_topic_0057972661_table15044407105358:

.. table:: **Table 5** **block_device_mapping_v2** parameters

   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type            | Mandatory       | Description                                                                                                                                                                                                                                                                                         |
   +=======================+=================+=================+=====================================================================================================================================================================================================================================================================================================+
   | source_type           | String          | Yes             | Specifies the source type of the volume device. Its value can be **volume**, **image**, **snapshot**, or **blank**.                                                                                                                                                                                 |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                     |
   |                       |                 |                 | If you use a volume to create an ECS, set **source_type** to **volume**. If you use an image to create an ECS, set **source_type** to **image**. If you use a snapshot to create an ECS, set **source_type** to **snapshot**. If you create an empty data volume, set **source_type** to **blank**. |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                     |
   |                       |                 |                 | .. note::                                                                                                                                                                                                                                                                                           |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                     |
   |                       |                 |                 |    If **source_type** is **snapshot** and **boot_index** is 0, the EVS disk of this snapshot must be the system disk.                                                                                                                                                                               |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | destination_type      | String          | No              | Specifies the target type of the disk device. Its value can only be **volume**.                                                                                                                                                                                                                     |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                     |
   |                       |                 |                 | -  **volume**: indicates the volume type.                                                                                                                                                                                                                                                           |
   |                       |                 |                 | -  **local**: indicates the local file, which has not been supported.                                                                                                                                                                                                                               |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | guest_format          | String          | No              | Specifies the local file system format. Its value can be **swap** or **ext4**.                                                                                                                                                                                                                      |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                     |
   |                       |                 |                 | This function is not supported.                                                                                                                                                                                                                                                                     |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | device_name           | String          | No              | Specifies the disk device name.                                                                                                                                                                                                                                                                     |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                     |
   |                       |                 |                 | .. note::                                                                                                                                                                                                                                                                                           |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                     |
   |                       |                 |                 |    This field has been discarded.                                                                                                                                                                                                                                                                   |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                     |
   |                       |                 |                 |    The specified **device_name** does not take effect. The system generates a device name by default.                                                                                                                                                                                               |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | delete_on_termination | Boolean         | No              | Specifies whether disks are deleted when an ECS is deleted. Its default value is **false**.                                                                                                                                                                                                         |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                     |
   |                       |                 |                 | -  **true**: When an ECS is deleted, its disks are deleted.                                                                                                                                                                                                                                         |
   |                       |                 |                 | -  **false**: When an ECS is deleted, its disks are not deleted.                                                                                                                                                                                                                                    |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | boot_index            | String          | No              | Specifies whether it is a boot disk. **0** specifies a boot disk, and **-1** specifies a non-boot disk.                                                                                                                                                                                             |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                     |
   |                       |                 |                 | .. note::                                                                                                                                                                                                                                                                                           |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                     |
   |                       |                 |                 |    If **source_type** of the volume device is **volume**, there must be one **boot_index** whose value is **0**.                                                                                                                                                                                    |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | uuid                  | String          | No              | -  If **source_type** is **volume**, the value of this parameter is the volume UUID.                                                                                                                                                                                                                |
   |                       |                 |                 | -  If **source_type** is **snapshot**, the value of this parameter is the snapshot UUID.                                                                                                                                                                                                            |
   |                       |                 |                 | -  If **source_type** is **image**, the value of this parameter is the image UUID.                                                                                                                                                                                                                  |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_size           | Integer         | No              | Specifies the volume size. The value is an integer. This parameter is mandatory when **source_type** is set to **image** or **blank**, and **destination_type** is set to **volume**.                                                                                                               |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                     |
   |                       |                 |                 | Unit: GB                                                                                                                                                                                                                                                                                            |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_type           | String          | No              | Specifies the volume type. This parameter is recommended when **source_type** is set to **image** and **destination_type** is set to **volume**.                                                                                                                                                    |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0068473331__en-us_topic_0057972661_table16920677105453:

.. table:: **Table 6** **security_groups** parameters

   ========= ========= ====== ==========================================
   Parameter Mandatory Type   Description
   ========= ========= ====== ==========================================
   name      No        String Specifies the security group name or UUID.
   ========= ========= ====== ==========================================

.. _en-us_topic_0068473331__en-us_topic_0057972661_table9995892105551:

.. table:: **Table 7** **networks** parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================================================================+
   | port            | No              | String          | Specifies the network port UUID.                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                  |
   |                 |                 |                 | This parameter must be set when the network UUID is not specified.                                                                                                                                               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | uuid            | No              | String          | Specifies the network UUID.                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                  |
   |                 |                 |                 | This parameter must be set when the network port is not specified.                                                                                                                                               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fixed_ip        | No              | String          | Specifies the fixed IP address. Parameter **port** in the three network parameters (**port**, **uuid**, and **fixed_ip**) has the highest priority. If parameter **fixed_ip** is set, you must specify the UUID. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0068473331__en-us_topic_0057972661_table12534817105641:

.. table:: **Table 8** **os:scheduler_hints** parameters

   +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type             | Description                                                                                                                                                           |
   +====================+=================+==================+=======================================================================================================================================================================+
   | group              | No              | String           | Specifies the anti-affinity group.                                                                                                                                    |
   |                    |                 |                  |                                                                                                                                                                       |
   |                    |                 |                  | The value is in UUID format.                                                                                                                                          |
   |                    |                 |                  |                                                                                                                                                                       |
   |                    |                 |                  | .. note::                                                                                                                                                             |
   |                    |                 |                  |                                                                                                                                                                       |
   |                    |                 |                  |    Ensure that the ECS group uses the anti-affinity policy. You are not advised to use other policies.                                                                |
   +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | different_host     | No              | Array of strings | The function has not been supported, and this field is reserved.                                                                                                      |
   +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | same_host          | No              | Array of strings | The function has not been supported, and this field is reserved.                                                                                                      |
   +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cidr               | No              | String           | The function has not been supported, and this field is reserved.                                                                                                      |
   +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | build_near_host_ip | No              | String           | The function has not been supported, and this field is reserved.                                                                                                      |
   +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenancy            | No              | String           | Specifies whether the ECS is created on a Dedicated Host (DeH) or in a shared pool (default).                                                                         |
   |                    |                 |                  |                                                                                                                                                                       |
   |                    |                 |                  | The value can be **shared** or **dedicated**.                                                                                                                         |
   |                    |                 |                  |                                                                                                                                                                       |
   |                    |                 |                  | -  **shared**: indicates the shared pool.                                                                                                                             |
   |                    |                 |                  | -  **dedicated**: indicates the DeH.                                                                                                                                  |
   |                    |                 |                  |                                                                                                                                                                       |
   |                    |                 |                  | The parameter value also takes effect for ECS query operations.                                                                                                       |
   +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dedicated_host_id  | No              | String           | Specifies the DeH ID.                                                                                                                                                 |
   |                    |                 |                  |                                                                                                                                                                       |
   |                    |                 |                  | This parameter takes effect only when the value of **tenancy** is **dedicated**.                                                                                      |
   |                    |                 |                  |                                                                                                                                                                       |
   |                    |                 |                  | If you do not specify this parameter, the system will automatically assign a DeH to you to deploy ECSs.                                                               |
   |                    |                 |                  |                                                                                                                                                                       |
   |                    |                 |                  | The parameter value also takes effect for ECS query operations.                                                                                                       |
   +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | check_resources    | No              | String           | Specifies whether to check resource sufficiency when creating an ECS. If this parameter is not configured, the system does not check resource sufficiency by default. |
   |                    |                 |                  |                                                                                                                                                                       |
   |                    |                 |                  | The value can be **true** or **false**. The default value is **false**.                                                                                               |
   |                    |                 |                  |                                                                                                                                                                       |
   |                    |                 |                  | -  **true**: indicates that the system will check resource sufficiency. If the resources are insufficient, the check result will be returned.                         |
   |                    |                 |                  | -  **false**: indicates that the system will not check resource sufficiency.                                                                                          |
   |                    |                 |                  |                                                                                                                                                                       |
   |                    |                 |                  | .. note::                                                                                                                                                             |
   |                    |                 |                  |                                                                                                                                                                       |
   |                    |                 |                  |    Since the resource usage is dynamic, the resource sufficiency check result is not accurate.                                                                        |
   +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 9 <en-us_topic_0068473331__table44736746>` describes the response parameters.

.. _en-us_topic_0068473331__table44736746:

.. table:: **Table 9** Response parameters

   +-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                 |
   +===========+========+=============================================================================================================================+
   | server    | Object | Specifies ECS information. For details, see :ref:`Table 10 <en-us_topic_0068473331__en-us_topic_0057972661_table37882063>`. |
   +-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0068473331__en-us_topic_0057972661_table37882063:

.. table:: **Table 10** **server** field description

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                               |
   +=======================+=======================+===========================================================================================================================================+
   | id                    | String                | Specifies the ECS ID in UUID format.                                                                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | links                 | Array of objects      | Specifies the URI of the ECS. For details, see :ref:`Table 11 <en-us_topic_0068473331__table16539321>`.                                   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | security_groups       | Array of objects      | Specifies the security groups to which the ECS belongs. For details, see :ref:`Table 12 <en-us_topic_0068473331__table761507165933>`.     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-DCF:diskConfig     | String                | Specifies the disk configuration mode.                                                                                                    |
   |                       |                       |                                                                                                                                           |
   |                       |                       | -  **MANUAL**: indicates that the image space of the system disk cannot be expanded.                                                      |
   |                       |                       | -  **AUTO**: indicates that the image space of the system disk can be automatically expanded to a value same as that specified in flavor. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | reservation_id        | String                | Specifies a filtering criteria to query the created ECSs.                                                                                 |
   |                       |                       |                                                                                                                                           |
   |                       |                       | .. note::                                                                                                                                 |
   |                       |                       |                                                                                                                                           |
   |                       |                       |    When you create ECSs in a batch, this parameter is available.                                                                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | adminPass             | String                | Specifies the password of user **Administrator** for logging in to a Windows ECS.                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0068473331__table16539321:

.. table:: **Table 11** **links** field description

   ========= ====== =========================================
   Parameter Type   Description
   ========= ====== =========================================
   rel       String Specifies the shortcut link marker name.
   href      String Provides the corresponding shortcut link.
   ========= ====== =========================================

.. _en-us_topic_0068473331__table761507165933:

.. table:: **Table 12** **security_groups** field description

   ========= ====== ==========================================
   Parameter Type   Description
   ========= ====== ==========================================
   name      String Specifies the security group name or UUID.
   ========= ====== ==========================================

Example Request (Creating an ECS)
---------------------------------

Example URL request

.. code-block:: text

   POST https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/servers
   POST https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/servers

**Example 1: Use an image to create an ECS through the API block_device_mapping_v2.**

.. code-block::

    {
       "server": {
           "flavorRef": "2",
           "name": "wjvm48",
           "metadata": {
               "name": "name_xx1",
               "id": "id_xxxx1"
           },
           "block_device_mapping_v2": [{
               "source_type": "image",
               "destination_type": "volume",
               "uuid": "b023fe17-11db-4efb-b800-78882a0e394b",
               "delete_on_termination": "False",
               "boot_index": "0",
               "volume_type": "SAS",
               "volume_size": "40"
           }],
           "security_groups": [{
               "name": "name_xx5_sg"
           }],
           "networks": [{
               "uuid": "fd40e6f8-942d-4b4e-a7ae-465287b02a2c",
               "port": "e730a11c-1a19-49cc-8797-cee2ad67af6f",
               "fixed_ip": "10.20.30.137"
           }],
           "key_name": "test",
           "user_data": "ICAgICAgDQoiQSBjbG91ZCBkb2VzIG5vdCBrbm93IHdoeSBpdCBtb3ZlcyBpbiBqdXN0IHN1Y2ggYSBkaXJlY3Rpb24gYW5kIGF0IHN1Y2ggYSBzcGVlZC4uLkl0IGZlZWxzIGFuIGltcHVsc2lvbi4uLnRoaXMgaXMgdGhlIHBsYWNlIHRvIGdvIG5vdy4gQnV0IHRoZSBza3kga25vd3MgdGhlIHJlYXNvbnMgYW5kIHRoZSBwYXR0ZXJucyBiZWhpbmQgYWxsIGNsb3VkcywgYW5kIHlvdSB3aWxsIGtub3csIHRvbywgd2hlbiB5b3UgbGlmdCB5b3Vyc2VsZiBoaWdoIGVub3VnaCB0byBzZWUgYmV5b25kIGhvcml6b25zLiINCg0KLVJpY2hhcmQgQmFjaA==",
           "availability_zone":"az1-dc1"
       }
   }

**Example 2: Use a snapshot to create an ECS through the API block_device_mapping_v2.**

.. note::

   When **source_type** is **snapshot**, **boot_index** is **0**, and the EVS disk corresponding to the snapshot must be a system disk.

.. code-block::

   {
       "server":{
           "name":"wjvm48",
           "availability_zone":"az1-dc1",
           "block_device_mapping_v2": [
               {
                   "source_type":"snapshot",
                   "boot_index":"0",
                   "uuid":"df51997d-ee35-4fb3-a372-e2ac933a6565", //Specifies the snapshot ID, which is returned by the API for creating a snapshot.
                   "destination_type":"volume"
               }
           ],
           "flavorRef":"s3.xlarge.2",
           "max_count":1,
           "min_count":1,
           "networks": [
               {
                   "uuid":"79a68cef-0936-4e21-b1f4-b800ecb70246"
               }
           ]
       }
   }

**Example 3: Use a disk to create an ECS through the API block_device_mapping_v2.**

.. code-block::

   {
       "server": {
           "flavorRef": "2",
           "name": "wjvm48",
           "metadata": {
               "name": "name_xx1",
               "id": "id_xxxx1"
           },
           "block_device_mapping_v2": [{
               "source_type": "volume",
               "destination_type": "volume",
               "uuid": "bd7e4f86-b004-4745-bea2-a55b1085f107",
               "delete_on_termination": "False",
               "boot_index": "0",
               "volume_type": "dsware",
               "volume_size": "40"
           }],
           "security_groups": [{
               "name": "name_xx5_sg"
           }],
           "networks": [{
               "uuid": "fd40e6f8-942d-4b4e-a7ae-465287b02a2c",
               "port": "e730a11c-1a19-49cc-8797-cee2ad67af6f",
               "fixed_ip": "10.20.30.137"
           }],
           "key_name": "test",
           "user_data": "ICAgICAgDQoiQSBjbG91ZCBkb2VzIG5vdCBrbm93IHdoeSBpdCBtb3ZlcyBpbiBqdXN0IHN1Y2ggYSBkaXJlY3Rpb24gYW5kIGF0IHN1Y2ggYSBzcGVlZC4uLkl0IGZlZWxzIGFuIGltcHVsc2lvbi4uLnRoaXMgaXMgdGhlIHBsYWNlIHRvIGdvIG5vdy4gQnV0IHRoZSBza3kga25vd3MgdGhlIHJlYXNvbnMgYW5kIHRoZSBwYXR0ZXJucyBiZWhpbmQgYWxsIGNsb3VkcywgYW5kIHlvdSB3aWxsIGtub3csIHRvbywgd2hlbiB5b3UgbGlmdCB5b3Vyc2VsZiBoaWdoIGVub3VnaCB0byBzZWUgYmV5b25kIGhvcml6b25zLiINCg0KLVJpY2hhcmQgQmFjaA==",
           "availability_zone":"az1-dc1"
       }
   }

**Example 4: Create an ECS through the API imageRef.**

.. code-block::

   {
       "server": {
           "flavorRef": "2",
           "name": "wjvm48",
           "metadata": {
               "name": "name_xx1",
               "id": "id_xxxx1"
           },
           "adminPass": "name_xx1",
           "imageRef": "6b344c54-d606-4e1a-a99e-a7d0250c3d14",
           "security_groups": [{
               "name": "name_xx5_sg"
           }],
           "networks": [{
               "uuid": "fd40e6f8-942d-4b4e-a7ae-465287b02a2c",
               "port": "e730a11c-1a19-49cc-8797-cee2ad67af6f",
               "fixed_ip": "10.20.30.137"
           }],
           "key_name": "test",
           "user_data": "ICAgICAgDQoiQSBjbG91ZCBkb2VzIG5vdCBrbm93IHdoeSBpdCBtb3ZlcyBpbiBqdXN0IHN1Y2ggYSBkaXJlY3Rpb24gYW5kIGF0IHN1Y2ggYSBzcGVlZC4uLkl0IGZlZWxzIGFuIGltcHVsc2lvbi4uLnRoaXMgaXMgdGhlIHBsYWNlIHRvIGdvIG5vdy4gQnV0IHRoZSBza3kga25vd3MgdGhlIHJlYXNvbnMgYW5kIHRoZSBwYXR0ZXJucyBiZWhpbmQgYWxsIGNsb3VkcywgYW5kIHlvdSB3aWxsIGtub3csIHRvbywgd2hlbiB5b3UgbGlmdCB5b3Vyc2VsZiBoaWdoIGVub3VnaCB0byBzZWUgYmV5b25kIGhvcml6b25zLiINCg0KLVJpY2hhcmQgQmFjaA==",
           "availability_zone":"az1-dc1"
       }
   }

Example Response (Creating an ECS)
----------------------------------

.. code-block::

   {
       "server": {
           "security_groups": [
               {
                   "name": "name_xx5_sg"
               }
           ],
           "OS-DCF:diskConfig": " MANUAL",
           "id": "567c1557-0eca-422c-bfce-149d6b8f1bb8",
           "links": [
               {
                   "href": "http://xxx/v2/dc4059e8e7994f2498b514ca04cdaf44/servers/567c1557-0eca-422c-bfce-149d6b8f1bb8",
                   "rel": "self"
               },
               {
                   "href": "http://xxx/dc4059e8e7994f2498b514ca04cdaf44/servers/567c1557-0eca-422c-bfce-149d6b8f1bb8",
                   "rel": "bookmark"
               }
           ],
           "adminPass": "name_xx1"
       }
   }

Example Request (Creating ECSs in a Batch)
------------------------------------------

.. code-block::

   {
       "server": {
           "availability_zone":"az1.dc1",
           "name": "test",
           "imageRef": "10ff4f01-35b6-4209-8397-359cb4475fa0",
           "flavorRef": "s3.medium",
           "return_reservation_id": "true",
           "networks": [
               {
                   "uuid": "51bead38-d1a3-4d08-be20-0970c24b7cab"
               }
           ],
           "min_count": "2",
           "max_count": "3"
       }
   }

Example Response (Creating ECSs in a Batch)
-------------------------------------------

.. code-block::

   {
       "reservation_id": "r-3fhpjulh"
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
