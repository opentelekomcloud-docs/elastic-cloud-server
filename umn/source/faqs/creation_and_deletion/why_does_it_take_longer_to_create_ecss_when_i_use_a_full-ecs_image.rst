:original_name: en-us_topic_0102391480.html

.. _en-us_topic_0102391480:

Why Does It Take Longer to Create ECSs When I Use a Full-ECS Image?
===================================================================

Symptom
-------

When you use a full-ECS image that was created using a CSBS backup to create ECSs, the process is time-consuming or the system displays a message indicating that the image cannot be used to rapidly create ECSs.

Cause Analysis
--------------

If your full-ECS image is in the old backup format provided by CSBS, this issue occurs.

.. note::

   -  CSBS has a new backup format. You can rapidly create ECSs if the full-ECS image is in this format
   -  This issue does not occur if a full-ECS image is created using a CBR backup.

Solution (Using CBR)
--------------------

If you want to use a full-ECS image to rapidly create ECSs, ensure that the full-ECS image is created using a CSBS backup in the new format. The procedure is as follows:

-  Scenario 1: The ECS based on which the target CSBS backup is created is available.

   In such a case, use the ECS to create a CBR backup and use this backup to create a full-ECS image. You can use this full-ECS image to rapidly create ECSs.

   -  For instructions about how to back up an ECS, see *Cloud Backup and Recovery User Guide*.
   -  For instructions about how create a full-ECS image, see *Image Management Service User Guide*.

-  Scenario 2: The ECS based on which the target CSBS backup is created is unavailable.

   #. Use the full-ECS image to create a new ECS.

   #. Use an ECS to create a CBR backup.

      For details, see *Cloud Backup and Recovery User Guide*.

   #. Use the CBR backup to create a full-ECS image.

      For details, see *Image Management Service User Guide*.

      You can use the full-ECS image to rapidly create ECSs.

Solution (Using CSBS)
---------------------

If you want to use a full-ECS image to rapidly create ECSs, ensure that the full-ECS image is created using a CSBS backup in the new format. The procedure is as follows:

-  Scenario 1: The ECS based on which the target CSBS backup is created is available.

   Back up the original ECS on the **Cloud Server Backup Service** page and use the new format to create a full-ECS image. You can use the full-ECS image to rapidly create ECSs.

   -  For instructions about how to back up an ECS, see *Cloud Server Backup Service User Guide*.
   -  For instructions about how create a full-ECS image, see *Image Management Service User Guide*.

-  Scenario 2: The ECS based on which the target CSBS backup is created is unavailable.

   #. Use the full-ECS image to create a new ECS.

   #. Back up the newly created ECS.

      For details, see *Cloud Server Backup Service User Guide*.

   #. Use the CSBS backup to create a full-ECS image.

      For details, see *Image Management Service User Guide*.

      You can use the full-ECS image to rapidly create ECSs.
