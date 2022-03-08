Viewing ECS Creation Statuses
=============================

Scenarios
---------

After submitting the request for creating an ECS, you can view the creation status. This section describes how to view the creation status of an ECS.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select your region and project.
#. Under **Computing**, click **Elastic Cloud Server**.
#. After creating an ECS, view the creation status in the task status area on the right side of common operations (**Start**, **Stop**, and **More**).
#. Click the number displayed above **Creating** and view details about the tasks.\ |image2|

   -  An ECS that is being created is in one of the following states:

      -  **Creating**: The ECS is being created.

      -  **Failures**: Creating the ECS failed. In such a case, the system automatically rolls the task back and displays an error code on the GUI, for example, **Ecs.0013 Insufficient EIP quota**.

      -  **Running**: The request of creating the ECS has been processed, and the ECS is running properly. An ECS in this state can provide services for you.

         See `How Do I Handle Error Messages Displayed on the Management Console? <en-us_topic_0032398121.html>`__ for troubleshooting.

   -  If you find that the task status area shows an ECS creation failure but the ECS list displays the created ECS, see `Why Does the Failures Area Show an ECS Creation Failure But the ECS List Displays the Created ECS? <en-us_topic_0039524582.html>`__


.. |image1| image:: /_static/images/en-us_image_0210779229.png

.. |image2| image:: /_static/images/note_3.0-en-us.png
