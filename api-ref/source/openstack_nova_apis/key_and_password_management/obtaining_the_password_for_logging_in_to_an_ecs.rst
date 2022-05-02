:original_name: en-us_topic_0031176553.html

.. _en-us_topic_0031176553:

Obtaining the Password for Logging In to an ECS
===============================================

Function
--------

This API is used to obtain the random password generated during initial Windows ECS installation for user **Administrator** or the configured **Cloudbase-init** user when you use an image that supports Cloudbase-Init to create a Windows ECS.

After starting an ECS, wait for 5 to 10 minutes and ensure that the password is injected. Then, you can use this API to query the password.

Linux ECSs do not use this API to obtain a password.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/os-server-password

GET /v2/{project_id}/servers/{server_id}/os-server-password

:ref:`Table 1 <en-us_topic_0031176553__table46110007>` describes the parameters in the URI.

.. _en-us_topic_0031176553__table46110007:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0031176553__table23477058>` describes the response parameters.

.. _en-us_topic_0031176553__table23477058:

.. table:: **Table 2** Response parameters

   ========= ====== =====================================
   Parameter Type   Description
   ========= ====== =====================================
   password  String Specifies the password in ciphertext.
   ========= ====== =====================================

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/servers/{server_id}/os-server-password
   GET https://{endpoint}/v2.1/{project_id}/servers/{server_id}/os-server-password

Example Response
----------------

.. code-block::

   {
       "password": "UHC9+YW1xDC1Yu8Mg9n+tnOp7euEO/cW//9KgdJKWhr5w=="
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
