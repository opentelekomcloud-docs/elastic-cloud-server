Deleting the Password for Logging In to an ECS
==============================================

Function
--------

This API is used to delete the recorded random password generated during initial Windows ECS installation. After the password is deleted, you can still use your password to log in to your ECS. However, you cannot use the **Get Password** function to recover the ECS initial password.

Linux ECSs do not use this API to delete a password.

URI
---

DELETE /v2.1/{project_id}/servers/{server_id}/os-server-password

DELETE /v2/{project_id}/servers/{server_id}/os-server-password

`Table 1 <#enustopic0031176554table46110007>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0031176554table46110007:

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

None

Example Request
---------------

.. code-block::

   DELETE https://{endpoint}/v2/{project_id}/servers/{server_id}/os-server-password
   DELETE https://{endpoint}/v2.1/{project_id}/servers/{server_id}/os-server-password

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


