Querying AZs
============

Function
--------

This API is used to query AZs.

URI
---

GET /v2.1/{project_id}/os-availability-zone

GET /v2/{project_id}/os-availability-zone

`Table 1 <#enustopic0065817728enustopic0057973206table2814978410562>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817728enustopic0057973206table2814978410562:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Response
--------

`Table 2 <#enustopic0065817728enustopic0057973206table34970028>`__ describes the response parameters.



.. _ENUSTOPIC0065817728enustopic0057973206table34970028:

.. table:: **Table 2** Response parameters

   +----------------------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Type             | Description                                                                                                       |
   +======================+==================+===================================================================================================================+
   | availabilityZoneInfo | Array of objects | Specifies the AZ information. For details, see `Table 3 <#enustopic0065817728enustopic0057973206table4376441>`__. |
   +----------------------+------------------+-------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817728enustopic0057973206table4376441:

.. table:: **Table 3** AvailabilityZoneInfo parameter information

   +-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                   |
   +===========+========+===============================================================================================================+
   | zoneState | Object | Specifies the AZ status. For details, see `Table 4 <#enustopic0065817728enustopic0057973206table37797818>`__. |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | hosts     | List   | The parameter is set to **null**.                                                                             |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | zoneName  | String | Specifies the AZ name.                                                                                        |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817728enustopic0057973206table37797818:

.. table:: **Table 4** zoneState parameter information

   ========= ======= ========================
   Parameter Type    Description
   ========= ======= ========================
   available Boolean Specifies the AZ status.
   ========= ======= ========================

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/os-availability-zone
   GET https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/os-availability-zone

Example Response
----------------

.. code-block::

   {
       "availabilityZoneInfo": [{
           "zoneState": {
               "available": true
           },
           "hosts": null,
           "zoneName": "az1"   //Replace the value with the actual AZ name.
       },
       {
           "zoneState": {
               "available": true
           },
           "hosts": null,
           "zoneName": "az2"   //Replace the value with the actual AZ name.
       }]
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


