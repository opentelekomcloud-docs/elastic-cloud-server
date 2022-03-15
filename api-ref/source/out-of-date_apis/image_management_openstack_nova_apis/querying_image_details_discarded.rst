Querying Image Details (Discarded)
==================================

Function
--------

This API is used to query detailed information about an image list.

This API has been discarded. Use the API described in "Querying Images (Native OpenStack API)".

URI
---

GET /v2/{project_id}/images/detail?name={name}&status={status}&changes-since={changes-since}&minRam={minRam}&minDisk={inDisk}

GET /v2.1/{project_id}/images/detail?name={name}&status={status}&changes-since={changes-since}&minRam={minRam}&minDisk={inDisk}

`Table 1 <#enustopic0065817696table2497448193514>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817696table2497448193514:

.. table:: **Table 1** Path parameters

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Parameters in the following table can be used as URI parameters to filter query results. Usage: /v2/{tenant_id}/images/detail? name ={name}&status={status}

`Table 2 <#enustopic0065817696table8153553113616>`__ describes the query parameters.



.. _ENUSTOPIC0065817696table8153553113616:

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                    |
   +=================+=================+=================+================================================================================================================================================================================================================================+
   | name            | No              | String          | Specifies the image name.                                                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | Specifies the image status.                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                |
   |                 |                 |                 | You cannot query images when the value is set to **deleted**. The value depends on the status in Glance. `Table 3 <#enustopic0065817696table84817387373>`__ shows the mapping relationship of image status in Nova and Glance. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | changes-since   | No              | String          | Specifies the images modified after the **changes-since** time point. The value is in ISO8601 format, such as **2013-06-09T06:42:18Z**.                                                                                        |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | minRam          | No              | Integer         | Specifies the minimum memory size in MB required by the image.                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | minDisk         | No              | Integer         | Specifies the minimum disk size in GB required by the image.                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817696table84817387373:

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

`Table 4 <#enustopic0065817696table510182515381>`__ describes the response parameters.



.. _ENUSTOPIC0065817696table510182515381:

.. table:: **Table 4** Response parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                       |
   +=======================+=======================+===================================================================+
   | id                    | String                | Specifies the image ID in UUID format.                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | links                 | Array of objects      | Specifies the shortcut link of the image.                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | name                  | String                | Specifies the image name.                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | metadata              | Object                | Specifies the key pair of the metadata.                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | OS-EXT-IMG-SIZE:size  | Integer               | Specifies the image size.                                         |
   |                       |                       |                                                                   |
   |                       |                       | The value must be greater than zero.                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | minDisk               | Integer               | Specifies the minimum disk size in GB required by the image.      |
   |                       |                       |                                                                   |
   |                       |                       | The value must be greater than zero.                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | minRam                | Integer               | Specifies the minimum memory size in GB required by the image.    |
   |                       |                       |                                                                   |
   |                       |                       | The value must be greater than zero.                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | progress              | Integer               | Specifies the image upload progress.                              |
   |                       |                       |                                                                   |
   |                       |                       | The value must be greater than zero.                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | status                | String                | Specifies the image status.                                       |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | created               | String                | Specifies the image creation time.                                |
   |                       |                       |                                                                   |
   |                       |                       | The value is in ISO8601 format, such as **2013-06-09T06:42:18Z**. |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | updated               | String                | Specifies the image update time.                                  |
   |                       |                       |                                                                   |
   |                       |                       | The value is in ISO8601 format, such as **2013-06-09T06:42:18Z**. |
   +-----------------------+-----------------------+-------------------------------------------------------------------+



.. _ENUSTOPIC0065817696table06801854144013:

.. table:: **Table 5** **links** parameter description

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

   GET https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/images/detail
   GET https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/images/detail

Example Response
----------------

.. code-block::

   {
       "image": {
           "OS-EXT-IMG-SIZE:size": 20578304,
           "created": "2014-02-10T17:05:01Z",
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
           "metadata": {
               "clean_attempts": "3",
               "image_location": "snapshot",
               "image_state": "available",
               "image_type": "snapshot",
               "instance_type_ephemeral_gb": "0",
               "instance_type_flavorid": "6",
               "instance_type_id": "7",
               "instance_type_memory_mb": "256",
               "instance_type_name": "wj.ssd",
               "instance_type_root_gb": "2",
               "instance_type_rxtx_factor": "1.0",
               "instance_type_swap": "0",
               "instance_type_vcpus": "1",
               "instance_uuid": "b600b5b1-ed8c-4814-aefa-8b903c894c20",
               "os_type": "None",
               "owner_id": "d9ebe43510414ef590a4aa158605329e",
               "user_id": "74fe4ff0674b434b8a274077d8106c5b"
           },
           "minDisk": 2,
           "minRam": 0,
           "name": "image1",
           "progress": 100,
           "server": {
               "id": "b600b5b1-ed8c-4814-aefa-8b903c894c20",
               "links": [
                   {
                       "href": "http://172.25.150.84:8774/v2/d9ebe43510414ef590a4aa158605329e/servers/b600b5b1-ed8c-4814-aefa-8b903c894c20",
                       "rel": "self"
                   },
                   {
                       "href": "http://172.25.150.84:8774/d9ebe43510414ef590a4aa158605329e/servers/b600b5b1-ed8c-4814-aefa-8b903c894c20",
                       "rel": "bookmark"
                   }
               ]
           },
           "status": "ACTIVE",
           "updated": "2014-02-10T17:05:07Z"
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


