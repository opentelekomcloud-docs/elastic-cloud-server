:original_name: en-us_topic_0065817694.html

.. _en-us_topic_0065817694:

Creating an Image Using an ECS
==============================

Function
--------

This API is used to create an image using an ECS. After the creation, you can use this image to create ECSs.

Images created using an ECS are stored on storage nodes as snapshots.

.. note::

   This API is a native OpenStack API that is not applicable to the images on the public cloud platform.

   -  To create a system disk image or data disk image, use the IMS API (**POST /v2/cloudimages/action**). For details, see "Creating an Image" in *Image Management Service API Reference*.
   -  To create a full-ECS image, use the IMS API (**POST /v1/cloudimages/wholeimages/action**). For details, see "Creating a Full-ECS Image" in *Image Management Service API Reference*.

Constraints
-----------

#. An ECS in the error state cannot be used to create an image.
#. If an image created using an ECS is used to create a new ECS, the new ECS must be located in the same AZ as the original ECS.
#. After an ECS is deleted, the images and snapshots created using this ECS will not be automatically deleted. You must manually delete them.
#. After an image created using an ECS is deleted, the associated snapshots will not be automatically deleted (this function is implemented by native OpenStack). You must manually delete such snapshots.
#. The image created using an ECS cannot be used to create data disks.
#. The images created using the API described in this section (URI: POST /v2/{project_id}/servers/{server_id}/action or POST /v2.1/{project_id}/servers/{server_id}/action) cannot be exported to OBS buckets. If such images must be exported, use the IMS API (**POST /v2/cloudimages/action**). For details, see "Creating an Image" in *Image Management Service API Reference*.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

:ref:`Table 1 <en-us_topic_0065817694__table9179610161220>` describes the parameters in the URI.

.. _en-us_topic_0065817694__table9179610161220:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0065817694__table3529164221216>` describes the request parameters.

.. _en-us_topic_0065817694__table3529164221216:

.. table:: **Table 2** Request parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                            |
   +=============+===========+========+========================================================================================================================================+
   | createImage | Yes       | Object | Specifies the image created using ECS. For details, see :ref:`Table 3 <en-us_topic_0065817694__en-us_topic_0057972976_table47198018>`. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817694__en-us_topic_0057972976_table47198018:

.. table:: **Table 3** **createImage** field description

   +-----------+-----------+--------+-------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                               |
   +===========+===========+========+===========================================================================================+
   | name      | Yes       | String | Specifies the image name with a length greater than 0 bytes and less than 243 bytes.      |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------+
   | metadata  | No        | Object | Specifies the image attribute with a length greater than 0 bytes and less than 255 bytes. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------+

Response
--------

+-----------------+-----------------+-----------------+--------------------------------------------------------------------------------+
| Parameter       | Mandatory       | Type            | Description                                                                    |
+=================+=================+=================+================================================================================+
| Location        | Yes             | String          | Specifies the local URL of the image, which is returned in the request header. |
|                 |                 |                 |                                                                                |
|                 |                 |                 | This parameter is not supported in microversion 2.44 and later.                |
+-----------------+-----------------+-----------------+--------------------------------------------------------------------------------+
| image_id        | Yes             | String          | Specifies the image UUID.                                                      |
|                 |                 |                 |                                                                                |
|                 |                 |                 | This parameter is supported in microversion 2.45 and later.                    |
+-----------------+-----------------+-----------------+--------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/servers/{server_id}/action
   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

.. code-block::

   {
      "createImage" : {
           "name" : "new-image-name",
           "metadata": {
               "ImageType": "Gold",
               "ImageVersion": "2.0"
           }
       }
   }

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
