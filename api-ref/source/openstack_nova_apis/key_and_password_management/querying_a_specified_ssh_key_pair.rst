Querying a Specified SSH Key Pair
=================================

Function
--------

This API is used to query a specified SSH key pair based on the SSH key pair name.

URI
---

GET /v2.1/{project_id}/os-keypairs/{keypair_name}

GET /v2/{project_id}/os-keypairs/{keypair_name}

`Table 1 <#enustopic0020212677table51931981>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212677table51931981:

.. table:: **Table 1** Parameter description

   ============ ========= ============================
   Parameter    Mandatory Description
   ============ ========= ============================
   project_id   Yes       Specifies the project ID.
   keypair_name Yes       Specifies the key pair name.
   ============ ========= ============================

Request
-------

None

Response
--------

`Table 2 <#enustopic0020212677table49096623>`__ describes the response parameters. 

.. _ENUSTOPIC0020212677table49096623:

.. table:: **Table 2** Response parameters

   +-----------+--------+-----------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                   |
   +===========+========+===============================================================================================+
   | keypair   | Object | Specifies the SSH key pair. For details, see `Table 3 <#enustopic0020212677table32323009>`__. |
   +-----------+--------+-----------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212677table32323009:

.. table:: **Table 3** **keypair** field description

   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                         |
   +=======================+=======================+=====================================================================+
   | public_key            | String                | Specifies information about the public key.                         |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | name                  | String                | Specifies the key pair name.                                        |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | fingerprint           | String                | Specifies fingerprint information about the key pair.               |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | created_at            | String                | Specifies the time when the key pair was created.                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | deleted               | Boolean               | Specifies whether a key pair has been deleted.                      |
   |                       |                       |                                                                     |
   |                       |                       | -  **true**: indicates that the key has been deleted.               |
   |                       |                       | -  **false**: indicates that the key is not deleted.                |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | deleted_at            | String                | Specifies the time when the key pair was deleted.                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | id                    | Integer               | Specifies the key pair ID.                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | updated_at            | String                | Specifies the time when the key pair was updated.                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | user_id               | String                | Specifies information about the user to which the key pair belongs. |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | type                  | String                | Specifies the key type, which is **ssh** by default.                |
   |                       |                       |                                                                     |
   |                       |                       | This parameter is supported in microversion 2.2 and later.          |
   +-----------------------+-----------------------+---------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/{project_id}/os-keypairs/{keypair_name}
   GET https://{endpoint}/v2.1/{project_id}/os-keypairs/{keypair_name}

Example Response
----------------

.. code-block::

   {
       "keypair": {
           "created_at": "2014-05-07T12:06:13.681238",
           "deleted": false,
           "deleted_at": null,
           "fingerprint": "9d:00:f4:d7:26:6e:52:06:4c:c1:d3:1d:fd:06:66:01",
           "id": 1,
           "name": "keypair-3582d8b7-e588-4aad-b7f7-f4e76f0e4314",
           "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDYJrTVpcMwFqQy/oMvtUSRofZdSRHEwrsX8AYkRvn2ZnCXM+b6+GZ2NQuuWj+ocznlnwiGFQDsL/yeE+/kurqcPJFKKp60mToXIMyzioFxW88fJtwEWawHKAclbHWpR1t4fQ4DS+/sIbX/Yd9btlVQ2tpQjodGDbM9Tr9/+/3i6rcR+EoLqmbgCgAiGiVV6VbM2Zx79yUwd+GnQejHX8BlYZoOjCnt3NREsITcmWE9FVFy6TnLmahs3FkEO/QGgWGkaohAJlsgaVvSWGgDn2AujKYwyDokK3dXyeX3m2Vmc3ejiqPa/C4nRrCOlko5nSgV/9IXRx1ERImsqZnE9usB Generated-by-Nova\n",
           "updated_at": null,
           "user_id": "fake"
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


