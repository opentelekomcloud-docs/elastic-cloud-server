:original_name: en-us_topic_0167957246.html

.. _en-us_topic_0167957246:

Data Structure for Creating ECSs
================================

Contents
--------

-  :ref:`publicip Field Description <en-us_topic_0167957246__section1846944811410>`
-  :ref:`security_groups Field Description <en-us_topic_0167957246__section332191084315>`
-  :ref:`eip Field Description <en-us_topic_0167957246__section1840318312449>`
-  :ref:`bandwidth Field Description <en-us_topic_0167957246__section172789339448>`
-  :ref:`ipv6_bandwidth Field Description <en-us_topic_0167957246__section2872318176>`
-  :ref:`extendparam Field Description for Creating Disks <en-us_topic_0167957246__section1361484104817>`
-  :ref:`extendparam Field Description for Creating ECSs <en-us_topic_0167957246__section1373711413505>`
-  :ref:`metadata Field Description for Creating Disks <en-us_topic_0167957246__section1228814491353>`
-  :ref:`metadata Field Description for Creating ECSs <en-us_topic_0167957246__section1574435185018>`
-  :ref:`os:scheduler_hints Field Description <en-us_topic_0167957246__section16585034175117>`
-  :ref:`binding:profile Field Description <en-us_topic_0167957246__section681114217434>`
-  :ref:`extra_dhcp_opts Field Description <en-us_topic_0167957246__section12781010134512>`

.. _en-us_topic_0167957246__section1846944811410:

**publicip** Field Description
------------------------------

This field is used by the following APIs:

-  Creating ECSs /v1/{project_id}/cloudservers

.. _en-us_topic_0167957246__table2785183710710:

.. table:: **Table 1** **publicip** field description

   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                          |
   +=======================+=================+=================+======================================================================================================+
   | id                    | No              | String          | Specifies the ID of the existing EIP assigned to the ECS to be created. The value is in UUID format. |
   |                       |                 |                 |                                                                                                      |
   |                       |                 |                 | Only EIPs in **DOWN** state can be assigned.                                                         |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | eip                   | No              | Object          | Specifies an EIP that will be automatically assigned to an ECS.                                      |
   |                       |                 |                 |                                                                                                      |
   |                       |                 |                 | For details, see :ref:`Table 3 <en-us_topic_0167957246__table020717438159>`.                         |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | delete_on_termination | No              | Boolean         | Specifies whether the EIP is released when the ECS where the EIP is bound is deleted.                |
   |                       |                 |                 |                                                                                                      |
   |                       |                 |                 | -  **true**: The EIP is released when the ECS is deleted.                                            |
   |                       |                 |                 | -  **false**: The EIP is not released when the ECS is deleted.                                       |
   |                       |                 |                 |                                                                                                      |
   |                       |                 |                 | The default value is **false**.                                                                      |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+

.. note::

   Either **id** or **eip** in the **publicip** field can be configured.

.. _en-us_topic_0167957246__section332191084315:

**security_groups** Field Description
-------------------------------------

This field is used by the following APIs:

-  Creating ECSs /v1/{project_id}/cloudservers

.. _en-us_topic_0167957246__table1698566599:

.. table:: **Table 2** **security_groups** field description

   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                                                                                                                            |
   +===========+===========+========+========================================================================================================================================================================================================================================================================================+
   | id        | No        | String | Specifies the ID of the security group to which an ECS is to be added. The configuration will take effect on the NICs of the ECS. You need to specify the ID of an existing security group in UUID format. Otherwise, the default security group will be used at the underlying layer. |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0167957246__section1840318312449:

**eip** Field Description
-------------------------

This field is used by the following APIs:

-  Creating ECSs /v1/{project_id}/cloudservers

.. _en-us_topic_0167957246__table020717438159:

.. table:: **Table 3** **eip** field description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================+
   | iptype          | Yes             | String          | Specifies the EIP type.                                                                                                             |
   |                 |                 |                 |                                                                                                                                     |
   |                 |                 |                 | For details about the enumerated values, see the **publicip** field in "Assigning an EIP" in *Virtual Private Cloud API Reference*. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | bandwidth       | Yes             | Object          | Specifies the bandwidth of an EIP.                                                                                                  |
   |                 |                 |                 |                                                                                                                                     |
   |                 |                 |                 | For details, see :ref:`bandwidth Field Description <en-us_topic_0167957246__section172789339448>`.                                  |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0167957246__section172789339448:

