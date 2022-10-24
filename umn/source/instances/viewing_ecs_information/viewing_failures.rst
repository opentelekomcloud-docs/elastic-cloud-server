:original_name: en-us_topic_0108255889.html

.. _en-us_topic_0108255889:

Viewing Failures
================

Scenarios
---------

The **Failures** area shows the tasks that failed due to an error, including the task name and status. **Failures** is displayed on the management console if a task failed. This section describes how to view failures.

Failure Types
-------------

:ref:`Table 1 <en-us_topic_0108255889__table155141127195016>` lists the types of failures that can be recorded in the **Failures** area.

.. _en-us_topic_0108255889__table155141127195016:

.. table:: **Table 1** Failure types

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Failure Type                      | Description                                                                                                                                                                                                                                                        |
   +===================================+====================================================================================================================================================================================================================================================================+
   | Creation failures                 | A task failed. For a failed task, the system rolls back and displays an error code, for example, **Ecs.0013 Insufficient EIP quota**. See :ref:`How Do I Handle Error Messages Displayed on the Management Console? <en-us_topic_0032398121>` for troubleshooting. |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation failures                | -  Modifying ECS specifications                                                                                                                                                                                                                                    |
   |                                   |                                                                                                                                                                                                                                                                    |
   |                                   |    If an ECS specifications modification failed, this operation is recorded in **Failures**.                                                                                                                                                                       |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. View **Failures** on the right side of common operations.


   .. figure:: /_static/images/en-us_image_0152768827.png
      :alt: **Figure 1** Failures

      **Figure 1** Failures

#. Click the number displayed in the **Failures** area to view details about the tasks.

   -  **Creation Failures**: show the tasks that are being created and those failed to create.
   -  **Operation Failures**: show the tasks with errors, including the operations performed on the tasks and error codes. Such information can be used for rapid fault locating.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
