:original_name: en-us_topic_0020212680.html

.. _en-us_topic_0020212680:

Deleting an SSH Key Pair
========================

Function
--------

This API is used to delete a specified SSH key pair based on the SSH key pair name.

URI
---

DELETE /v2.1/{project_id}/os-keypairs/{keypair_name}

DELETE /v2/{project_id}/os-keypairs/{keypair_name}

:ref:`Table 1 <en-us_topic_0020212680__table48776445>` describes the parameters in the URI.

.. _en-us_topic_0020212680__table48776445:

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

.. code-block:: text

   DELETE https://{endpoint}/v2/{project_id}/os-keypairs/{keypair_name}
   DELETE https://{endpoint}/v2.1/{project_id}/os-keypairs/{keypair_name}

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
