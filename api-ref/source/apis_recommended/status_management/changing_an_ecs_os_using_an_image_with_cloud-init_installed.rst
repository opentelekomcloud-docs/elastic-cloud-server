:original_name: en-us_topic_0067876971.html

.. _en-us_topic_0067876971:

Changing an ECS OS (Using an Image with Cloud-Init Installed)
=============================================================

Function
--------

This API is used to change an ECS OS. During the system disk reinstallation using a new image, the data disks of the ECS remain unchanged.

This API is an asynchronous API. After the OS change request is successfully delivered, a job ID is returned. This does not mean the OS change is complete. You need to call the API by referring to :ref:`Querying Task Execution Status <en-us_topic_0022225398>` to query the job status. The SUCCESS status indicates that the OS change is successful.

After this API is called, the system uninstalls the system disk, uses the new image to create a system disk, and attaches it to the ECS. In this way, the OS is changed.

Constraints
-----------

-  You can only use an image with Cloud-Init or Cloudbase-Init installed.
-  Only a stopped ECS or an ECS on which reinstalling or changing the OS failed supports changing OS.
-  Only an ECS with a system disk supports changing OS.
-  You are not allowed to perform other operations when changing the OS. Otherwise, changing the OS will fail.

URI
---

POST /v2/{project_id}/cloudservers/{server_id}/changeos

:ref:`Table 1 <en-us_topic_0067876971__table55945983>` describes the parameters in the URI.

.. _en-us_topic_0067876971__table55945983:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0067876971__table2840889>` describes the request parameters.

.. _en-us_topic_0067876971__table2840889:

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                 |
   +===========+===========+========+=============================================================================================+
   | os-change | Yes       | Object | Changes an ECS OS. For details, see :ref:`Table 3 <en-us_topic_0067876971__table32200631>`. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------+

.. _en-us_topic_0067876971__table32200631:

.. table:: **Table 3** **os-change** field description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================================================================+
   | keyname         | Yes             | String          | Specifies the key name.                                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | userid          | No              | String          | Specifies the user ID. When the **keyname** parameter is being specified, the value of this parameter is used preferentially. If this parameter is left blank, the user ID in the token is used by default. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | imageid         | Yes             | String          | Specifies the ID of the new image in UUID format.                                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | You can obtain the image ID from the console or by following the instructions provided in "Querying Images" in *Image Management Service API Reference*.                                                    |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata        | No              | Object          | Specifies the metadata of the ECS for which the OS is to be changed.                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | For more information, see :ref:`Table 4 <en-us_topic_0067876971__table9120223>`.                                                                                                                            |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0067876971__table9120223:

.. table:: **Table 4** **metadata** field description

   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory       | Type            | Description                                                                                                                                      |
   +======================+=================+=================+==================================================================================================================================================+
   | BYOL                 | No              | String          | Specifies whether a user has the license of an image.                                                                                            |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 | -  If this parameter is set to **true**, the license file delivered with the image is used, indicating that BYOL is used.                        |
   |                      |                 |                 | -  If this parameter is set to a value other than **true**, BYOL is not used, and the license file provided by the cloud platform must be used.  |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 | The default value is not **true**, indicating that BYOL is not used.                                                                             |
   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_data            | No              | String          | Specifies the user data to be injected to the ECS during the creation. Text and text files can be injected.                                      |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 | .. note::                                                                                                                                        |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 |    -  The content of **user_data** must be encoded with base64.                                                                                  |
   |                      |                 |                 |    -  The maximum size of the content to be injected (before encoding) is 32 KB.                                                                 |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 | For more details, see "Injecting User Data into ECSs" in the *Elastic Cloud Server User Guide*.                                                  |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 | Examples                                                                                                                                         |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 | Before base64 encoding:                                                                                                                          |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 | -  Linux                                                                                                                                         |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 |    .. code-block::                                                                                                                               |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 |       #!/bin/bash                                                                                                                                |
   |                      |                 |                 |       echo user_test > /home/user.txt                                                                                                            |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 | -  Windows                                                                                                                                       |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 |    .. code-block::                                                                                                                               |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 |       rem cmd                                                                                                                                    |
   |                      |                 |                 |       echo 111 > c:\aaa.txt                                                                                                                      |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 | After base64 encoding:                                                                                                                           |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 | -  Linux                                                                                                                                         |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 |    .. code-block::                                                                                                                               |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 |       IyEvYmluL2Jhc2gKZWNobyB1c2VyX3Rlc3QgPiAvaG9tZS91c2VyLnR4dA==                                                                               |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 | -  Windows                                                                                                                                       |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 |    .. code-block::                                                                                                                               |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 |       cmVtIGNtZAplY2hvIDExMSA+IGM6XGFhYS50eHQ=                                                                                                   |
   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | \__system__encrypted | No              | String          | Specifies encryption in **metadata**. The value can be **0** (encryption disabled) or **1** (encryption enabled).                                |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 | If this parameter does not exist, the system disk will not be encrypted by default.                                                              |
   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | \__system__cmkid     | No              | String          | Specifies the CMK ID, which indicates encryption in **metadata**. This parameter is used with **\__system__encrypted**.                          |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 | .. note::                                                                                                                                        |
   |                      |                 |                 |                                                                                                                                                  |
   |                      |                 |                 |    For details about how to obtain the CMK ID through HTTPS requests, see "Querying the List of CMKs" in *Key Management Service API Reference*. |
   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

See :ref:`Responses (Task) <en-us_topic_0022067714>`.

Example Request
---------------

-  After the ECS OS is switched, use the password for login authentication. For security purposes, store the password in ciphertext in configuration files or environment variables.

   .. code-block:: text

      POST https://{endpoint}/v2/{project_id}/cloudservers/{server_id}/changeos

      {
          "os-change": {
              "userid": "7e25b1da389f4697a79df3a0e5bd494e",
              "imageid": "e215580f-73ad-429d-b6f2-5433947433b0"
          }
      }

-  Change the OS and use the key pair for login authentication after the OS change.

   .. code-block:: text

      POST https://{endpoint}/v2/{project_id}/cloudservers/{server_id}/changeos

      {
          "os-change": {
              "keyname": "KeyPair-350b",
              "userid": "7e25b1da389f4697a79df3a0e5bd494e",
              "imageid": "e215580f-73ad-429d-b6f2-5433947433b0"
          }
      }

-  If the ECS OS is switched using encrypted full-ECS images of the system disk, use the password for login authentication. For security purposes, store the password in ciphertext in configuration files or environment variables.

   .. code-block:: text

      POST https://{endpoint}/v2/{project_id}/cloudservers/{server_id}/changeos

      {
          "os-change": {
              "userid": "7e25b1da389f4697a79df3a0e5bd494e",
              "imageid": "e215580f-73ad-429d-b6f2-5433947433b0",
              "metadata": {
                    "__system__encrypted": "1",
                    "__system__cmkid": "83cdb52d-9ebf-4469-9cfa-e7b5b80da846"
              }
          }
      }

Example Response
----------------

See :ref:`Responses (Task) <en-us_topic_0022067714>`.

.. code-block::

   {
       "job_id": "ff80808288d41e1b018990260955686a"
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
