:original_name: en-us_topic_0118308527.html

.. _en-us_topic_0118308527:

Modifying ECS Details
=====================

Function
--------

This API is used to modify ECS details. Only the name and description of an ECS can be modified.

This API supports checking fine-grained permissions for enterprise projects. For details, see :ref:`ecs:cloudServers:updateServer <en-us_topic_0103071510>`.

Constraints
-----------

This API is used to change the name of an ECS. For details about how to change the hostname of an ECS, see "How Can a Changed Static Hostname Take Effect Permanently?" in *Elastic Cloud Server User Guide*.

URI
---

PUT /v1/{project_id}/cloudservers/{server_id}

:ref:`Table 1 <en-us_topic_0118308527__table44564854>` describes the parameters in the URI.

.. _en-us_topic_0118308527__table44564854:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+---------------------------+
   | Parameter             | Mandatory             | Description               |
   +=======================+=======================+===========================+
   | project_id            | Yes                   | **Definition**            |
   |                       |                       |                           |
   |                       |                       | Specifies the project ID. |
   |                       |                       |                           |
   |                       |                       | **Constraints**           |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Range**                 |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Default Value**         |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   +-----------------------+-----------------------+---------------------------+
   | server_id             | Yes                   | **Definition**            |
   |                       |                       |                           |
   |                       |                       | Specifies the ECS ID.     |
   |                       |                       |                           |
   |                       |                       | **Constraints**           |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Range**                 |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Default Value**         |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   +-----------------------+-----------------------+---------------------------+

Request
-------

:ref:`Table 2 <en-us_topic_0118308527__table13100926>` describes the request parameters.

.. _en-us_topic_0118308527__table13100926:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                    |
   +=================+=================+=================+================================================================================+
   | server          | Yes             | Object          | **Definition**                                                                 |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | Specifies the ECS data structure.                                              |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | For details, see :ref:`Table 3 <en-us_topic_0118308527__table26827213163326>`. |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | **Constraints**                                                                |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | N/A                                                                            |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | **Range**                                                                      |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | N/A                                                                            |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | **Default Value**                                                              |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | N/A                                                                            |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------+

.. _en-us_topic_0118308527__table26827213163326:

.. table:: **Table 3** **server** field description

   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                             |
   +==================+=================+=================+=========================================================================================================================================================================================================================================================================================================================================+
   | name             | No              | String          | **Definition**                                                                                                                                                                                                                                                                                                                          |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | Specifies the name of the modified ECS.                                                                                                                                                                                                                                                                                                 |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | **Constraints**                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | The parameter value consists of 1 to 128 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                                                                                                                                                                                          |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | **Range**                                                                                                                                                                                                                                                                                                                               |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | N/A                                                                                                                                                                                                                                                                                                                                     |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | **Default Value**                                                                                                                                                                                                                                                                                                                       |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | N/A                                                                                                                                                                                                                                                                                                                                     |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description      | No              | String          | **Definition**                                                                                                                                                                                                                                                                                                                          |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | Specifies the ECS description.                                                                                                                                                                                                                                                                                                          |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | **Constraints**                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | Angle brackets (<>) are not allowed.                                                                                                                                                                                                                                                                                                    |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | **Range**                                                                                                                                                                                                                                                                                                                               |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | 0 to 85 characters                                                                                                                                                                                                                                                                                                                      |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | **Default Value**                                                                                                                                                                                                                                                                                                                       |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | N/A                                                                                                                                                                                                                                                                                                                                     |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hostname         | No              | String          | **Definition**                                                                                                                                                                                                                                                                                                                          |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | Specifies the new hostname of the ECS.                                                                                                                                                                                                                                                                                                  |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | **Constraints**                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | The name consists of 1-64 characters. It can be segmented using periods (.). Only letters, digits, and hyphens (-) are allowed in each segment. A name cannot contain consecutive periods (.) or hyphens (-), and cannot start or end with a period (.) or hyphen (-). Additionally, the combinations of (.-) and (-.) are not allowed. |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | .. note::                                                                                                                                                                                                                                                                                                                               |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 |    This parameter is discarded. For details about how to change the hostname of an ECS, see "How Can a Changed Static Hostname Take Effect Permanently?" in *Elastic Cloud Server User Guide*.                                                                                                                                          |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | **Range**                                                                                                                                                                                                                                                                                                                               |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | N/A                                                                                                                                                                                                                                                                                                                                     |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | **Default Value**                                                                                                                                                                                                                                                                                                                       |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | N/A                                                                                                                                                                                                                                                                                                                                     |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_options | No              | Object          | **Definition**                                                                                                                                                                                                                                                                                                                          |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | Specifies the secure boot option.                                                                                                                                                                                                                                                                                                       |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | For details, see :ref:`Table 4 <en-us_topic_0118308527__table137954971413>`.                                                                                                                                                                                                                                                            |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | **Constraints**                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | N/A                                                                                                                                                                                                                                                                                                                                     |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | **Range**                                                                                                                                                                                                                                                                                                                               |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | N/A                                                                                                                                                                                                                                                                                                                                     |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | **Default Value**                                                                                                                                                                                                                                                                                                                       |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                                                         |
   |                  |                 |                 | N/A                                                                                                                                                                                                                                                                                                                                     |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0118308527__table137954971413:

