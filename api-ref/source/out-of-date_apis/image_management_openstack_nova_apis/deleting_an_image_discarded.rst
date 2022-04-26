:original_name: en-us_topic_0065817699.html

.. _en-us_topic_0065817699:

Deleting an Image (Discarded)
=============================

Function
--------

This API is used to delete a specified image. The image cannot be restored after being deleted.

This API has been discarded. Use the API described in "Deleting an Image (Native OpenStack API)".

URI
---

DELETE /v2/{project_id}/images/{image_id}

DELETE /v2.1/{project_id}/images/{image_id}

:ref:`Table 1 <en-us_topic_0065817699__table148747347424>` describes the parameters in the URI.

.. _en-us_topic_0065817699__table148747347424:

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

None

Example Request
---------------

.. code-block::

   DELETE https://{endpoint}/v2/9c53a566cb3443ab910cf0daebca90c4/images/6cad483b-e281-4985-a345-7afef1f3c5b7
   DELETE https://{endpoint}/v2.1/9c53a566cb3443ab910cf0daebca90c4/images/6cad483b-e281-4985-a345-7afef1f3c5b7

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
