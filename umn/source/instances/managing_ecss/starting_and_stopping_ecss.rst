:original_name: en-us_topic_0013771110.html

.. _en-us_topic_0013771110:

Starting and Stopping ECSs
==========================

You can start, stop, restart, and delete ECSs.

-  To prevent load increase when starting or stopping a large number of ECSs at the same time, you are advised to select a small number of ECSs for each batch.
-  If an ECS remains in the **Restarting** or **Stopping** state for a long time, you can forcibly restart or stop it. In such a case, any unsaved data on the ECS will be lost. Therefore, exercise caution when forcibly restarting or stopping an ECS.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select your region and project.
#. Under **Computing**, select **Elastic Cloud Server**.
#. In the ECS list, select the target ECSs.
#. Above the list, click **Start**, **Stop**, or choose **More** > **Restart** or **Delete**.
#. In the displayed window, click **Yes**.

   .. note::

      Contact the administrator if an ECS has been in any of the following intermediate states for more than 30 minutes:

      -  Starting
      -  Stopping
      -  Restarting
      -  Forcibly restarting
      -  Deleting

.. |image1| image:: /_static/images/en-us_image_0210779229.png
