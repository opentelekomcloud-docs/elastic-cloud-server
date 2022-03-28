Querying Networks
=================

Function
--------

This API is used to query the networks available to a tenant.

Constraints
-----------

You can query only the network ID and label (network name). Other fields are all null.

URI
---

GET /v2.1/{project_id}/os-networks

GET /v2/{project_id}/os-networks

`Table 1 <#enustopic0031169828table60562285165259>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0031169828table60562285165259:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

None

Response
--------

`Table 2 <#enustopic0031169828table50321718145545>`__ describes the response parameters. 

.. _ENUSTOPIC0031169828table50321718145545:

.. table:: **Table 2** Response parameters

   +------------+-----------+--------+------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                          |
   +============+===========+========+======================================================+
   | id         | Yes       | String | Specifies the network ID in UUID format.             |
   +------------+-----------+--------+------------------------------------------------------+
   | label      | Yes       | String | Specifies the network name.                          |
   +------------+-----------+--------+------------------------------------------------------+
   | broadcast  | Yes       | String | The value can only be null.                          |
   +------------+-----------+--------+------------------------------------------------------+
   | cidr       | Yes       | String | The value can only be null.                          |
   +------------+-----------+--------+------------------------------------------------------+
   | cidr_v6    | Yes       | String | The value can only be null.                          |
   +------------+-----------+--------+------------------------------------------------------+
   | dns1       | Yes       | String | The value can only be null.                          |
   +------------+-----------+--------+------------------------------------------------------+
   | dns2       | Yes       | String | The value can only be null.                          |
   +------------+-----------+--------+------------------------------------------------------+
   | gateway    | Yes       | String | The value can only be null.                          |
   +------------+-----------+--------+------------------------------------------------------+
   | gateway_v6 | Yes       | String | The value can only be null.                          |
   +------------+-----------+--------+------------------------------------------------------+
   | netmask    | Yes       | String | The value can only be null.                          |
   +------------+-----------+--------+------------------------------------------------------+
   | netmask_v6 | Yes       | String | The value can only be null.                          |
   +------------+-----------+--------+------------------------------------------------------+
   | bridge     | No        | String | The value is fixed to be null and is in UUID format. |
   +------------+-----------+--------+------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/{project_id}/os-networks
   GET https://{endpoint}/v2.1/{project_id}/os-networks

Example Response
----------------

.. code-block::

   {
       "networks": [
           {
               "id": "04468f37-500a-4a80-88da-af823e7a1d6c",
               "cidr_v6": null,
               "gateway": null,
               "label": "network_demo1",
               "broadcast": null,
               "netmask": null,
               "cidr": null,
               "dns2": null,
               "gateway_v6": null,
               "netmask_v6": null,
               "dns1": null
           },
           {
               "id": "1fcff959-21d0-4ba8-976a-974cb564c977",
               "cidr_v6": null,
               "gateway": null,
               "label": "network_demo2",
               "broadcast": null,
               "netmask": null,
               "cidr": null,
               "dns2": null,
               "gateway_v6": null,
               "netmask_v6": null,
               "dns1": null
           }
       ]
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


