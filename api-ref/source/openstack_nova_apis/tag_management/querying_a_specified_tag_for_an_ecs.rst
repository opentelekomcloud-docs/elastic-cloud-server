Querying a Specified Tag for an ECS
===================================

This API is used to query whether an ECS has a specified tag.

You are required to use the HTTP header **X-OpenStack-Nova-API-Version: 2.26** to specify the microversion on the client.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/tags/{tag}

`Table 1 <#enustopic0065820826enustopic0057972841table32475667>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065820826enustopic0057972841table32475667:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================================================+
   | project_id            | Yes                   | Specifies the project ID.                                                                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | server_id             | Yes                   | Specifies the ECS ID.                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tag                   | Yes                   | Specifies the key of the tag to be queried. If no key is specified, all tags of the ECS will be displayed.                                                          |
   |                       |                       |                                                                                                                                                                     |
   |                       |                       | For details about key rules, see `Tag Types <../../openstack_nova_apis/tag_management/tag_types.html>`__.                                                           |
   |                       |                       |                                                                                                                                                                     |
   |                       |                       | .. note::                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                     |
   |                       |                       |    Tag functions have been upgraded on the public cloud. If the tags added before the function upgrade are in the format of "Key.Value", query tags using "Key".    |
   |                       |                       |                                                                                                                                                                     |
   |                       |                       |    For example, an existing tag is "a.b". The tag can be queried in the format of "tag=a.b" before and in the format of "tag=a" now according to the new tag rules. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

None

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2.1/{project_id}/servers/{server_id}/tags/{tag}

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


