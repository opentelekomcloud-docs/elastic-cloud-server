Releasing a Floating IP Address (Discarded)
===========================================

Function
--------

This API is used to release a floating IP address.

This API has been discarded. Use the API described in "Deleting a Floating IP Address".

URI
---

DELETE /v2/{project_id}/os-floating-ips/{floating_ip_id}

DELETE /v2.1/{project_id}/os-floating-ips/{floating_ip_id}

`Table 1 <#enustopic0065820819enustopic0057972674table32475667>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065820819enustopic0057972674table32475667:

.. table:: **Table 1** Parameter description

   ============== ========= ============================================
   Parameter      Mandatory Description
   ============== ========= ============================================
   project_id     Yes       Specifies the project ID.
   floating_ip_id Yes       Specifies the ID of the floating IP address.
   ============== ========= ============================================

Request
-------

None

Response
--------

None

Example Request
---------------

.. code-block::

   DELETE https://{endpoint}/v2/e73621affb8f44e1bc01898747ca09d4/os-floating-ips/05f71f43-f3c9-47ef-ac8d-9f02aef66418
   DELETE https://{endpoint}/v2.1/e73621affb8f44e1bc01898747ca09d4/os-floating-ips/05f71f43-f3c9-47ef-ac8d-9f02aef66418

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


