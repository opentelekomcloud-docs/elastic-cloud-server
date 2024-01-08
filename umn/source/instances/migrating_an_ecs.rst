:original_name: en-us_topic_0133365988.html

.. _en-us_topic_0133365988:

Migrating an ECS
================

Scenarios
---------

ECSs can be migrated:

-  Between Dedicated Hosts (DeHs)
-  From a DeH to a public resource pool
-  From a public resource pool to a DeH

This section describes how to migrate ECSs from a public resource pool to a DeH.

.. note::

   -  Before migrating an ECS, ensure that there are available DeH resources.

   -  For details about migrating ECSs from a DeH to another DeH or to a public resource pool, see "Migrating ECSs" in the *Dedicated Host User Guide*.

Constraints
-----------

-  Only stopped ECSs can be migrated.
-  To ensure that the migration is successful, there must be an available DeH.
-  CBR and CSBS backups are not affected by migrations.
-  ECS IDs remain unchanged after a migration.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select your region and project.
#. Under **Computing**, click **Elastic Cloud Server**.
#. Locate the row that contains the target ECS and choose **More** > **Migrate ECS** in the **Operation** column.
#. In the displayed dialog box, select the target DeH.

   .. note::

      If no DeHs are available, create a DeH first. For details, see Allocating DeHs in the *Dedicated Host User Guide*.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
