Viewing Failures
================

Scenarios
---------

The **Failures** area shows the tasks that failed to process due to an error, including the task name and status. **Failures** is displayed on the management console if a task failed. This section describes how to view failures.

Failure Types
-------------

`Table 1 <#enustopic0108255889table155141127195016>`__ lists the types of failures that can be recorded in the **Failures** area.



.. _ENUSTOPIC0108255889table155141127195016:

.. table:: **Table 1** Failure types

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Failure Type                      | Description                                                                                                                                                                                                                                                                                                                                           |
   +===================================+=======================================================================================================================================================================================================================================================================================================================================================+
   | Creation failures                 | A task failed to process. For a failed task, the system rolls back and displays an error code, for example, **Ecs.0013 Insufficient EIP quota**. See `How Do I Handle Error Messages Displayed on the Management Console? <../../faqs/ecs_management/how_do_i_handle_error_messages_displayed_on_the_management_console.html>`__ for troubleshooting. |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation failures                | -  Modifying ECS specifications                                                                                                                                                                                                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                                                                                                                       |
   |                                   |    If an ECS specifications modification failed, this operation is recorded in **Failures**.                                                                                                                                                                                                                                                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. View **Failures** on the right side of common operations.

   .. figure:: /_static/images/en-us_image_0152768827.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 1** Failures

#. Click the number displayed in the **Failures** area to view details about the tasks.

   -  **Creation Failures**: show the tasks that are being created and those failed to create.
   -  **Operation Failures**: show the tasks with errors, including the operations performed on the tasks and error codes. Such information can be used for rapid fault locating.



.. |image1| image:: /_static/images/en-us_image_0210779229.png