**bandwidth** Field Description
-------------------------------

This field is used by the following APIs:

-  Creating ECSs /v1/{project_id}/cloudservers

.. table:: **Table 4** **bandwidth** field description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================+
   | size            | Yes             | Integer         | Specifies the bandwidth size.                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                      |
   |                 |                 |                 | Specifies the bandwidth (Mbit/s). The value ranges from 1 to 1,000.                                                                                  |
   |                 |                 |                 |                                                                                                                                                      |
   |                 |                 |                 | The specific range may vary depending on the configuration in each region. You can see the bandwidth range of each region on the management console. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sharetype       | Yes             | String          | Specifies the bandwidth sharing type.                                                                                                                |
   |                 |                 |                 |                                                                                                                                                      |
   |                 |                 |                 | Enumerated values: **PER** (indicates exclusive bandwidth) and **WHOLE** (indicates sharing)                                                         |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | chargemode      | Yes             | String          | Specifies the bandwidth billing mode.                                                                                                                |
   |                 |                 |                 |                                                                                                                                                      |
   |                 |                 |                 | -  If the field value is **traffic**, the ECS is billed by traffic.                                                                                  |
   |                 |                 |                 | -  If the field value is others, creating the ECS will fail.                                                                                         |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0167957246__section2872318176:

**ipv6_bandwidth** Field Description
------------------------------------

This field is used by the following APIs:

-  Creating ECSs /v1/{project_id}/cloudservers

.. table:: **Table 5** **ipv6_bandwidth** field description

   ========= ========= ====== ======================================
   Parameter Mandatory Type   Description
   ========= ========= ====== ======================================
   id        No        String Specifies the ID of an IPv6 bandwidth.
   ========= ========= ====== ======================================

.. _en-us_topic_0167957246__section1361484104817:

**extendparam** Field Description for Creating Disks
----------------------------------------------------

This field is used by the following APIs:

-  Creating ECSs /v1/{project_id}/cloudservers

.. _en-us_topic_0167957246__table7562101331712:

.. table:: **Table 6** **extendparam** field description for creating disks

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================================================================================================================================================================================+
   | snapshotId      | No              | String          | Specifies the snapshot ID or ID of the original data disk contained in the full-ECS image.                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 | **Application scenarios:**                                                                                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 | This parameter is used if an ECS is created using a full-ECS image, and the image contains one or more data disks.                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 | If you use a full-ECS image to create an ECS, the system automatically restores the data type and data from the data disks in the image. The **snapshotId** parameter allows you to specify the disk type for the original data disk after restoration.                                                           |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 | .. note::                                                                                                                                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 |    -  You are advised to specify **snapshotId** for each original data disk.                                                                                                                                                                                                                                      |
   |                 |                 |                 |    -  If you are required to change a disk size, ensure that the changed disk size is greater than or equal to the size of the original data disk. Otherwise, restoring data of the original data disk will fail.                                                                                                 |
   |                 |                 |                 |    -  To set disk sharing, you need to specify the sharing attribute.                                                                                                                                                                                                                                             |
   |                 |                 |                 |    -  To set disk encryption, you need to specify the encryption attribute in the metadata field.                                                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 | **Working rules:**                                                                                                                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 | **snapshotId** uniquely identifies an original data disk contained in a full-ECS image. You can use **snapshotId** to obtain the information of the original data disk for data restoration.                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 | **Obtaining snapshotId through the management console:**                                                                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 | Log in to the management console, choose **Elastic Volume Service** > **Snapshot**. Then, use the name of the original data disk to find the snapshot ID or the original disk ID.                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 | **Obtaining snapshotId through the API:**                                                                                                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 | If you have obtained the full-ECS image ID, obtain the Cloud Backup and Recovery (CBR) or Cloud Server Backup Service (CSBS) backup ID associated with the full-ECS image ID by following the instructions provided in the API for querying image details.                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 | -  If CBR backup is used, use the CBR backup ID to obtain the backup. The **resource_id** or **snapshot_id** contained in the children field in the response is the desired **snapshotId**. For details, see the API for "Querying a Specified Backup" in *Cloud Backup and Recovery User Guide*.                 |
   |                 |                 |                 | -  If CSBS backup is used, use the CSBS backup ID to obtain the backup. The **source_volume_id** or **snapshot_id** contained in the **volume_backups** field in the response is the desired **snapshotId**. For details, see the API for "Querying a Single Backup" in *Cloud Server Backup Service User Guide*. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0167957246__section1373711413505:

