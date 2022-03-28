Deleting an ECS Group
=====================

Function
--------

This API is used to delete an ECS group.

URI
---

DELETE /v2.1/{project_id}/os-server-groups/{server_group_id}

DELETE /v2/{project_id}/os-server-groups/{server_group_id}

`Table 1 <#enustopic0065817723table105214393178>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817723table105214393178:

.. table:: **Table 1** Parameter description

   =============== ========= =============================
   Parameter       Mandatory Description
   =============== ========= =============================
   project_id      Yes       Specifies the project ID.
   server_group_id Yes       Specifies the ECS group UUID.
   =============== ========= =============================

Request
-------

None

Response
--------

None

Example Request
---------------

.. code-block::

   DELETE https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/os-server-groups/5bbcc3c4-1da2-4437-a48a-66f15b1b13f9
   DELETE https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/os-server-groups/5bbcc3c4-1da2-4437-a48a-66f15b1b13f9

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


