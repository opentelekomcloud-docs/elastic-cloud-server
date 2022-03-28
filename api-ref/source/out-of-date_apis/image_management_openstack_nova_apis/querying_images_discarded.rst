Querying Images (Discarded)
===========================

Function
--------

This API is used to query all images.

This API has been discarded. Use the API described in "Querying Images (Native OpenStack API)".

URI
---

GET /v2/{project_id}/images?name={name}&status={status}&changes-since={changes-since}&minRam={minRam}&minDisk={inDisk}

GET /v2.1/{project_id}/images?name={name}&status={status}&changes-since={changes-since}&minRam={minRam}&minDisk={inDisk}

`Table 1 <#enustopic0065817695table15332113010326>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817695table15332113010326:

.. table:: **Table 1** Path parameters

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Parameters in the following table can be used as URI parameters to filter query results. Usage: /v2/{project_id}/images? name ={name}&status={status}

`Table 2 <#enustopic0065817695table21481517103310>`__ describes the query parameters.



.. _ENUSTOPIC0065817695table21481517103310:

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================================================================================+
   | name            | No              | String          | Specifies the image name.                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | Specifies the image status.                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                  |
   |                 |                 |                 | You cannot query images when the value is set to **deleted**. The value depends on the status in Glance. `Table 3 <#enustopic0065817695table7740622133418>`__ shows the mapping relationship of image status in Nova and Glance. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | changes-since   | No              | String          | Specifies the images modified after the **changes-since** time point. The parameter is in ISO 8601 time format, for example, 2013-06-09T06:42:18Z.                                                                               |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | minRam          | No              | Integer         | Specifies the minimum memory size in MB required by the image.                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | minDisk         | No              | Integer         | Specifies the minimum disk size in GB required by the image.                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817695table7740622133418:

.. table:: **Table 3** Mapping relationship of image status in Nova and Glance

   ====================== ====================
   Image Status in Glance Image Status in Nova
   ====================== ====================
   queued                 saving
   saving                 saving
   active                 active
   deleted                deleted
   ====================== ====================

Request
-------

None

Response
--------

`Table 4 <#enustopic0065817695table199957019352>`__ describes the response parameters.



.. _ENUSTOPIC0065817695table199957019352:

.. table:: **Table 4** Response parameters

   +--------------+-----------+------------------+-------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type             | Description                                                                   |
   +==============+===========+==================+===============================================================================+
   | images       | Yes       | Array of objects | Specifies the image information.                                              |
   +--------------+-----------+------------------+-------------------------------------------------------------------------------+
   | images_links | No        | Array of objects | Specifies the information about the next page when you query images in pages. |
   +--------------+-----------+------------------+-------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817695enustopic0057973086table512095:

.. table:: **Table 5** **images** information

   +-----------+-----------+------------------+-------------------------------------------+
   | Parameter | Mandatory | Type             | Description                               |
   +===========+===========+==================+===========================================+
   | id        | Yes       | String           | Specifies the image ID in UUID format.    |
   +-----------+-----------+------------------+-------------------------------------------+
   | links     | Yes       | Array of objects | Specifies the shortcut link of the image. |
   +-----------+-----------+------------------+-------------------------------------------+
   | name      | Yes       | String           | Specifies the image name.                 |
   +-----------+-----------+------------------+-------------------------------------------+



.. _ENUSTOPIC0065817695enustopic0057973086table65862751:

.. table:: **Table 6** **images_links** parameters

   +-----------+-----------+--------+--------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                        |
   +===========+===========+========+====================================================================+
   | href      | Yes       | String | Specifies the URL of the next page when you query images in pages. |
   +-----------+-----------+--------+--------------------------------------------------------------------+
   | rel       | Yes       | String | Specifies the query direction when you query images in pages.      |
   +-----------+-----------+--------+--------------------------------------------------------------------+



.. _ENUSTOPIC0065817695enustopic0057973086table1949017543515:

.. table:: **Table 7** **links** parameter description

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================================================+
   | href            | Yes             | String          | Specifies the link of the corresponding resource.                                                                                                                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rel             | Yes             | String          | The value can be:                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                           |
   |                 |                 |                 | -  **self**: A self link contains a version link to the resource. Use these links when the link is followed immediately.                                                                                  |
   |                 |                 |                 | -  **bookmark**: A bookmark link provides a permanent link to a resource, which is suitable for long term storage.                                                                                        |
   |                 |                 |                 | -  **alternate**: An alternate link can contain an alternate representation of the resource. For example, an OpenStack Compute image may have an alternate representation in the OpenStack image service. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | The type attribute provides a hint as to the type of representation to expect when following the link.                                                                                                    |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/images
   GET https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/images

Example Response
----------------

.. code-block::

   {
       "images": [
           {
               "id": "ee10f19c-503c-44af-af2f-73d5e42f7a17",
               "links": [
                   {
                       "href": "http://172.25.150.84:8774/v2/d9ebe43510414ef590a4aa158605329e/images/ee10f19c-503c-44af-af2f-73d5e42f7a17",
                       "rel": "self"
                   },
                   {
                       "href": "http://172.25.150.84:8774/d9ebe43510414ef590a4aa158605329e/images/ee10f19c-503c-44af-af2f-73d5e42f7a17",
                       "rel": "bookmark"
                   },
                   {
                       "href": "http://172.25.150.84:9292/d9ebe43510414ef590a4aa158605329e/images/ee10f19c-503c-44af-af2f-73d5e42f7a17",
                       "rel": "alternate",
                       "type": "application/vnd.openstack.image"
                   }
               ],
               "name": "image1"
           }
       ]
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