.. table:: **Table 4** **security_options** field description

   +-----------------+-----------------+-----------------+------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                |
   +=================+=================+=================+============================================================+
   | tpm_enabled     | No              | Boolean         | **Definition**                                             |
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

Response
--------

:ref:`Table 5 <en-us_topic_0118308527__table44736746>` describes the response parameters.

.. _en-us_topic_0118308527__table44736746:

.. table:: **Table 5** Response parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                              |
   +=======================+=======================+==========================================================================+
   | server                | Object                | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Specifies the ECS.                                                       |
   |                       |                       |                                                                          |
   |                       |                       | For details, see :ref:`Table 6 <en-us_topic_0118308527__table11253402>`. |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | N/A                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+

.. _en-us_topic_0118308527__table11253402:

.. table:: **Table 6** **server** field description

   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Type                  | Description                                                                                                                                                                                                                |
   +==========================+=======================+============================================================================================================================================================================================================================+
   | tenant_id                | String                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the tenant or project ID.                                                                                                                                                                                        |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image                    | String                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the image ID.                                                                                                                                                                                                    |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | accessIPv4               | String                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | This is a reserved parameter.                                                                                                                                                                                              |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | addresses                | Object                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the attributed network information of the ECS.                                                                                                                                                                   |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | The structure is Map<String, Object>.                                                                                                                                                                                      |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | For details, see :ref:`Table 7 <en-us_topic_0118308527__table1656029015527>`.                                                                                                                                              |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata                 | Object                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the ECS metadata.                                                                                                                                                                                                |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | accessIPv6               | String                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | This is a reserved parameter.                                                                                                                                                                                              |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created                  | String                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the time when the ECS was created. The time is in the format of "2019-05-22T03:19:19Z".                                                                                                                          |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hostId                   | String                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the host ID of the ECS.                                                                                                                                                                                          |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavor                   | Object                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the ECS flavor. For details, see :ref:`Table 8 <en-us_topic_0118308527__table19588408>`.                                                                                                                         |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-DCF:diskConfig        | String                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the disk configuration mode. This is an extended attribute. This field is valid for the ECS started using an image.                                                                                              |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_id                  | String                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the ID of the user to which an ECS belongs.                                                                                                                                                                      |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                     | String                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the name of the modified ECS.                                                                                                                                                                                    |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | progress                 | Integer               | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | This is a reserved parameter.                                                                                                                                                                                              |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | links                    | Array of Object       | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies ECS shortcut links for ECS. For details, see :ref:`Table 9 <en-us_topic_0118308527__table64121649>`.                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                       | String                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the unique ID of an ECS.                                                                                                                                                                                         |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated                  | String                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the time when the ECS was updated last time.                                                                                                                                                                     |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | The time is in the format of "2019-05-22T03:19:19Z".                                                                                                                                                                       |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | locked                   | Boolean               | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the ECS lock status, which is **True** when the ECS is locked and **False** when the ECS is unlocked.                                                                                                            |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description              | String                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Describes the ECS.                                                                                                                                                                                                         |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                     | Array of strings      | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies ECS tags.                                                                                                                                                                                                        |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Tag functions have been upgraded on the cloud platform. After the upgrade, the tag values returned by the system comply with the following rules:                                                                          |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | -  The key and value of a tag are connected using an equal sign (=), for example, key=value.                                                                                                                               |
   |                          |                       | -  If the value is empty, only the key is returned.                                                                                                                                                                        |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | For more details about upgraded tag functions, see :ref:`Tag Types <en-us_topic_0167811962>`.                                                                                                                              |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                   | String                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the ECS status.                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **ACTIVE**, **BUILD**, **ERROR**, **HARD_REBOOT**, **MIGRATING**, **REBOOT**, **REBUILD**, **RESIZE**, **REVERT_RESIZE**, **SHUTOFF**, **VERIFY_RESIZE**, **DELETED**, **SHELVED**, **SHELVED_OFFLOADED**, and **UNKNOWN** |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | For details, see :ref:`ECS Statuses <en-us_topic_0178420672>`.                                                                                                                                                             |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS-EXT-SRV-ATTR:hostname | String                | **Definition**                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | Specifies the new host name of the ECS.                                                                                                                                                                                    |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | **Range**                                                                                                                                                                                                                  |
   |                          |                       |                                                                                                                                                                                                                            |
   |                          |                       | N/A                                                                                                                                                                                                                        |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0118308527__table1656029015527:

