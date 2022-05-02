:original_name: en-us_topic_0065817728.html

.. _en-us_topic_0065817728:

Querying AZs
============

Function
--------

This API is used to query AZs.

URI
---

GET /v2.1/{project_id}/os-availability-zone

GET /v2/{project_id}/os-availability-zone

:ref:`Table 1 <en-us_topic_0065817728__en-us_topic_0057973206_table2814978410562>` describes the parameters in the URI.

.. _en-us_topic_0065817728__en-us_topic_0057973206_table2814978410562:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Response
--------

:ref:`Table 2 <en-us_topic_0065817728__en-us_topic_0057973206_table34970028>` describes the response parameters.

.. _en-us_topic_0065817728__en-us_topic_0057973206_table34970028:

.. table:: **Table 2** Response parameters

   +----------------------+------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Type             | Description                                                                                                                  |
   +======================+==================+==============================================================================================================================+
   | availabilityZoneInfo | Array of objects | Specifies the AZ information. For details, see :ref:`Table 3 <en-us_topic_0065817728__en-us_topic_0057973206_table4376441>`. |
   +----------------------+------------------+------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817728__en-us_topic_0057973206_table4376441:

.. table:: **Table 3** AvailabilityZoneInfo parameter information

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                              |
   +===========+========+==========================================================================================================================+
   | zoneState | Object | Specifies the AZ status. For details, see :ref:`Table 4 <en-us_topic_0065817728__en-us_topic_0057973206_table37797818>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | hosts     | List   | The parameter is set to **null**.                                                                                        |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | zoneName  | String | Specifies the AZ name.                                                                                                   |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817728__en-us_topic_0057973206_table37797818:

.. table:: **Table 4** zoneState parameter information

   ========= ======= ========================
   Parameter Type    Description
   ========= ======= ========================
   available Boolean Specifies the AZ status.
   ========= ======= ========================

Example Request
---------------

.. code-block:: text

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
