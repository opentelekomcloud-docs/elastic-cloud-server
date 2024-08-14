:original_name: en-us_topic_0013771110.html

.. _en-us_topic_0013771110:

Starting and Stopping ECSs
==========================

You can start, stop, restart, or delete the ECS.

-  To prevent a sudden load increase, you are advised to start or stop a small number of ECSs at a time.
-  If an ECS remains in the **Restarting** or **Stopping** state for a long time, you can forcibly restart or stop it. In such a case, any unsaved data on the ECS will be lost. Therefore, exercise caution when forcibly restarting or stopping an ECS.

Starting ECSs
-------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select your region and project.
#. Under **Computing**, select **Elastic Cloud Server**.
#. In the ECS list, select the target ECSs.
#. Click **Start** in the upper left corner of the list.
#. In the displayed window, click **Yes**.

   .. note::

      Contact the administrator if the ECS has been in the **Starting** state for more than 30 minutes.

Stopping ECSs
-------------

#. Log in to the management console.
#. Click |image2| in the upper left corner and select your region and project.
#. Under **Computing**, select **Elastic Cloud Server**.
#. In the ECS list, select the target ECSs.
#. Click **Stop** in the upper left corner of the list.
#. In the displayed dialog box, select **Forcibly stop the preceding ECSs** based on your service requirements.

   .. important::

      After an ECS is forcibly stopped, unsaved data on the ECS will be lost.

#. Click **Yes** to stop the ECSs.

   .. note::

      Contact the administrator if the ECS has been in the **Stopping** state for more than 30 minutes.

Restarting ECSs
---------------

#. Log in to the management console.
#. Click |image3| in the upper left corner and select your region and project.
#. Under **Computing**, select **Elastic Cloud Server**.
#. In the ECS list, select the target ECSs.
#. Click **Restart** in the upper left corner of the list.

   .. important::

      After an ECS is forcibly restarted, unsaved data on the ECS will be lost.

#. Click **Yes** to stop the ECSs.

   .. note::

      Contact the administrator if the ECS has been in the **Restarting** state for more than 30 minutes.

Deleting an ECS
---------------

#. Log in to the management console.
#. Click |image4| in the upper left corner and select your region and project.
#. Under **Computing**, select **Elastic Cloud Server**.
#. In the ECS list, select the target ECSs.
#. Click **Delete** in the upper left corner of the list.

   .. note::

      Contact the administrator if the ECS has been in the **Deleting** state for more than 30 minutes.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
.. |image2| image:: /_static/images/en-us_image_0210779229.png
.. |image3| image:: /_static/images/en-us_image_0210779229.png
.. |image4| image:: /_static/images/en-us_image_0210779229.png
