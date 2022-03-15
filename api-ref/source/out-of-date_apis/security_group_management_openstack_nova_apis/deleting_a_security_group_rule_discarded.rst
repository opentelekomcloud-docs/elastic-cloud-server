Deleting a Security Group Rule (Discarded)
==========================================

Function
--------

This API is used to delete a security group rule.

This API has been discarded. Use the API described in section "Security Group (OpenStack Neutron APIs) > Deleting a Security Group Rule" in *Virtual Private Network API Reference*.

URI
---

DELETE /v2/{project_id}/os-security-group-rules/{security_group_rule_id}

DELETE /v2.1/{project_id}/os-security-group-rules/{security_group_rule_id}

`Table 1 <#enustopic0065817704enustopic0057972668table32475667>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817704enustopic0057972668table32475667:

.. table:: **Table 1** Parameter description

   +------------------------+-----------+----------------------------------------------------------------------+
   | Parameter              | Mandatory | Description                                                          |
   +========================+===========+======================================================================+
   | project_id             | Yes       | Specifies the project ID.                                            |
   +------------------------+-----------+----------------------------------------------------------------------+
   | security_group_rule_id | Yes       | Specifies the security group rule ID, which is specified in the URI. |
   +------------------------+-----------+----------------------------------------------------------------------+

Request
-------

None

Response
--------

None

Example Request
---------------

Example request

.. code-block::

   DELETE https://{endpoint}/v2/3d72597871904daeb6887f75f848b531/os-security-group-rules/012fa2c6-bf4a-4b0b-b893-70d0caee81c7
   DELETE https://{endpoint}/v2.1/3d72597871904daeb6887f75f848b531/os-security-group-rules/012fa2c6-bf4a-4b0b-b893-70d0caee81c7

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


