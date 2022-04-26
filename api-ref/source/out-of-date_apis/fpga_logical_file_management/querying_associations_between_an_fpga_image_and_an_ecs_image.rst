:original_name: en-us_topic_0081950550.html

.. _en-us_topic_0081950550:

Querying Associations Between an FPGA Image and an ECS Image
============================================================

Function
--------

This API is used to query associations that are available to a tenant and between an FPGA image and an ECS image.

URI
---

GET /v1/{project_id}/cloudservers/fpga_image/associations?image_id={image_id}&fpga_image_id={fpga_image_id}&page={page}&size={size}

:ref:`Table 1 <en-us_topic_0081950550__table35325481211756>` describes the parameters in the URI.

.. _en-us_topic_0081950550__table35325481211756:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                              |
   +=======================+=======================+==========================================================================+
   | project_id            | Yes                   | Specifies the project ID.                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | image_id              | No                    | Specifies the ECS image ID.                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | fpga_image_id         | No                    | Specifies the FPGA image ID.                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | page                  | No                    | Specifies the number of pages in a pagination query.                     |
   |                       |                       |                                                                          |
   |                       |                       | The value of this parameter must meet the following requirements:        |
   |                       |                       |                                                                          |
   |                       |                       | -  Must be a decimal integer.                                            |
   |                       |                       | -  Ranges from 1 (inclusive) to 65,535 (exclusive).                      |
   |                       |                       | -  Cannot contain **+**.                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | size                  | No                    | Specifies the maximum records displayed on a page in a pagination query. |
   |                       |                       |                                                                          |
   |                       |                       | -  Must be a decimal integer.                                            |
   |                       |                       | -  Ranges from 1 (inclusive) to 100 (inclusive).                         |
   |                       |                       | -  Cannot contain **+**.                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+

.. note::

   -  You can obtain the association only after specifying either **fpga_image_id** or **image_id**. Otherwise, only one empty list is returned.
   -  Pagination query takes effect only if parameters **page** and **size** both have a value. If only one of them has a value, an error message indicating invalid parameter will be displayed. If both **image_id** and **fpga_image_id** are used, pagination query specified by **page** and **size** does not take effect.

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0081950550__table41782128362>` describes the response parameters.

.. _en-us_topic_0081950550__table41782128362:

.. table:: **Table 2** Response parameters

   ============ ================ ===============================
   Parameter    Type             Description
   ============ ================ ===============================
   associations Array of objects Specifies queried associations.
   ============ ================ ===============================

.. table:: **Table 3** **associations** field description

   ========== ================ ============================================
   Parameter  Type             Description
   ========== ================ ============================================
   image_id   String           Specifies the ECS ID.
   fpgaimages Array of objects Specifies details of associated FPGA images.
   ========== ================ ============================================

.. table:: **Table 4** **fpgaimages** field description

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                  |
   +=======================+=======================+==============================================================================================================================================================================+
   | id                    | String                | Specifies the FPGA image ID.                                                                                                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the FPGA image name.                                                                                                                                               |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Describes the FPGA image.                                                                                                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                | Specifies the FPGA image status. Options:                                                                                                                                    |
   |                       |                       |                                                                                                                                                                              |
   |                       |                       | -  **active**: indicates that the FPGA image is available for use.                                                                                                           |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size                  | Integer               | Specifies the size (MB) of the FPGA image file.                                                                                                                              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | createdAt             | String                | Specifies the time when the FPGA image was created.                                                                                                                          |
   |                       |                       |                                                                                                                                                                              |
   |                       |                       | UTC time is used.                                                                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protected             | Boolean               | Specifies whether an FPGA image is protected.                                                                                                                                |
   |                       |                       |                                                                                                                                                                              |
   |                       |                       | If an FPGA image is protected, it is associated with an image used to create ECSs and cannot be deleted.                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message               | String                | Specifies the FPGA image supplementation.                                                                                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata              | Object                | Specifies the FPGA image metadata.                                                                                                                                           |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_directory         | String                | Specifies the directory, in the format of "Bucket name:Directory", in which the log file for constructing the FPGA image is stored in OBS, for example, "obs-fpga:vu9p/log". |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v1/{project_id}/cloudservers/fpga_image/associations

Example Response
----------------

.. code-block::

   { 
     "associations": [ 
       { 
         "image_id": "89e38a0a-de83-4f3d-83b9-a2df2c605487", 
         "fpgaimages": [ 
           { 
             "id": "4010a32b5f231f04015f24259efd0429", 
             "name": "relate-test", 
             "description": "relate-test", 
             "status": "active", 
             "size": 40, 
             "createdAt": "2017-10-16 07:46:06", 
             "protected": true, 
             "message": null, 
             "metadata": { 
               "shell_type": "OCL", 
               "shell_version": "1.0" 
             },
             "log_directory": "obs-fpga:vu9p/log"
           }, 
           { 
             "id": "4010a32b5f231f04015f23f0c07c041a", 
             "name": "name123", 
             "description": "desc123", 
             "status": "active", 
             "size": 60, 
             "createdAt": "2017-10-16 06:48:21", 
             "protected": true, 
             "message": null, 
             "metadata": { 
               "shell_type": "OCL", 
               "shell_version": "1.0" 
             },
             "log_directory": "obs-fpga:vu9p/log"
           } 
         ] 
       } 
     ] 
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
