.. _en-us_topic_0133365988:

Migrating an ECS
================



.. _en-us_topic_0133365988__section17761164816565:

Scenarios
---------

ECSs can be migrated between DeHs and public resource pools.

-  An ECS created on a DeH can be migrated to another DeH.
-  An ECS created on a DeH can be migrated to a public resource pool.
-  An ECS deployed in a public resource pool can be migrated to a DeH.



.. _en-us_topic_0133365988__section1213835718599:

Notes
-----

-  Only a stopped ECS can be migrated.
-  CBR and CSBS backups are not affected by cold migrations.
-  ECS IDs remain unchanged after a cold migration.



.. _en-us_topic_0133365988__section12638144614015:

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the **Elastic Cloud Server** page, select the target ECS.

#. Click **Migrate ECS** in the **Operation** column.

#. In the **Migrate ECS** dialog box, migrate the ECS as prompted.

   -  If you want to migrate the ECS to a DeH, select a DeH from the list.
   -  If you want to migrate the ECS to another DeH, select **Migrated** **To another DeH**.
   -  If you want to migrate the ECS from a DeH to a public resource pool, select **Migrated** **Out of DeH**.

#. Click **OK**.

   The ECS is migrated as required.

.. |image1| image:: /_static/images/en-us_image_0210779229.png

