Deleting an ECS Group
=====================

Function
--------

This API is used to delete an ECS group.

URI
---

DELETE /v1/{project_id}/cloudservers/os-server-groups/{server_group_id}

`Table 1 <#enustopic0161097719table1962114910318>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0161097719table1962114910318:

.. table:: **Table 1** Parameter description

   =============== ========= =============================
   Parameter       Mandatory Description
   =============== ========= =============================
   project_id      Yes       Specifies the project ID.
   server_group_id Yes       Specifies the ECS group UUID.
   =============== ========= =============================

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Request
---------------

.. code-block::

   DELETE https://{endpoint}/v1/{project_id}/cloudservers/os-server-groups/{server_group_id}

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


