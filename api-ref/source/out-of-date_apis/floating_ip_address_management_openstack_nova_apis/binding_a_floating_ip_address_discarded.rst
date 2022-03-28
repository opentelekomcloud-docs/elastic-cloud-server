Binding a Floating IP Address (Discarded)
=========================================

Function
--------

This API is used to bind a floating IP address for an ECS.

This API has been discarded. Since microversion 2.44, the system will return error 404 when you call this API. You are advised to use the VPC API "Updating a Floating IP Address".

URI
---

POST /v2/{project_id}/servers/{server_id}/action

POST /v2.1/{project_id}/servers/{server_id}/action

`Table 1 <#enustopic0065817718enustopic0057972997table32475667>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817718enustopic0057972997table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0065817718enustopic0057972997table49322741>`__ describes the request parameters.



.. _ENUSTOPIC0065817718enustopic0057972997table49322741:

.. table:: **Table 2** Request parameter

   +---------------+-----------+--------+----------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                              |
   +===============+===========+========+==========================================================+
   | addFloatingIp | Yes       | Object | Specifies the floating IP address to be bound to an ECS. |
   +---------------+-----------+--------+----------------------------------------------------------+



.. _ENUSTOPIC0065817718enustopic0057972997table58252101:

.. table:: **Table 3** **addFloatingIp** parameter information

   +---------------+-----------+--------+-------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                   |
   +===============+===========+========+===============================================================================+
   | address       | Yes       | String | Specifies the floating IP address.                                            |
   +---------------+-----------+--------+-------------------------------------------------------------------------------+
   | fixed_address | No        | String | Specifies the fixed IP address with which the floating IP address associates. |
   +---------------+-----------+--------+-------------------------------------------------------------------------------+

Response
--------

None

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/servers/47e9be4e-a7b9-471f-92d9-ffc83814e07a/action
   POST https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/servers/47e9be4e-a7b9-471f-92d9-ffc83814e07a/action

.. code-block::

   {
      "addFloatingIp" : {
          "address" : "10.144.2.1",
          "fixed_address" : "192.168.1.3"
       }
   }

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