.. table:: **Table 7** Data structure of the network that an ECS accesses

   +-----------------------+-----------------------+-----------------------------------------------+
   | Parameter             | Type                  | Description                                   |
   +=======================+=======================+===============================================+
   | addr                  | String                | **Definition**                                |
   |                       |                       |                                               |
   |                       |                       | Specifies the IP address.                     |
   |                       |                       |                                               |
   |                       |                       | **Range**                                     |
   |                       |                       |                                               |
   |                       |                       | N/A                                           |
   +-----------------------+-----------------------+-----------------------------------------------+
   | version               | Integer               | **Definition**                                |
   |                       |                       |                                               |
   |                       |                       | Specifies the IP address type.                |
   |                       |                       |                                               |
   |                       |                       | **Range**                                     |
   |                       |                       |                                               |
   |                       |                       | -  **4**: The type of the IP address is IPv4. |
   |                       |                       | -  **6**: The type of the IP address is IPv6. |
   +-----------------------+-----------------------+-----------------------------------------------+

.. _en-us_topic_0118308527__table19588408:

.. table:: **Table 8** **flavor** field description

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                      |
   +=======================+=======================+==================================================================================================================+
   | id                    | String                | **Definition**                                                                                                   |
   |                       |                       |                                                                                                                  |
   |                       |                       | Specifies the ECS ID.                                                                                            |
   |                       |                       |                                                                                                                  |
   |                       |                       | **Range**                                                                                                        |
   |                       |                       |                                                                                                                  |
   |                       |                       | N/A                                                                                                              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
   | links                 | Array of objects      | **Definition**                                                                                                   |
   |                       |                       |                                                                                                                  |
   |                       |                       | Specifies shortcut links for ECS types. For details, see :ref:`Table 9 <en-us_topic_0118308527__table64121649>`. |
   |                       |                       |                                                                                                                  |
   |                       |                       | **Range**                                                                                                        |
   |                       |                       |                                                                                                                  |
   |                       |                       | N/A                                                                                                              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0118308527__table64121649:

.. table:: **Table 9** **links** field description

   +-----------------------+-----------------------+------------------------------------------+
   | Parameter             | Type                  | Description                              |
   +=======================+=======================+==========================================+
   | rel                   | String                | **Definition**                           |
   |                       |                       |                                          |
   |                       |                       | Specifies the shortcut link marker name. |
   |                       |                       |                                          |
   |                       |                       | **Range**                                |
   |                       |                       |                                          |
   |                       |                       | N/A                                      |
   +-----------------------+-----------------------+------------------------------------------+
   | href                  | String                | **Definition**                           |
   |                       |                       |                                          |
   |                       |                       | Provides the shortcut link.              |
   |                       |                       |                                          |
   |                       |                       | **Range**                                |
   |                       |                       |                                          |
   |                       |                       | N/A                                      |
   +-----------------------+-----------------------+------------------------------------------+

Example Request
---------------

Change the ECS name to **new-server-test**.

.. code-block:: text

   PUT  https://{endpoint}/v1/{project_id}/cloudservers/{server_id}

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
           "tenant_id": "10c351034cb84212ba9d9721504812fe",
           "image": "",
           "accessIPv4": null,
           "metadata": {
               "__support_agent_list": "hss,ces"
           },
           "addresses": {
               "ee8d408c-9f11-4407-9cbc-b17c8d372502": [
                   {
                       "addr": "192.168.26.22",
                       "version": 4
                   }
               ]
           },
           "accessIPv6": null,
           "created": "2025-07-23T08:22:35Z",
           "OS-EXT-SRV-ATTR:user_data": null,
           "hostId": "5228412f60464f196eb4db431011d476312bf0d53de9c828f36daeef",
           "description": "",
           "OS-EXT-SRV-ATTR:hostname": "server-test",
           "flavor": {
               "links": [
                   {
                       "rel": "bookmark",
                       "href": "https://{endpoint}/flavors/s2.large.2"
                   }
               ],
               "id": "s2.large.2"
           },
           "OS-DCF:diskConfig": "MANUAL",
           "user_id": "d4e91bab74ac4d45bb7d7bce182b6684",
           "name": "new-server-test",
           "progress": 0,
           "links": [
               {
                   "rel": "self",
                   "href": "https://{endpoint}/v1.0/servers/17833209-75ba-4ad3-931d-5645919e3664"
               },
               {
                   "rel": "bookmark",
                   "href": "https://{endpoint}/servers/17833209-75ba-4ad3-931d-5645919e3664"
               }
           ],
           "id": "17833209-75ba-4ad3-931d-5645919e3664",
           "updated": "2026-07-23T08:23:05Z",
           "status": "ACTIVE"
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
