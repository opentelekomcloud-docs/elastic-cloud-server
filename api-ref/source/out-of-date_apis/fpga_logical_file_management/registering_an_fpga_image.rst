Registering an FPGA Image
=========================

Function
--------

This API is used to register an FPGA image.

An FPGA image, which is also called accelerated engine image (AEI), is a logic FPGA file developed by a user. During FPGA image registration, the logic file must be stored in the Object Storage Service (OBS) bucket of the user.

URI
---

POST /v1/{project_id}/cloudservers/fpga_image

`Table 1 <#enustopic0065962597table10080802211311>`__ describes the parameters in the URI.



.. _ENUSTOPIC0065962597table10080802211311:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0065962597table5698154011375>`__ describes the request parameters.



.. _ENUSTOPIC0065962597table5698154011375:

.. table:: **Table 2** Request parameters

   ========== ====== ========= ======================================
   Parameter  Type   Mandatory Description
   ========== ====== ========= ======================================
   fpga_image Object Yes       Indicates details about an FPGA image.
   ========== ====== ========= ======================================



.. _ENUSTOPIC0065962597table36632723211311:

.. table:: **Table 3** **fpga_image** field description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================================================================+
   | location        | String          | Yes             | Specifies the OBS bucket path in which the logic FPGA file is stored. The format of the path is "Bucket name:File name", for example, "obs-fpga:fpga.bin".                                        |
   |                 |                 |                 |                                                                                                                                                                                                   |
   |                 |                 |                 | Bucket naming rules comply with the following OBS requirements:                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                   |
   |                 |                 |                 | -  Consists of lowercase letters, digits, and special characters **.** and **-**.                                                                                                                 |
   |                 |                 |                 | -  Must start and end with a digit or letter.                                                                                                                                                     |
   |                 |                 |                 | -  Contains 3 to 63 characters.                                                                                                                                                                   |
   |                 |                 |                 | -  Cannot be an IP address.                                                                                                                                                                       |
   |                 |                 |                 | -  Cannot contain **..**, **.-**, or **-.**.                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                   |
   |                 |                 |                 | A file name must conform to the following rules:                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                   |
   |                 |                 |                 | -  Consists of uppercase and lowercase letters, digits, hyphens (-), underscores (_), slashes (/), and periods (.).                                                                               |
   |                 |                 |                 | -  Must end with **.bin** or **xclbin**.                                                                                                                                                          |
   |                 |                 |                 | -  Contains 4 to 64 characters.                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | String          | Yes             | Specifies the name of the FPGA image.                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                   |
   |                 |                 |                 | Value range:                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                   |
   |                 |                 |                 | -  Contains only letters, digits, underscores, and hyphens.                                                                                                                                       |
   |                 |                 |                 | -  Contains 1 to 64 characters.                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata        | Object          | Yes             | Specifies the FPGA image metadata, which must be a valid JavaScript Object Notation (JSON) object.                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                   |
   |                 |                 |                 | The number of characters in metadata after JSON serialization cannot exceed 1024.                                                                                                                 |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | String          | No              | Describes an FPGA image. The value consists of uppercase and lowercase letters, digits, hyphens (-), underscores (_), periods (.), commas, and spaces. The value consists of 0 to 255 characters. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

`Table 4 <#enustopic0065962597table551653634018>`__ describes the response parameters.



.. _ENUSTOPIC0065962597table551653634018:

.. table:: **Table 4** Response parameters

   ========== ====== ======================================
   Parameter  Type   Description
   ========== ====== ======================================
   fpga_image Object Indicates details about an FPGA image.
   ========== ====== ======================================



.. _ENUSTOPIC0065962597table8648200211311:

.. table:: **Table 5** **fpga_image** field description

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                 |
   +=======================+=======================+=============================================================================================+
   | id                    | String                | ID of an FPGA image                                                                         |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | status                | String                | Specifies the FPGA image status. Options:                                                   |
   |                       |                       |                                                                                             |
   |                       |                       | -  **saving**: indicates that the FPGA image file is being uploaded to the backend storage. |
   |                       |                       | -  **deleting**: indicates that the FPGA image is being deleted.                            |
   |                       |                       | -  **error**: indicates that creating the FPGA image failed.                                |
   |                       |                       | -  **active**: indicates that the FPGA image is available for use.                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v1/{project_id}/cloudservers/fpga_image

.. code-block::

   { 
     "fpga_image": { 
       "location": "obs-fpga:fpga.bin", 
       "name": "fpga-image-test", 
       "description": "fpga description", 
       "metadata": { 
         "shell_type": "OCL", 
         "shell_version": "1.0" 
       } 
     } 
   }

Example Response
----------------

.. code-block::

   {
     "fpga_image": {
       "status": "saving",
       "id": "4010a32c5c62bad9015c62dc2290002b"
     }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


