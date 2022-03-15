Adding a Tag to an ECS
======================

This API is used to add a tag to an ECS.

You are required to use the HTTP header **X-OpenStack-Nova-API-Version: 2.26** to specify the microversion on the client.

Constraints
-----------

-  The tag contains a maximum of 80 characters.
-  A tag can only consist of digits, letters, hyphens (-), and underscores (_).
-  A maximum of 50 tags can be added to an ECS.
-  An empty tag cannot be created.

URI
---

PUT /v2.1/{project_id}/servers/{server_id}/tags/{tag}

`Table 1 <#enustopic0065820825enustopic0057972840table32475667>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065820825enustopic0057972840table32475667:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================================================+
   | project_id            | Yes                   | Specifies the project ID.                                                                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | server_id             | Yes                   | Specifies the ECS ID.                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tag                   | Yes                   | Specifies the key of the tag to be added.                                                                                                                           |
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



.. _ENUSTOPIC0065820825table1481741123815:

.. table:: **Table 2** Response parameters

   ========= ====== =============================
   Parameter Type   Description
   ========= ====== =============================
   message   String Example: "<br /><br />\n\n\n"
   code      String Example: "201 Created"
   title     String Example: "Created"
   ========= ====== =============================

Example Request
---------------

.. code-block::

   PUT https://{endpoint}/v2.1/{project_id}/servers/{server_id}/tags/{tag}

Example Response
----------------

By default, the response is in HTML format.

.. code-block::

   <html>
   <head>
         <title>201 Created</title>
   </head>
   <body>
         <h1>201 Created</h1>
         <br /><br />



   </body>
   </html>

JSON format

.. code-block::

   {
      "message": "<br /><br />\n\n\n",
      "code": "201 Created",
      "title": "Created"
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


