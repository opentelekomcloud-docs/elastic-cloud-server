:original_name: en-us_topic_0028714262.html

.. _en-us_topic_0028714262:

Confirming the Specifications Modification of an ECS
====================================================

Function
--------

This API is used to confirm the specifications modification of an ECS.

Constraints
-----------

Before calling this API, ensure that the ECS status (which can be queried using the API for querying details about the ECS) meets the following requirements:

OS-EXT-STS:vm_state=resized

OS-EXT-STS:task_state=""

status=VERIFY_RESIZE

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

:ref:`Table 1 <en-us_topic_0028714262__table54458463165029>` describes the parameters in the URI.

.. _en-us_topic_0028714262__table54458463165029:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0028714262__table47783938165029>` describes the request parameters.

.. _en-us_topic_0028714262__table47783938165029:

.. table:: **Table 2** Request parameters

   +---------------+-----------+------+--------------------------------------------------+
   | Parameter     | Mandatory | Type | Description                                      |
   +===============+===========+======+==================================================+
   | confirmResize | Yes       | Null | Confirms the modification to ECS specifications. |
   +---------------+-----------+------+--------------------------------------------------+

Response
--------

None

Example Request
---------------

Confirm the modifications to the specifications of a specified ECS.

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/servers/{server_id}/action
   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

   {
       "confirmResize" : null
   }

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
