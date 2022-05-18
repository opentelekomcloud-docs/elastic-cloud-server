:original_name: en-us_topic_0065820822.html

.. _en-us_topic_0065820822:

Querying Tags of an ECS
=======================

This API is used to query all tags of an ECS.

You are required to use the HTTP header **X-OpenStack-Nova-API-Version: 2.26** to specify the microversion on the client.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/tags

:ref:`Table 1 <en-us_topic_0065820822__en-us_topic_0057972837_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0065820822__en-us_topic_0057972837_table32475667:

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

:ref:`Table 2 <en-us_topic_0065820822__en-us_topic_0057972838_table28387752>` describes the response parameters.

.. _en-us_topic_0065820822__en-us_topic_0057972838_table28387752:

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
   |                       |                       | For more details about upgraded tag functions, see :ref:`Tag Types <en-us_topic_0065817686>`.                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
