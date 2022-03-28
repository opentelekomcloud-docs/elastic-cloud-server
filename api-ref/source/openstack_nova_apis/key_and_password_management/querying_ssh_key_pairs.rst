Querying SSH Key Pairs
======================

Function
--------

This API is used to query SSH key pairs.

URI
---

GET /v2.1/{project_id}/os-keypairs

GET /v2/{project_id}/os-keypairs

`Table 1 <#enustopic0020212676table38623499>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212676table38623499:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

None

Response
--------

`Table 2 <#enustopic0020212676table46959463>`__ describes the response parameters. 

.. _ENUSTOPIC0020212676table46959463:

.. table:: **Table 2** Response parameters

   +-----------+------------------+----------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                            |
   +===========+==================+========================================================================================+
   | keypairs  | Array of objects | Specifies key pairs. For details, see `Table 3 <#enustopic0020212676table41882197>`__. |
   +-----------+------------------+----------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212676table41882197:

.. table:: **Table 3** **keypairs** field description

   +-----------+--------+-------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                           |
   +===========+========+=======================================================================================================+
   | keypair   | Object | Specifies details about a key pair. For details, see `Table 4 <#enustopic0020212676table48408329>`__. |
   +-----------+--------+-------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212676table48408329:

.. table:: **Table 4** **keypair** field description

   +-----------------------+-----------------------+------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                |
   +=======================+=======================+============================================================+
   | fingerprint           | String                | Specifies fingerprint information about the key pair.      |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | name                  | String                | Specifies the key pair name.                               |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | type                  | String                | Specifies the key type, which is **ssh** by default.       |
   |                       |                       |                                                            |
   |                       |                       | This parameter is supported in microversion 2.2 and later. |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | public_key            | String                | Specifies information about the public key.                |
   +-----------------------+-----------------------+------------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/{project_id}/os-keypairs
   GET https://{endpoint}/v2.1/{project_id}/os-keypairs

Example Response
----------------

.. code-block::

   {
       "keypairs": [
           {
               "keypair": {
                   "fingerprint": "15:b0:f8:b3:f9:48:63:71:cf:7b:5b:38:6d:44:2d:4a",
                   "name": "keypair-601a2305-4f25-41ed-89c6-2a966fc8027a",
                   "type": "ssh",
                   "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAAAgQC+Eo/RZRngaGTkFs7I62ZjsIlO79KklKbMXi8F+KITD4bVQHHn+kV+4gRgkgCRbdoDqoGfpaDFs877DYX9n4z6FrAIZ4PES8TNKhatifpn9NdQYWA+IkU8CuvlEKGuFpKRi/k7JLos/gHi2hy7QUwgtRvcefvD/vgQZOVw/mGR9Q== Generated-by-Nova\n"
               }
           }
       ]
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


