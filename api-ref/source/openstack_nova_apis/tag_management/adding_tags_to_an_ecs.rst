:original_name: en-us_topic_0065820823.html

.. _en-us_topic_0065820823:

Adding Tags to an ECS
=====================

This API is used to add tags to an ECS.

You are required to use the HTTP header **X-OpenStack-Nova-API-Version: 2.26** to specify the microversion on the client.

URI
---

PUT /v2.1/{project_id}/servers/{server_id}/tags

:ref:`Table 1 <en-us_topic_0065820823__en-us_topic_0057972838_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0065820823__en-us_topic_0057972838_table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0065820823__en-us_topic_0057972838_table28387752>` describes the request parameters.

.. _en-us_topic_0065820823__en-us_topic_0057972838_table28387752:

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

.. table:: **Table 3** Response parameters

   ========= ========= ================ ===================
   Parameter Mandatory Type             Description
   ========= ========= ================ ===================
   tags      Yes       Array of strings Specifies ECS tags.
   ========= ========= ================ ===================

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
