:original_name: en-us_topic_0065817719.html

.. _en-us_topic_0065817719:

Unbinding a Floating IP Address (Discarded)
===========================================

Function
--------

This API is used to unbind a floating IP address from an ECS.

This API has been discarded. Since microversion 2.44, the system will return error 404 when you call this API. You are advised to use the VPC API "Updating a Floating IP Address".

URI
---

POST /v2/{project_id}/servers/{server_id}/action

POST /v2.1/{project_id}/servers/{server_id}/action

:ref:`Table 1 <en-us_topic_0065817719__en-us_topic_0057973008_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0065817719__en-us_topic_0057973008_table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0065817719__en-us_topic_0057973008_table20592177>` describes the request parameters.

.. _en-us_topic_0065817719__en-us_topic_0057973008_table20592177:

.. table:: **Table 2** Request parameter

   +------------------+-----------+--------+--------------------------------------------+
   | Parameter        | Mandatory | Type   | Description                                |
   +==================+===========+========+============================================+
   | removeFloatingIp | Yes       | Object | Unbinds a floating IP address from an ECS. |
   +------------------+-----------+--------+--------------------------------------------+

.. table:: **Table 3** **removeFloatingIp** parameter information

   ========= ========= ====== ==================================
   Parameter Mandatory Type   Description
   ========= ========= ====== ==================================
   address   Yes       String Specifies the floating IP address.
   ========= ========= ====== ==================================

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
      "removeFloatingIp" : {
           "address" : "10.144.2.1"
       }
   }

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
