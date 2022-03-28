Associating an FPGA Image with an ECS Image
===========================================

Function
--------

This API is used to create a mapping between an FPGA image and an ECS image.

URI
---

POST /v1/{project_id}/cloudservers/fpga_image/{fpga_image_id}/association

`Table 1 <#enustopic0065962598table28107133211632>`__ describes the parameters in the URI.



.. _ENUSTOPIC0065962598table28107133211632:

.. table:: **Table 1** Parameter description

   ============= ========= ============================
   Parameter     Mandatory Description
   ============= ========= ============================
   project_id    Yes       Specifies the project ID.
   fpga_image_id Yes       Specifies the FPGA image ID.
   ============= ========= ============================

Request
-------

`Table 2 <#enustopic0065962598table41782128362>`__ describes the request parameters. 

.. _ENUSTOPIC0065962598table41782128362:

.. table:: **Table 2** Request parameters

   ========= ====== ========= ========================
   Parameter Type   Mandatory Description
   ========= ====== ========= ========================
   image     Object Yes       Specifies the ECS image.
   ========= ====== ========= ========================



.. _ENUSTOPIC0065962598table39016918211632:

.. table:: **Table 3** **image** field description

   ========= ====== ========= ===========================
   Parameter Type   Mandatory Description
   ========= ====== ========= ===========================
   id        String Yes       Specifies the ECS image ID.
   ========= ====== ========= ===========================

Response
--------

None

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v1/{project_id}/cloudservers/fpga_image/{fpga_image_id}/association

.. code-block::

   {
     "image": {
       "id": "18efee75-e058-4c52-a49c-9e3ba4d1c8de"
     }
   }

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


