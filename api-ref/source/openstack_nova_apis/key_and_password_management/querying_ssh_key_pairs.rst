:original_name: en-us_topic_0020212676.html

.. _en-us_topic_0020212676:

Querying SSH Key Pairs
======================

Function
--------

This API is used to query SSH key pairs.

URI
---

GET /v2.1/{project_id}/os-keypairs

GET /v2/{project_id}/os-keypairs

:ref:`Table 1 <en-us_topic_0020212676__table38623499>` describes the parameters in the URI.

.. _en-us_topic_0020212676__table38623499:

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

:ref:`Table 2 <en-us_topic_0020212676__table46959463>` describes the response parameters.

.. _en-us_topic_0020212676__table46959463:

.. table:: **Table 2** Response parameters

   +-----------+------------------+-----------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                   |
   +===========+==================+===============================================================================================+
   | keypairs  | Array of objects | Specifies key pairs. For details, see :ref:`Table 3 <en-us_topic_0020212676__table41882197>`. |
   +-----------+------------------+-----------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212676__table41882197:

.. table:: **Table 3** **keypairs** field description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                  |
   +===========+========+==============================================================================================================+
   | keypair   | Object | Specifies details about a key pair. For details, see :ref:`Table 4 <en-us_topic_0020212676__table48408329>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212676__table48408329:

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

.. code-block:: text

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
