Querying Tags of an ECS
=======================

This API is used to query all tags of an ECS.

You are required to use the HTTP header **X-OpenStack-Nova-API-Version: 2.26** to specify the microversion on the client.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/tags

`Table 1 <#enustopic0065820822enustopic0057972837table32475667>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065820822enustopic0057972837table32475667:

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

`Table 2 <#enustopic0065820822enustopic0057972838table28387752>`__ describes the response parameters.



.. _ENUSTOPIC0065820822enustopic0057972838table28387752:

.. table:: **Table 2** Response parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                     |
   +=======================+=======================+=================================================================================================================================================+
   | tags                  | Array of strings      | Specifies ECS tags.                                                                                                                             |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | Tag functions have been upgraded on the public cloud. After the upgrade, the tag values returned by the system comply with the following rules: |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  The key and value of a tag are connected using an equal sign (=), for example, key=value.                                                    |
   |                       |                       | -  If the value is empty, only the key is returned.                                                                                             |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | For more details about upgraded tag functions, see `Tag Types <../../openstack_nova_apis/tag_management/tag_types.html>`__.                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2.1/{project_id}/servers/{server_id}/tags

Example Response
----------------

Example response

.. code-block::

   { 
       "tags": ["baz=xyy", "foo", "qux"]
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


