.. _en-us_topic_0065962600:

Viewing Details of FPGA Images
==============================

Function
--------

This API is used to view the details of the FPGA images of a tenant.

URI
---

GET /v1/{project_id}/cloudservers/fpga_image/detail?fpga_image_id={fpga_image_id}&page={page}&size={size}

:ref:`Table 1 <en-us_topic_0065962600__table972014396283>` describes the parameters in the URI.

.. _en-us_topic_0065962600__table972014396283:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                              |
   +=======================+=======================+==========================================================================+
   | project_id            | Yes                   | Specifies the project ID.                                                |
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

   -  Pagination query takes effect only if parameters **page** and **size** both have a value. If only one of them has a value, an error message indicating invalid parameter will be displayed.
   -  If **fpga_image_id** is used, pagination query specified by **page** and **size** does not take effect.

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0065962600__table41782128362>` describes the response parameters.

.. _en-us_topic_0065962600__table41782128362:

.. table:: **Table 2** Response parameters

   +------------+------------------+----------------------------------------------------+
   | Parameter  | Type             | Description                                        |
   +============+==================+====================================================+
   | count      | Integer          | Specifies the number of FPGA images to be queried. |
   +------------+------------------+----------------------------------------------------+
   | fpgaimages | Array of objects | Specifies details of FPGA images.                  |
   +------------+------------------+----------------------------------------------------+

.. table:: **Table 3** **fpgaimages** field description

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
   |                       |                       | -  **initialing**: indicates that the task of creating an FPGA image is being initialized.                                                                                   |
   |                       |                       | -  **scheduling**: indicates that the task of creating an FPGA image is waiting for scheduling.                                                                              |
   |                       |                       | -  **creating**: indicates that the FPGA image is being created.                                                                                                             |
   |                       |                       | -  **saving**: indicates that the FPGA image file is being uploaded to the backend storage.                                                                                  |
   |                       |                       | -  **deleting**: indicates that the FPGA image is being deleted.                                                                                                             |
   |                       |                       | -  **error**: indicates that creating the FPGA image failed.                                                                                                                 |
   |                       |                       | -  **active**: indicates that the FPGA image is available for use.                                                                                                           |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size                  | Integer               | Specifies the size (MB) of the FPGA image file.                                                                                                                              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | createdAt             | String                | Specifies the time when the FPGA image was created.                                                                                                                          |
   |                       |                       |                                                                                                                                                                              |
   |                       |                       | Coordinated Universal Time (UTC) time is used.                                                                                                                               |
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

   GET https://{endpoint}/v1/{project_id}/cloudservers/fpga_image/detail

Example Response
----------------

.. code-block::

   { 
     "count": 2, 
     "fpgaimages": [ 
       { 
         "id": "4010a32c5c7d7711015c81ac714c009d", 
         "name": "FPGA001", 
         "description": "fpga test", 
         "status": "active", 
         "size": 40, 
         "createdAt": "2017-06-07 08:29:41", 
         "protected": false, 
         "message": null, 
         "metadata": { 
           "shell_type": "OCL", 
           "shell_version": "1.0" 
         },
         "log_directory": "obs-fpga:vu9p/log"
       }, 
       { 
         "id": "4010a32c5c7d7711015c813e69bd002c", 
         "name": "FPGA002", 
         "description": "fpga test", 
         "status": "active", 
         "size": 43, 
         "createdAt": "2017-06-07 16:29:30", 
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

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