**extendparam** Field Description for Creating ECSs
---------------------------------------------------

This field is used by the following APIs:

-  Creating ECSs /v1/{project_id}/cloudservers

.. _en-us_topic_0167957246__table1137234112314:

.. table:: **Table 7** extendparam field description for creating ECSs (for V1 APIs)

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================+
   | regionID        | No              | String          | Specifies the ID of the region where the ECS resides.                                                                                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CB_CSBS_BACKUP  | No              | String          | Specifies a CSBS policy ID and CSBS vault ID.                                                                                                             |
   |                 |                 |                 |                                                                                                                                                           |
   |                 |                 |                 | For example, a CSBS policy ID obtained on the console is fdcaa27d-5be4-4f61-afe3-09ff79162c04.                                                            |
   |                 |                 |                 |                                                                                                                                                           |
   |                 |                 |                 | A CSBS vault ID is 332a9408-463f-436a-9e92-78dad95d1ac4.                                                                                                  |
   |                 |                 |                 |                                                                                                                                                           |
   |                 |                 |                 | The **CB_CSBS_BACKUP** value is "{\\"policy_id\\":\\"fdcaa27d-5be4-4f61-afe3-09ff79162c04\\",\\"vault_id\\":\\"332a9408-463f-436a-9e92-78dad95d1ac4\\"}". |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0167957246__section1228814491353:

**metadata** Field Description for Creating Disks
-------------------------------------------------

This field is used by the following APIs:

-  Creating ECSs /v1/{project_id}/cloudservers

.. note::

   -  When you create an ECS, both **root_volume** and **data_volume** contain the **metadata** field.

.. table:: **Table 8** **metadata** field description for creating disks

   +----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory       | Type            | Description                                                                                                               |
   +======================+=================+=================+===========================================================================================================================+
   | \__system__encrypted | No              | String          | Specifies encryption in **metadata**. The value can be **0** (encryption disabled) or **1** (encryption enabled).         |
   |                      |                 |                 |                                                                                                                           |
   |                      |                 |                 | If this parameter does not exist, the disk will not be encrypted by default.                                              |
   +----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
   | \__system__cmkid     | No              | String          | Specifies the CMK ID, which indicates encryption in **metadata**. This parameter is used with **\__system__encrypted**.   |
   |                      |                 |                 |                                                                                                                           |
   |                      |                 |                 | .. note::                                                                                                                 |
   |                      |                 |                 |                                                                                                                           |
   |                      |                 |                 |    For details about how to obtain the CMK ID, see "Querying the List of CMKs" in *Key Management Service API Reference*. |
   +----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0167957246__section1574435185018:

metadata Field Description for Creating ECSs
--------------------------------------------

This field is used by the following APIs:

-  Creating ECSs /v1/{project_id}/cloudservers

.. _en-us_topic_0167957246__table2373623012315:

.. table:: **Table 9** **metadata** reserved field description

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================================================================================+
   | admin_pass      | No              | String          | Specifies the password of user **Administrator** for logging in to a Windows ECS. For details, see :ref:`Function <en-us_topic_0020212668__section61372619>`.                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | .. note::                                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 |    This parameter is mandatory when a Windows ECS using password authentication is created.                                                                                                                                 |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | op_svc_userid   | No              | String          | Specifies the user ID.                                                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | agency_name     | No              | String          | Specifies the IAM agency name.                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | An agency is created by a tenant administrator on Identity and Access Management (IAM) to provide temporary credentials for ECSs to access cloud services.                                                                  |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | BYOL            | No              | String          | If you have an OS or a software license (a license certified based on the number of physical servers and cores), you can migrate your services to the cloud platform in BYOL mode to continue using your existing licenses. |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | -  **True**: Use your existing licenses.                                                                                                                                                                                    |
   |                 |                 |                 | -  **False**: System licenses are used.                                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0167957246__section16585034175117:

**os:scheduler_hints** Field Description
----------------------------------------

This field is used by the following APIs:

-  Creating ECSs: /v1/{project_id}/cloudservers
-  Creating ECSs (native): /v2.1/{project_id}/servers

.. _en-us_topic_0167957246__table24430409172542:

.. table:: **Table 10** **os:scheduler_hints** field description (request parameters)

   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                         |
   +===================+=================+=================+=====================================================================================================================+
   | group             | No              | String          | Specifies the ECS group ID in UUID format.                                                                          |
   |                   |                 |                 |                                                                                                                     |
   |                   |                 |                 | Obtain the parameter value from the console or by referring to :ref:`Querying ECS Groups <en-us_topic_0065817721>`. |
   |                   |                 |                 |                                                                                                                     |
   |                   |                 |                 | .. note::                                                                                                           |
   |                   |                 |                 |                                                                                                                     |
   |                   |                 |                 |    Ensure that the ECS group uses the anti-affinity policy.                                                         |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | tenancy           | No              | String          | Creates ECSs on a dedicated or shared host.                                                                         |
   |                   |                 |                 |                                                                                                                     |
   |                   |                 |                 | The value of this parameter can be **dedicated** or **shared**.                                                     |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | dedicated_host_id | No              | String          | Specifies the dedicated host ID.                                                                                    |
   |                   |                 |                 |                                                                                                                     |
   |                   |                 |                 | .. note::                                                                                                           |
   |                   |                 |                 |                                                                                                                     |
   |                   |                 |                 |    A DeH ID takes effect only when **tenancy** is set to **dedicated**.                                             |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0167957246__table3756175217341:

.. table:: **Table 11** **os:scheduler_hints** field description (response parameters)

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                         |
   +=======================+=======================+=====================================================================================================================+
   | group                 | Array of strings      | Specifies the ECS group ID in UUID format.                                                                          |
   |                       |                       |                                                                                                                     |
   |                       |                       | Obtain the parameter value from the console or by referring to :ref:`Querying ECS Groups <en-us_topic_0065817721>`. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
   | tenancy               | Array of strings      | Creates ECSs on a dedicated or shared host.                                                                         |
   |                       |                       |                                                                                                                     |
   |                       |                       | The value of this parameter can be **dedicated** or **shared**.                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
   | dedicated_host_id     | Array of strings      | Specifies the dedicated host ID.                                                                                    |
   |                       |                       |                                                                                                                     |
   |                       |                       | .. note::                                                                                                           |
   |                       |                       |                                                                                                                     |
   |                       |                       |    A DeH ID takes effect only when **tenancy** is set to **dedicated**.                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0167957246__section681114217434:

**binding:profile** Field Description
-------------------------------------

This field is used by the following APIs:

-  Creating ECSs: /v1/{project_id}/cloudservers

.. _en-us_topic_0167957246__table42451440577:

.. table:: **Table 12** **binding:profile** field description

   +-------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------+
   | Parameter               | Mandatory       | Type            | Description                                                                         |
   +=========================+=================+=================+=====================================================================================+
   | disable_security_groups | No              | Boolean         | Specifies whether the NIC of an ECS is not added to a security group.               |
   |                         |                 |                 |                                                                                     |
   |                         |                 |                 | .. note::                                                                           |
   |                         |                 |                 |                                                                                     |
   |                         |                 |                 |    -  The primary NIC of the ECS must be added to a security group.                 |
   |                         |                 |                 |    -  At most one NIC of the ECS is allowed not to be added to any security groups. |
   +-------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------+

.. _en-us_topic_0167957246__section12781010134512:

**extra_dhcp_opts** Field Description
-------------------------------------

This field is used by the following APIs:

-  Creating ECSs: /v1/{project_id}/cloudservers

.. _en-us_topic_0167957246__table93959401279:

.. table:: **Table 13** **extra_dhcp_opts** field description

   +-----------+-----------+---------+--------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                            |
   +===========+===========+=========+========================================================+
   | opt_value | Yes       | Integer | Specifies the NIC MTU, which ranges from 1280 to 8888. |
   +-----------+-----------+---------+--------------------------------------------------------+
   | opt_name  | Yes       | String  | Set the parameter value to **26**.                     |
   +-----------+-----------+---------+--------------------------------------------------------+
