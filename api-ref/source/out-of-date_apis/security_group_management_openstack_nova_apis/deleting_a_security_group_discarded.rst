Deleting a Security Group (Discarded)
=====================================

Function
--------

This API is used to delete a security group.

This API has been discarded. Use the API described in section "Security Group (OpenStack Neutron APIs) > Deleting a Security Group" in *Virtual Private Network API Reference*.

URI
---

DELETE /v2/{project_id}/os-security-groups/{security_group_id}

DELETE /v2.1/{project_id}/os-security-groups/{security_group_id}

`Table 1 <#enustopic0065817701enustopic0057972665table55945983>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817701enustopic0057972665table55945983:

.. table:: **Table 1** Parameter description

   +-------------------+-----------+-----------------------------------------------------------------+
   | Parameter         | Mandatory | Description                                                     |
   +===================+===========+=================================================================+
   | project_id        | Yes       | Specifies the project ID.                                       |
   +-------------------+-----------+-----------------------------------------------------------------+
   | security_group_id | Yes       | Specifies the security group ID, which is specified in the URI. |
   +-------------------+-----------+-----------------------------------------------------------------+

Request
-------

None

Response
--------

None

Example Request
---------------

.. code-block::

   DELETE https://{endpoint}/v2/bb1118612ba64af3a6ea63a1bdcaa5ae/os-security-groups/81f1d23b-b1e2-42cd-bdee-359b4a065a42
   DELETE https://{endpoint}/v2.1/bb1118612ba64af3a6ea63a1bdcaa5ae/os-security-groups/81f1d23b-b1e2-42cd-bdee-359b4a065a42

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


