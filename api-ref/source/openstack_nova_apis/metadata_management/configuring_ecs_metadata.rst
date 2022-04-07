.. _en-us_topic_0077847902:

Configuring ECS Metadata
========================

Function
--------

This API is used to configure ECS metadata.

When you call this API, all the metadata of this ECS will be deleted, and the ECS uses the value configured in the request.

Constraints
-----------

An ECS must be in active, stopped, paused, or suspended state, which is specified by **OS-EXT-STS:vm_state**.

URI
---

PUT /v2.1/{project_id}/servers/{server_id}/metadata

PUT /v2/{project_id}/servers/{server_id}/metadata

:ref:`Table 1 <en-us_topic_0077847902__en-us_topic_0057973166_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0077847902__en-us_topic_0057973166_table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0077847902__en-us_topic_0057973166_table58874912>` describes the request parameters.

.. _en-us_topic_0077847902__en-us_topic_0057973166_table58874912:

.. table:: **Table 2** Request

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================================================================================+
   | metadata        | Object          | Yes             | Specifies the user-defined metadata key-value pair.                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                      |
   |                 |                 |                 | For a metadata key:                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                      |
   |                 |                 |                 | A key contains a maximum of 255 Unicode characters and cannot be empty. A key can contain uppercase letters (A-Z), lowercase letters (a-z), digits (0-9), hyphens (-), underscores (_), colons (:), and periods (.). |
   |                 |                 |                 |                                                                                                                                                                                                                      |
   |                 |                 |                 | For a metadata value:                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                      |
   |                 |                 |                 | A value contains a maximum of 255 Unicode characters.                                                                                                                                                                |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 3 <en-us_topic_0077847902__en-us_topic_0057973166_table52843024>` describes the response parameters.

.. _en-us_topic_0077847902__en-us_topic_0057973166_table52843024:

.. table:: **Table 3** Response parameters

   ========= ====== ===================================================
   Parameter Type   Description
   ========= ====== ===================================================
   metadata  Object Specifies the user-defined metadata key-value pair.
   ========= ====== ===================================================

Example Request
---------------

.. code-block::

   PUT https://{endpoint}/v2/{project_id}/servers/{server_id}/metadata
   PUT https://{endpoint}/v2.1/{project_id}/servers/{server_id}/metadata

.. code-block::

   {
       "metadata": {
               "key1": "value1",
               "key2": "value2"
       }
   }

Example Response
----------------

.. code-block::

   {
       "metadata": {
               "key1": "value1",
               "key2": "value2"
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
