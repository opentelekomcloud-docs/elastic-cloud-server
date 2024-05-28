:original_name: en-us_topic_0122110044.html

.. _en-us_topic_0122110044:

Updating ECS Metadata
=====================

Function
--------

This API is used to update ECS metadata.

-  If the metadata does not contain the target field, the field is automatically added.
-  If the metadata contains the target field, the field value is automatically updated.
-  If the field in the metadata is not requested, the field value remains unchanged.

.. note::

   If the metadata contains sensitive data, take appropriate measures to protect the sensitive data, for example, controlling access permissions and encrypting the data.

Constraints
-----------

An ECS must be in active, stopped, paused, or suspended state, which is specified by **OS-EXT-STS:vm_state**.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/metadata

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================================+
   | metadata        | Yes             | Object          | Specifies the user-defined metadata key-value pair.                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | The data structure can be empty. If the value is empty, data is not updated.                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | For a metadata tag:                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | It contains a maximum of 255 Unicode characters and cannot be left blank. A tag can contain uppercase letters (A-Z), lowercase letters (a-z), digits (0-9), hyphens (-), underscores (_), colons (:), and periods (.). |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | For a metadata value:                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | It contains a maximum of 255 Unicode characters.                                                                                                                                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

.. table:: **Table 3** Parameter description

   ========= ====== ===================================================
   Parameter Type   Description
   ========= ====== ===================================================
   metadata  Object Specifies the user-defined metadata key-value pair.
   ========= ====== ===================================================

Example Request
---------------

Updated the metadata of an ECS to the user-defined metadata key-value pair.

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/metadata

   {
       "metadata": {
           "key": "value"
       }
   }

Example Response
----------------

.. code-block::

   {
       "metadata":{
           "key":"value"
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
