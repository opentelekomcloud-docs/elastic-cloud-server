Obtaining a VNC-based Remote Login Address (Microversion 2.6 or Later)
======================================================================

Function
--------

This API is used to obtain the address for remotely logging in to an ECS using VNC.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/remote-consoles

`Table 1 <#enustopic0142763126enustopic0092803065table55945983>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0142763126enustopic0092803065table55945983:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Constraints
-----------

-  When using this API, ensure that the microversion is 2.6 or later.

   Add a microversion using the HTTP request header X-OpenStack-Nova-API-Version or OpenStack-API-Version.

   For example, X-OpenStack-Nova-API-Version: 2.6 or OpenStack-API-Version: compute 2.6

-  An obtained login address is valid for 10 minutes. Obtain a new one after expiration.

Request
-------



.. _ENUSTOPIC0142763126table2421133916364:

.. table:: **Table 2** Request parameters

   +----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                                                              |
   +================+===========+========+==========================================================================================================================================+
   | remote_console | Yes       | Object | Obtains the address for remotely logging in to an ECS using VNC. For details, see `Table 3 <#enustopic0142763126table19959184318164>`__. |
   +----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0142763126table19959184318164:

.. table:: **Table 3** **remote_console** parameters

   +-----------+-----------+--------+-------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                           |
   +===========+===========+========+=======================================================+
   | type      | Yes       | String | Specifies a remote login mode. Set it to **novnc**.   |
   +-----------+-----------+--------+-------------------------------------------------------+
   | protocol  | Yes       | String | Specifies a remote login protocol. Set it to **vnc**. |
   +-----------+-----------+--------+-------------------------------------------------------+

Response
--------

`Table 4 <#enustopic0142763126table8420447171011>`__ describes the response parameters.



.. _ENUSTOPIC0142763126table8420447171011:

.. table:: **Table 4** Response parameters

   +----------------+--------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type   | Description                                                                                                                    |
   +================+========+================================================================================================================================+
   | remote_console | Object | Obtains the address for remotely logging in to an ECS. For details, see `Table 5 <#enustopic0142763126table12434194718104>`__. |
   +----------------+--------+--------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0142763126table12434194718104:

.. table:: **Table 5** **remote_console** parameters

   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                         |
   +=======================+=======================+=====================================================================+
   | type                  | String                | Specifies a remote login mode.                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | protocol              | String                | Specifies a remote login protocol.                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | url                   | String                | Specifies a remote login URL.                                       |
   |                       |                       |                                                                     |
   |                       |                       | The URL is valid for 10 minutes. Obtain a new one after expiration. |
   +-----------------------+-----------------------+---------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2.1/13c67a214ced4afb88d911ae4bd5721a/servers/47bc79ae-df61-4ade-9197-283a74e5d70e/remote-consoles

.. code-block::

   {
      "remote_console" : {
           "type" : "novnc",
           "protocol": "vnc"
       }
   }

Example Response
----------------

.. code-block::

   {
       "remote_console": {
           "url": "https://nova-novncproxy.az21.dc1.domainname.com:8002/vnc.auto.html?token=80fa7c8d-37fe-451e-8b08-bfbd9fb6a4df&lang=EN",
           "type": "novnc",
           "protocol": "vnc"
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


