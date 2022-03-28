Querying All API Versions
=========================

Function
--------

This API is used to query all available Nova versions.

To support function extension, Nova APIs can be distinguished by version. There are two types of versions:

-  Major version: Independent URL
-  Microversion: Used by the HTTP request header X-OpenStack-Nova-API-Version. Since microversion 2.27, the new microversion header OpenStack-API-Version has been supported.

URI
---

GET /

Request
-------

None

Response
--------

The following table describes the response parameters.



.. _ENUSTOPIC0065792793table1456520231001:

.. table:: **Table 1** Response parameters

   +-----------+--------+--------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                      |
   +===========+========+==================================================================================================+
   | versions  | Object | Specifies the API versions. For details, see `Table 2 <#enustopic0065792793table16114143917>`__. |
   +-----------+--------+--------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065792793table16114143917:

.. table:: **Table 2** **versions** field description

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                 |
   +=======================+=======================+=============================================================================================================================================+
   | id                    | string                | Specifies the version ID.                                                                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | links                 | Object                | Specifies shortcut links for versions. For details, see `Table 3 <#enustopic0065792793table1586318199718>`__.                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | min_version           | string                | -  Specifies the microversion. If the APIs of this version support microversions, set this parameter to the supported minimum microversion. |
   |                       |                       | -  If the microversion is not supported, leave this parameter blank.                                                                        |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | string                | Specifies the API version status. Possible values are as follows:                                                                           |
   |                       |                       |                                                                                                                                             |
   |                       |                       | -  **CURRENT**: This is the preferred API version.                                                                                          |
   |                       |                       | -  **SUPPORTED**: This is the old API version that is still supported.                                                                      |
   |                       |                       | -  **DEPRECATED**: This is the deprecated API version that will be removed.                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | version               | string                | -  Specifies the microversion. If the APIs of this version support microversions, set this parameter to the supported maximum microversion. |
   |                       |                       | -  If the microversion is not supported, leave this parameter blank.                                                                        |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | updated               | string                | The value of this parameter varies by API version.                                                                                          |
   |                       |                       |                                                                                                                                             |
   |                       |                       | If the API version is 2.0, the value is **2011-01-21T11:33:21Z**. If the API version is 2.1, the value is **2013-07-23T11:33:21Z**.         |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065792793table1586318199718:

.. table:: **Table 3** **links** field description

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                |
   +=======================+=======================+============================================================================================================================+
   | href                  | string                | Specifies the links of the corresponding resources.                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | rel                   | string                | -  **self**: A self link contains a versioned link to the resource. Use these links when the link is followed immediately. |
   |                       |                       |                                                                                                                            |
   |                       |                       | -  **bookmark**: A bookmark link provides a permanent link to a resource that is appropriate for long term storage.        |
   |                       |                       |                                                                                                                            |
   |                       |                       | -  **alternate**: An alternate link can contain an alternate representation of the resource.                               |
   |                       |                       |                                                                                                                            |
   |                       |                       |    For example, an OpenStack Compute image might have an alternate representation in the OpenStack Image service.          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/

Example Response
----------------

.. code-block::

   {
    "versions": [{
     "links": [{
      "rel": "self",
      "href": "https://ecs.service.domain.com:443/v2/"
     }],
     "id": "v2.0",
     "updated": "2001-09-21T12:33:21Z",
     "status": "SUPPORTED"
    }]
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


