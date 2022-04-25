:original_name: en-us_topic_0065962599.html

.. _en-us_topic_0065962599:

Deleting an FPGA Image
======================

Function
--------

This API is used to delete an FPGA image.

URI
---

DELETE /v1/{project_id}/cloudservers/fpga_image/{fpga_image_id}

:ref:`Table 1 <en-us_topic_0065962599__table44329634211725>` describes the parameters in the URI.

.. _en-us_topic_0065962599__table44329634211725:

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
