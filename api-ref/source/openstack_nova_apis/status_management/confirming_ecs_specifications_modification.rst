Confirming ECS Specifications Modification
==========================================

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

`Table 1 <#enustopic0028714262table54458463165029>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0028714262table54458463165029:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0028714262table47783938165029>`__ describes the request parameters. 

.. _ENUSTOPIC0028714262table47783938165029:

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

.. code-block::

   POST https://{endpoint}/v2/{project_id}/servers/{server_id}/action
   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

.. code-block::

   {
       "confirmResize" : null
   }

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


