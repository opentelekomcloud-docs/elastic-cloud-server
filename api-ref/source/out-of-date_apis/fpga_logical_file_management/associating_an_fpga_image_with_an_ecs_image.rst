:original_name: en-us_topic_0065962598.html

.. _en-us_topic_0065962598:

Associating an FPGA Image with an ECS Image
===========================================

Function
--------

This API is used to create a mapping between an FPGA image and an ECS image.

URI
---

POST /v1/{project_id}/cloudservers/fpga_image/{fpga_image_id}/association

:ref:`Table 1 <en-us_topic_0065962598__table28107133211632>` describes the parameters in the URI.

.. _en-us_topic_0065962598__table28107133211632:

.. table:: **Table 1** Parameter description

   ============= ========= ============================
   Parameter     Mandatory Description
   ============= ========= ============================
   project_id    Yes       Specifies the project ID.
   fpga_image_id Yes       Specifies the FPGA image ID.
   ============= ========= ============================

Request
-------

:ref:`Table 2 <en-us_topic_0065962598__table41782128362>` describes the request parameters.

.. _en-us_topic_0065962598__table41782128362:

.. table:: **Table 2** Request parameters

   ========= ====== ========= ========================
   Parameter Type   Mandatory Description
   ========= ====== ========= ========================
   image     Object Yes       Specifies the ECS image.
   ========= ====== ========= ========================

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
