Adding a Security Group
=======================

Function
--------

This API is used to add an ECS to a security group.

You are suggested to add an ECS to a maximum of five security groups.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

`Table 1 <#enustopic0067161469table55945983>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0067161469table55945983:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0067161469enustopic0058745339table44724688204850>`__ describes the request parameters.



.. _ENUSTOPIC0067161469enustopic0058745339table44724688204850:

.. table:: **Table 2** Request parameter

   +------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory | Type   | Description                                                                                                                                     |
   +==================+===========+========+=================================================================================================================================================+
   | addSecurityGroup | Yes       | Object | Specifies the security group where the ECS is added. For details, see `Table 3 <#enustopic0067161469enustopic0058745339table59377750205027>`__. |
   +------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0067161469enustopic0058745339table59377750205027:

.. table:: **Table 3** **addSecurityGroup** parameter description

   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                         |
   +===========+===========+========+=====================================================================================================================================+
   | name      | Yes       | String | Specifies the UUID or name of the security group to which the ECS is added. The configuration takes effect for the NICs on the ECS. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

None

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

.. code-block::

   { 
       "addSecurityGroup": { 
           "name": "sg-test"
       }
   }

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


