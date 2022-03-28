Changing an ECS OS (Using an Image with Cloud-Init Installed)
=============================================================

Function
--------

This API is used to change an ECS OS. During the system disk reinstallation using a new image, the data disks of the ECS remain unchanged.

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

`Table 1 <#enustopic0067876971table55945983>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0067876971table55945983:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0067876971table2840889>`__ describes the request parameters. 

.. _ENUSTOPIC0067876971table2840889:

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+--------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                          |
   +===========+===========+========+======================================================================================+
   | os-change | Yes       | Object | Changes an ECS OS. For details, see `Table 3 <#enustopic0067876971table32200631>`__. |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------+



.. _ENUSTOPIC0067876971table32200631:

.. table:: **Table 3** **os-change** field description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================================================================+
   | keyname         | Yes             | String          | Specifies the key pair name.                                                                                                                                                                                |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | userid          | No              | String          | Specifies the user ID. When the **keyname** parameter is being specified, the value of this parameter is used preferentially. If this parameter is left blank, the user ID in the token is used by default. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | imageid         | Yes             | String          | Specifies the ID of the new image in UUID format.                                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | You can obtain the image ID from the console or by following the instructions provided in "Querying Images" in *Image Management Service API Reference*.                                                    |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata        | No              | Object          | Specifies the metadata of the ECS for which the OS is to be changed.                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | For more information, see `Table 4 <#enustopic0067876971table9120223>`__.                                                                                                                                   |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0067876971table9120223:

.. table:: **Table 4** **metadata** field description

   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory       | Type            | Description                                                                                                                                            |
   +======================+=================+=================+========================================================================================================================================================+
   | BYOL                 | No              | String          | Specifies whether a user has the license of an image.                                                                                                  |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 | -  If this parameter is set to **true**, the license file delivered with the image is used, indicating that BYOL is used.                              |
   |                      |                 |                 | -  If this parameter is set to a value other than **true**, BYOL is not used, and the license file provided by the public cloud platform must be used. |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 | The default value is not **true**, indicating that BYOL is not used.                                                                                   |
   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_data            | No              | String          | Specifies the user data to be injected to the ECS during the creation. Text and text files can be injected.                                            |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 | .. note::                                                                                                                                              |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 |    -  The content of **user_data** must be encoded with base64.                                                                                        |
   |                      |                 |                 |    -  The maximum size of the content to be injected (before encoding) is 32 KB.                                                                       |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 | For more details, see "Injecting User Data into ECSs" in *Elastic Cloud Server User Guide*.                                                            |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 | Examples                                                                                                                                               |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 | Before base64 encoding:                                                                                                                                |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 | -  Linux                                                                                                                                               |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 |    .. code-block::                                                                                                                                     |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 |       #! /bin/bash                                                                                                                                     |
   |                      |                 |                 |       echo user_test >> /home/user.txt                                                                                                                 |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 | -  Windows                                                                                                                                             |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 |    .. code-block::                                                                                                                                     |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 |       rem cmd                                                                                                                                          |
   |                      |                 |                 |       echo 111 > c:\aaa.txt                                                                                                                            |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 | After base64 encoding:                                                                                                                                 |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 | -  Linux                                                                                                                                               |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 |    .. code-block::                                                                                                                                     |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 |       IyEgL2Jpbi9iYXNoDQplY2hvIHVzZXJfdGVzdCAmZ3Q7Jmd0OyAvaG9tZS91c2VyLnR4dA==                                                                         |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 | -  Windows                                                                                                                                             |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 |    .. code-block::                                                                                                                                     |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 |       cmVtIGNtZA0KZWNobyAxMTEgJmd0OyBjOlxhYWEudHh0                                                                                                     |
   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | \__system__encrypted | No              | String          | Specifies encryption in **metadata**. The value can be **0** (encryption disabled) or **1** (encryption enabled).                                      |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 | If this parameter does not exist, the system disk will not be encrypted by default.                                                                    |
   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | \__system__cmkid     | No              | String          | Specifies the CMK ID, which indicates encryption in **metadata**. This parameter is used with **\__system__encrypted**.                                |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 | .. note::                                                                                                                                              |
   |                      |                 |                 |                                                                                                                                                        |
   |                      |                 |                 |    For details about how to obtain the CMK ID, see "Querying the List of CMKs" in *Key Management Service API Reference*.                              |
   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

See `Responses (Task) <../../common_parameters/task_request_result/responses_task.html>`__.

Example Request
---------------

-  Example URL request

   .. code-block::

      POST https://{endpoint}/v2/{project_id}/cloudservers/{server_id}/changeos

-  Example request 1 (using a password to remotely log in to an ECS with OS changed)

   .. code-block::

      {
          "os-change": {
              "adminpass": "1qazXSW@", 
              "userid": "7e25b1da389f4697a79df3a0e5bd494e", 
              "imageid": "e215580f-73ad-429d-b6f2-5433947433b0"
          }
      }

-  Example request 2 (using a key to remotely log in to an ECS with OS changed)

   .. code-block::

      {
          "os-change": {
              "keyname": "KeyPair-350b", 
              "userid": "7e25b1da389f4697a79df3a0e5bd494e", 
              "imageid": "e215580f-73ad-429d-b6f2-5433947433b0"
          }
      }

-  Example request 3 (using a password to remotely log in a full-ECS-image-created ECS with OS changed and system disk encrypted)

   .. code-block::

      {
          "os-change": {
              "adminpass": "1qazXSW@", 
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

See `Responses (Task) <../../common_parameters/task_request_result/responses_task.html>`__.

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


