:original_name: en-us_topic_0108255889.html

.. _en-us_topic_0108255889:

Viewing Failed Tasks
====================

Scenarios
---------

You can view the details of failed task (if any) in the **Failures** area, including the task names and statuses. This section describes how to view failures.

Failure Types
-------------

:ref:`Table 1 <en-us_topic_0108255889__table155141127195016>` lists the types of failures that can be recorded in the **Failures** area.

.. _en-us_topic_0108255889__table155141127195016:

.. table:: **Table 1** Failure types

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Failure Type                      | Description                                                                                                                                                                                                                                                                                         |
   +===================================+=====================================================================================================================================================================================================================================================================================================+
   | Creation failures                 | A task failed. For a failed task, the system rolls back the task and displays an error code, for example, **Ecs.0013 Insufficient EIP quota**. For details about how to handle the failure, see :ref:`How Do I Handle Error Messages Displayed on the Management Console? <en-us_topic_0032398121>` |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation failures                | -  Modifying ECS specifications                                                                                                                                                                                                                                                                     |
   |                                   |                                                                                                                                                                                                                                                                                                     |
   |                                   |    If an ECS specifications modification failed, this operation is recorded in **Failures**.                                                                                                                                                                                                        |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, choose **Elastic Cloud Server**.

#. View **Failures** on the right side of common operations.


   .. figure:: /_static/images/en-us_image_0162732523.png
      :alt: **Figure 1** Failures

      **Figure 1** Failures

#. Click the number displayed in the **Failures** area to view task details.

   -  **Creation Failures**: show the failed ECS creation tasks.
   -  **Operation Failures**: show the tasks with failed operations and error codes, which help you troubleshoot the faults.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
