Deleting an FPGA Image
======================

Function
--------

This API is used to delete an FPGA image.

URI
---

DELETE /v1/{project_id}/cloudservers/fpga_image/{fpga_image_id}

`Table 1 <#enustopic0065962599table44329634211725>`__ describes the parameters in the URI.



.. _ENUSTOPIC0065962599table44329634211725:

.. table:: **Table 1** Parameter description

   ============= ========= ============================
   Parameter     Mandatory Description
   ============= ========= ============================
   project_id    Yes       Specifies the project ID.
   fpga_image_id Yes       Specifies the FPGA image ID.
   ============= ========= ============================

Request
-------

None

Response
--------

None

Example Request
---------------

.. code-block::

   DELETE https://{endpoint}/v1/{project_id}/cloudservers/fpga_image/{fpga_image_id}

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.

