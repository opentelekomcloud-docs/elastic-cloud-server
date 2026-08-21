:original_name: en-us_topic_0025567413.html

.. _en-us_topic_0025567413:

Modifying ECS Metadata with a Specified Key
===========================================

Function
--------

This API is used to modify the ECS metadata with a specified key.

-  If the metadata does not contain the target field, the field is automatically added.
-  If the metadata contains the target field, the field value is automatically updated.

Constraints
-----------

An ECS must be in active, stopped, paused, or suspended state, which is specified by **OS-EXT-STS:vm_state**.

URI
---

PUT /v2.1/{project_id}/servers/{server_id}/metadata/{key}

PUT /v2/{project_id}/servers/{server_id}/metadata/{key}

:ref:`Table 1 <en-us_topic_0025567413__table258804192629>` describes the parameters in the URI.

.. _en-us_topic_0025567413__table258804192629:

.. table:: **Table 1** Parameter description

   ========== ========= ===============================
   Parameter  Mandatory Description
   ========== ========= ===============================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   key        Yes       Specifies the ECS metadata key.
   ========== ========= ===============================

Request
-------

:ref:`Table 2 <en-us_topic_0025567413__table21113531192629>` describes the request parameters.

.. _en-us_topic_0025567413__table21113531192629:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================+
   | meta            | Yes             | Object          | Specifies the user-defined metadata key pair.                                                                                                        |
   |                 |                 |                 |                                                                                                                                                      |
   |                 |                 |                 | For a metadata key:                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                      |
   |                 |                 |                 | It cannot be left blank. Only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), colons (:), and periods (.) are supported. |
   |                 |                 |                 |                                                                                                                                                      |
   |                 |                 |                 | For a metadata value:                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                      |
   |                 |                 |                 | A maximum of 255 characters are supported.                                                                                                           |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 3 <en-us_topic_0025567413__table34681280192629>` describes the response parameters.

.. _en-us_topic_0025567413__table34681280192629:

.. table:: **Table 3** Response parameters

   ========= ====== ===================================================
   Parameter Type   Description
   ========= ====== ===================================================
   meta      Object Specifies the user-defined metadata key-value pair.
   ========= ====== ===================================================

Example Request
---------------

Set the metadata with a specified key of an ECS.

.. code-block:: text

   PUT https://{endpoint}/v2/{project_id}/servers/{server_id}/metadata/{key}
   PUT https://{endpoint}/v2.1/{project_id}/servers/{server_id}/metadata/{key}

   {
       "meta":{
           "key":"value"
       }
   }

Example Response
----------------

.. code-block::

   {
       "meta":{
           "key":"value"
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
