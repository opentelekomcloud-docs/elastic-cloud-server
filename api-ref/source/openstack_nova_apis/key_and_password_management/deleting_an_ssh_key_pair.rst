Deleting an SSH Key Pair
========================

Function
--------

This API is used to delete a specified SSH key pair based on the SSH key pair name.

URI
---

DELETE /v2.1/{project_id}/os-keypairs/{keypair_name}

DELETE /v2/{project_id}/os-keypairs/{keypair_name}

`Table 1 <#enustopic0020212680table48776445>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212680table48776445:

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

None

Example Request
---------------

.. code-block::

   DELETE https://{endpoint}/v2/{project_id}/os-keypairs/{keypair_name}
   DELETE https://{endpoint}/v2.1/{project_id}/os-keypairs/{keypair_name}

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


