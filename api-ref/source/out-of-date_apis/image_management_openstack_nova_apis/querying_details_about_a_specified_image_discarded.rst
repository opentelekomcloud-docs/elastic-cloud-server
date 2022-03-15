Querying Details About a Specified Image (Discarded)
====================================================

Function
--------

This API is used to query the details about the specified image.

This API has been discarded. Use the API described in "Querying Images (Native OpenStack API)".

URI
---

GET /v2/{project_id}/images/{image_id}

GET /v2.1/{project_id}/images/{image_id}

`Table 1 <#enustopic0065817697table105393143396>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817697table105393143396:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   image_id   Yes       Specifies the image ID.
   ========== ========= =========================

Request
-------

None

Response
--------

`Table 2 <#enustopic0065817697table128661753193915>`__ describes the response parameters.



.. _ENUSTOPIC0065817697table128661753193915:

.. table:: **Table 2** Response parameters

   +----------------------+------------------+------------------------------------------------------------------------------------------------------+
   | Parameter            | Type             | Description                                                                                          |
   +======================+==================+======================================================================================================+
   | id                   | String           | Specifies the image ID in UUID format.                                                               |
   +----------------------+------------------+------------------------------------------------------------------------------------------------------+
   | links                | Array of objects | Specifies the shortcut link of the image.                                                            |
   +----------------------+------------------+------------------------------------------------------------------------------------------------------+
   | name                 | String           | Specifies the image name.                                                                            |
   +----------------------+------------------+------------------------------------------------------------------------------------------------------+
   | metadata             | Object           | Specifies the key pair of the metadata.                                                              |
   +----------------------+------------------+------------------------------------------------------------------------------------------------------+
   | OS-EXT-IMG-SIZE:size | Integer          | Specifies the image size. The value must be greater than zero.                                       |
   +----------------------+------------------+------------------------------------------------------------------------------------------------------+
   | minDisk              | Integer          | Specifies the minimum disk size in GB required by the image. The value must be greater than zero.    |
   +----------------------+------------------+------------------------------------------------------------------------------------------------------+
   | minRam               | Integer          | Specifies the minimum memory size in GB required by the image. The value must be greater than zero.  |
   +----------------------+------------------+------------------------------------------------------------------------------------------------------+
   | progress             | Integer          | Specifies the image upload progress. The value must be greater than zero.                            |
   +----------------------+------------------+------------------------------------------------------------------------------------------------------+
   | status               | String           | Specifies the image status.                                                                          |
   +----------------------+------------------+------------------------------------------------------------------------------------------------------+
   | created              | String           | Specifies the image creation time. The value is in ISO8601 format, such as **2013-06-09T06:42:18Z**. |
   +----------------------+------------------+------------------------------------------------------------------------------------------------------+
   | updated              | String           | Specifies the image update time. The value is in ISO8601 format, such as **2013-06-09T06:42:18Z**.   |
   +----------------------+------------------+------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817697table82851550164111:

.. table:: **Table 3** **links** parameter description

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

   GET https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/images/17a1890b-0fa4-485e-8505-14e294017988
   GET https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/images/17a1890b-0fa4-485e-8505-14e294017988

Example Response
----------------

.. code-block::

   {
       "image": {
           "status": "ACTIVE", 
           "updated": "2015-12-27T02:52:25Z", 
           "name": "cirror", 
           "links": [
               {
                   "href": "https://compute.localdomain.com:8001/v2/719e9483f42d4784a089862ac4c3e8d0/images/17a1890b-0fa4-485e-8505-14e294017988", 
                   "rel": "self"
               }, 
               {
                   "href": "https://compute.localdomain.com:8001/719e9483f42d4784a089862ac4c3e8d0/images/17a1890b-0fa4-485e-8505-14e294017988", 
                   "rel": "bookmark"
               }, 
               {
                   "href": "https://https://image.az2.dc1.domainname.com:443/719e9483f42d4784a089862ac4c3e8d0/images/17a1890b-0fa4-485e-8505-14e294017988", 
                   "type": "application/vnd.openstack.image", 
                   "rel": "alternate"
               }
           ], 
           "created": "2015-12-27T02:52:24Z", 
           "minDisk": 0, 
           "progress": 100, 
           "minRam": 0, 
           "metadata": {
               "__os_version": "CentOS 4.4 32bit", 
               "file_format": "img", 
               "file_name": "**.img", 
               "describe": "", 
               "__os_type": "Linux", 
               "virtual_env_type": "KVM", 
               "hw_disk_bus": "scsi"
           }, 
           "id": "17a1890b-0fa4-485e-8505-14e294017988", 
           "OS-EXT-IMG-SIZE:size": 13167616
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


