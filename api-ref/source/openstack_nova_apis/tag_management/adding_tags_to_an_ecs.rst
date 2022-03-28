Adding Tags to an ECS
=====================

This API is used to add tags to an ECS.

You are required to use the HTTP header **X-OpenStack-Nova-API-Version: 2.26** to specify the microversion on the client.

URI
---

PUT /v2.1/{project_id}/servers/{server_id}/tags

`Table 1 <#enustopic0065820823enustopic0057972838table32475667>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065820823enustopic0057972838table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0065820823enustopic0057972838table28387752>`__ describes the request parameters.



.. _ENUSTOPIC0065820823enustopic0057972838table28387752:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                           |
   +=================+=================+==================+=======================================================================================+
   | tags            | Yes             | Array of strings | Specifies ECS tags.                                                                   |
   |                 |                 |                  |                                                                                       |
   |                 |                 |                  | A maximum of 50 tags can be configured, and each tag can contain up to 80 characters. |
   |                 |                 |                  |                                                                                       |
   |                 |                 |                  | Can only consist of digits, letters, hyphens (-), and underscores (_).                |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------+

Response
--------



.. _ENUSTOPIC0065820823table1481741123815:

.. table:: **Table 3** Response parameters

   ========= ========= ================ ===================
   Parameter Mandatory Type             Description
   ========= ========= ================ ===================
   tags      Yes       Array of strings Specifies ECS tags.
   ========= ========= ================ ===================



.. _ENUSTOPIC0065820823table5668174110389:

.. table:: **Table 4** Reserved tag parameters

   ================= ====================================
   Tag Name          Description
   ================= ====================================
   \__type_baremetal Specifies that the server is a BMS.
   \__type_virtual   Specifies that the server is an ECS.
   ================= ====================================

Example Request
---------------

.. code-block::

   PUT https://{endpoint}/v2.1/{project_id}/servers/{server_id}/tags

.. code-block::

   { 
      "tags": ["baz", "foo", "qux"]
   }

Example Response
----------------

.. code-block::

   { 
      "tags": ["baz", "foo", "qux"]
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


