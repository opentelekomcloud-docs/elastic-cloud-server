:original_name: en-us_topic_0039588795.html

.. _en-us_topic_0039588795:

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

#. After creating an ECS, view the creation status above the ECS list beside the common operations (**Start**, **Stop**, **Restart**, and **Delete**).


   .. figure:: /_static/images/en-us_image_0000001705420301.png
      :alt: **Figure 1** ECS creation status

      **Figure 1** ECS creation status

#. Click the number displayed above **Creating** and view task details.

   .. note::

      -  An ECS that is being created is in one of the following states:

         -  **Creating**: The ECS is being created.

         -  **Faulty**: Creating the ECS failed. In such a case, the system automatically rolls back the task and displays an error code on the GUI, for example, **Ecs.0013 Insufficient EIP quota**.

         -  **Running**: The request of creating the ECS has been processed, and the ECS is running properly. An ECS in this state can provide services for you.

            See :ref:`How Do I Handle Error Messages Displayed on the Management Console? <en-us_topic_0032398121>` for troubleshooting.

      -  If you find that the task status area shows an ECS creation failure but the ECS has been created successfully and displayed in the ECS list, see :ref:`Why Does the Failures Area Show an ECS Creation Failure But the ECS List Displays the Created ECS? <en-us_topic_0039524582>`

.. |image1| image:: /_static/images/en-us_image_0210779229.png
