:original_name: en-us_topic_0065792794.html

.. _en-us_topic_0065792794:

Querying a Specified API Version
================================

Function
--------

This API is used to query the information of a specified version.

To support function extension, Nova APIs can be distinguished by version. There are two types of versions:

-  Major version: Independent URL
-  Microversion: Used by the HTTP request header X-OpenStack-Nova-API-Version. Since version 2.27, the new microversion header OpenStack-API-Version has been supported.

   .. note::

      If the OpenStack-API-Version request header is used, the version is in the format of "compute microversion".

      For example, if **key** is set to **OpenStack-API-Version**, set **value** to **compute 2.27**.

URI
---

GET /{api_version}

:ref:`Table 1 <en-us_topic_0065792794__table46110007>` describes the parameters in the URI.

.. _en-us_topic_0065792794__table46110007:

.. table:: **Table 1** Parameter description

   =========== ========= =====================================
   Parameter   Mandatory Description
   =========== ========= =====================================
   api_version Yes       Specifies an API version, such as V2.
   =========== ========= =====================================

Request
-------

None

Response
--------

The following table describes the response parameters.

.. table:: **Table 2** Response parameters

   +-----------+--------+-------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                           |
   +===========+========+=======================================================================================================+
   | versions  | Object | Specifies the versions. For details, see :ref:`Table 3 <en-us_topic_0065792794__table1970522313484>`. |
   +-----------+--------+-------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065792794__table1970522313484:

.. table:: **Table 3** **versions** field description

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                            |
   +=======================+=======================+========================================================================================================================================================================================+
   | id                    | string                | Specifies the version ID.                                                                                                                                                              |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | links                 | Object                | Specifies the links to resources. For more information, see the `OpenStack Documentation <https://docs.openstack.org/api-guide/compute/links_and_references.html>`__.                  |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | For details, see :ref:`Table 4 <en-us_topic_0065792794__table1586318199718>`.                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | media-types           | Object                | Specifies the media types. For details, see :ref:`Table 5 <en-us_topic_0065792794__table1242753025619>`.                                                                               |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_version           | string                | -  Specifies the microversion. If the APIs of this version support microversions, set this parameter to the supported minimum microversion.                                            |
   |                       |                       | -  If the microversion is not supported, leave this parameter blank.                                                                                                                   |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | string                | Specifies the API version status. Possible values are as follows:                                                                                                                      |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | -  **CURRENT**: This is the preferred API version.                                                                                                                                     |
   |                       |                       | -  **SUPPORTED**: This is the old API version that is still supported.                                                                                                                 |
   |                       |                       | -  **DEPRECATED**: This is the deprecated API version that will be removed.                                                                                                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated               | string                | The value of this parameter varies by API version. If the API version is 2.0, the value is **2011-01-21T11:33:21Z**. If the API version is 2.1, the value is **2013-07-23T11:33:21Z**. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version               | string                | -  Specifies the microversion. If the APIs of this version support microversions, set this parameter to the supported maximum microversion.                                            |
   |                       |                       | -  If the microversion is not supported, leave this parameter blank.                                                                                                                   |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065792794__table1586318199718:

.. table:: **Table 4** **links** field description

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                 |
   +=======================+=======================+=============================================================================================================================================================================================================+
   | href                  | string                | Specifies the links of the corresponding resources.                                                                                                                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rel                   | string                | -  **self**: A self link contains a versioned link to the resource. Use these links when the link is followed immediately.                                                                                  |
   |                       |                       | -  **bookmark**: A bookmark link provides a permanent link to a resource that is appropriate for long term storage.                                                                                         |
   |                       |                       | -  **alternate**: An alternate link can contain an alternate representation of the resource. For example, an OpenStack Compute image might have an alternate representation in the OpenStack Image service. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065792794__table1242753025619:

.. table:: **Table 5** **media-types** field description

   ========= ====== =========================
   Parameter Type   Description
   ========= ====== =========================
   base      string Specifies the basic type.
   type      string Specifies the media type.
   ========= ====== =========================

Example Request
---------------

Query information about a specified API version.

.. code-block:: text

   GET https://{endpoint}/v2.1

Example Response
----------------

.. code-block::

   {
       "version":{
           "min_version":"2.1",
           "media-types":[
               {
                   "type":"application/vnd.openstack.compute+json;version=2.1",
                   "base":"application/json"
               }
           ],
           "links":[
               {
                   "rel":"self",
                   "href":"https://{endpoint}/v2.1/"
               },
               {
                   "rel":"describedby",
                   "href":"http://docs.openstack.org/",
                   "type":"text/html"
               }
           ],
           "id":"v2.1",
           "updated":"2013-07-23T11:33:21Z",
           "version":"2.60",
           "status":"CURRENT"
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
