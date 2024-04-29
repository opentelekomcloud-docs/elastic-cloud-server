:original_name: en-us_topic_0020212678.html

.. _en-us_topic_0020212678:

Creating and Importing an SSH Key Pair
======================================

Function
--------

This API is used to create an SSH key pair or import a public key to generate a key pair.

After a private SSH key is created, download the private key to a local directory. Then, you can use this private key to log in to the ECS. To ensure ECS security, the private key can be downloaded only once. Keep it secure.

Only the user that created the key pair can view it. If the key pair is created by an IAM user, the IAM account of the user and the other users of the same account cannot view the key pair.

URI
---

POST /v2.1/{project_id}/os-keypairs

POST /v2/{project_id}/os-keypairs

:ref:`Table 1 <en-us_topic_0020212678__table909717>` describes the parameters in the URI.

.. _en-us_topic_0020212678__table909717:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0020212678__table8287277>` describes the request parameters.

.. note::

   When creating an SSH key, you only need to configure **name**. When importing an SSH key, you must configure **public_key**.

.. _en-us_topic_0020212678__table8287277:

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                              |
   +===========+===========+========+==========================================================================================================================+
   | keypair   | Yes       | Object | Specifies the created or imported SSH key pair. For details, see :ref:`Table 3 <en-us_topic_0020212678__table54046809>`. |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212678__table54046809:

.. table:: **Table 3** **keypair** field description

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                               |
   +=================+=================+=================+===========================================================================================================+
   | public_key      | No              | String          | Specifies the imported public key.                                                                        |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | It is recommended that the length of the imported public key be less than or equal to 1024 bytes.         |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | .. note::                                                                                                 |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 |    If the length of the public key to be imported exceeds 1024 bytes, importing the public key will fail. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | Specifies the key type. The value is **ssh** or **x509**.                                                 |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | This parameter is supported in microversion 2.2 and later.                                                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | name            | Yes             | String          | Specifies the key pair name.                                                                              |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | The new key pair name cannot be the same as an existing one.                                              |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | user_id         | No              | String          | Specifies the user ID of the key.                                                                         |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | This parameter is supported in microversion 2.10 and later.                                               |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 4 <en-us_topic_0020212678__table51598880>` describes the response parameters.

.. _en-us_topic_0020212678__table51598880:

.. table:: **Table 4** Response parameters

   +-----------+--------+------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                          |
   +===========+========+======================================================================================================+
   | keypair   | Object | Specifies the SSH key pair. For details, see :ref:`Table 5 <en-us_topic_0020212678__table51079899>`. |
   +-----------+--------+------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212678__table51079899:

.. table:: **Table 5** **keypair** field description

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                         |
   +=======================+=======================+=====================================================================================================+
   | fingerprint           | String                | Specifies fingerprint information about the key pair.                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the key pair name.                                                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+
   | public_key            | String                | Specifies information about the public key.                                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+
   | private_key           | String                | Specifies information about the private key.                                                        |
   |                       |                       |                                                                                                     |
   |                       |                       | -  The information about the private key is contained in the response for creating an SSH key.      |
   |                       |                       | -  The information about the private key is not contained in the response for importing an SSH key. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+
   | user_id               | String                | Specifies the ID of the user to which the key pair belongs.                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+
   | type                  | String                | Specifies the key type. The value is **ssh** or **x509**.                                           |
   |                       |                       |                                                                                                     |
   |                       |                       | This parameter is supported in microversion 2.2 and later.                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+

Example Request
---------------

-  Import an SSH key.

   .. code-block:: text

      POST https://{endpoint}/v2/{project_id}/os-keypairs
      POST https://{endpoint}/v2.1/{project_id}/os-keypairs

      {
          "keypair": {
              "public_key": "ssh-rsaAAAAB3NzaC1yc2EAAAADAQABAAABAQDWNgTxQYeBzK9LYy4IakX7IsIl5j5zqR6BU2GJaEg3RK6dlS7rKFQhvy/V/1emK+GT/7P8up9VsMZ9Dx6PBOLow5p+2/wGsMlwDJpW*************************************************************************************************************************************************************************************************************************** Generated-by-Nova\\n\n",
              "type": "ssh",
              "name": "demo1",
              "user_id": "fake"
          }
      }

-  Create an SSH key.

   .. code-block:: text

      POST https://{endpoint}/v2/{project_id}/os-keypairs
      POST https://{endpoint}/v2.1/{project_id}/os-keypairs

      {
          "keypair": {
              "name": "demo"
          }
      }

Example response
----------------

Importing an SSH Key

.. code-block::

   {
       "keypair": {
           "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDWNgTxQYeBzK9LYy4IakX7IsIl5j5zqR6BU2GJaEg3RK6dlS7rKFQhvy/V/1emK+GT/7P8up9VsMZ9Dx6PBOLow5p+2/wGsMlwDJpWiQ8zNnE********************************************************************************************************************************************************************************************************************************************* Generated-by-Nova\\n\n",
           "user_id": "6fc0d2cbbfab40b199874b97097e913d",
           "name": "demo1",
           "fingerprint": "fc:47:b5:c3:7d:25:32:**:**:**:**:**:**:**:**:**"
       }
   }

Creating an SSH Key

.. code-block::

   {
       "keypair": {
           "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDWNgTxQYeBzK9LYy4IakX7IsIl5j5zqR6BU2GJaEg3RK6dlS7rKFQhvy/V/1emK+GT/7P8up9VsMZ9Dx6PBOLow5p+2/wGsMlwDJpWiQ8zNnE********************************************************************************************************************************************************************************************************************************************* Generated-by-Nova\n",
           "private_key": "-----BEGIN RSA PRIVATE KEY-----\nMIIEpQIBAAKCAQEA1jYE8UGHgcyvS2MuCGpF+yLCJeY+c6kegVNhiWhIN0SunZUu\n6yhUIb8v1f9Xpivhk/+z/LqfVbDGfQ8ejwTi6MOaftv8BrDJcAyaVokPMzZxDIPr\nvwK/2YWBwDMihADjicSHJz6FIMXzXY/3ol1ffAGm7AXVAO0A99DoPBeAZp9pYov1\ng/Sm0EFY2+5Gwd4DSCaRk1HKF+92q6K6pKv6aWi0ZpsDCe20yBpfP9DFlNg8vnkw\ncjmgzG9obWwfo/GV8hLuzqKMtDWknfjzR79z2fTiFTu4HdZcqE0bwjCvxd+Ovs5m\nbZORAEkjseUYn50sJNzbboFY17PRjCXxSwUYmwIDAQABAoIBADNKQ+ywUA3YQLDA\nUqlZKOB09h+0/YccG13D5TrNaV0yaMz6h31u7pYV/RI0TXxQTXbuZt5AoR4Xca9I\nC30bImmxTDDL45CGi/T0T5AgyS7t/iuM+smFkwI2YVbv53fL7q9yCxpucdnjC95/\nNj/+M3qxupIQ42uRVAYCU1jwF6J6YLy/9UamrmVd4bWFRtT19O7uszUhHLqJOZXq\n3ItqnMyD5bSMkzMN+RxmZVXAPkBOonGVeBBInCjvHv23REkngX38zcUSc543H3Di\n4673helqSdMnI0/TgyfLQcNuOsfQcD02A**********************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************\n-----END RSA PRIVATE KEY-----\n",
           "user_id": "6fc0d2cbbfab40b199874b97097e913d",
           "type": "ssh",
           "name": "demo",
           "fingerprint": "fc:47:b5:c3:7d:25:32:**:**:**:**:**:**:**:**:**"
      }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
