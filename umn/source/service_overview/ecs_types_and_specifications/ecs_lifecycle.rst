:original_name: en-us_topic_0140323150.html

.. _en-us_topic_0140323150:

ECS Lifecycle
=============

The ECS lifecycle refers to the entire journey an ECS goes through, from creation to deletion (or release).

.. table:: **Table 1** ECS statuses

   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Status                  | Status Attribute      | Description                                                                                                        |
   +=========================+=======================+====================================================================================================================+
   | Creating                | Intermediate          | The ECS creation has been requested and the ECS is preparing to enter the **Running** state.                       |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Starting                | Intermediate          | The ECS is between the **Stopped** and **Running** state.                                                          |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Running                 | Stable                | The ECS is running properly.                                                                                       |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Stopping                | Intermediate          | The ECS is being stopped.                                                                                          |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Stopped                 | Stable                | The ECS has been stopped.                                                                                          |
   |                         |                       |                                                                                                                    |
   |                         |                       | ECSs in this state cannot provide services.                                                                        |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Restarting              | Intermediate          | The ECS is being restarted.                                                                                        |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Resizing                | Intermediate          | The ECS has received a resizing request and has started to resize.                                                 |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Verifying resizing      | Intermediate          | The ECS is verifying the new specifications.                                                                       |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Deleting                | Intermediate          | The ECS is being deleted.                                                                                          |
   |                         |                       |                                                                                                                    |
   |                         |                       | If the ECS remains in this state for a long time, exceptions may occur. In such a case, contact technical support. |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Deleted                 | Intermediate          | The ECS has been deleted. ECSs in this state cannot provide services and will be removed from the system.          |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Faulty                  | Stable                | The ECS is faulty.                                                                                                 |
   |                         |                       |                                                                                                                    |
   |                         |                       | ECSs in this state cannot provide services. Contact technical support.                                             |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Reinstalling            | Intermediate          | The ECS has received a request to reinstall the OS and is currently undergoing the OS reinstallation process.      |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Reinstallation failed   | Stable                | The ECS has received a request to reinstall the OS, but due to exceptions, the reinstallation failed.              |
   |                         |                       |                                                                                                                    |
   |                         |                       | ECSs in this state cannot provide services. Contact technical support.                                             |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Changing OS             | Intermediate          | The ECS has received a request to change the OS and is currently undergoing the OS change process.                 |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Failed to change the OS | Stable                | The ECS has received a request to change the OS, but due to exceptions, the change failed.                         |
   |                         |                       |                                                                                                                    |
   |                         |                       | ECSs in this state cannot provide services. Contact technical support.                                             |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Forcibly restarting     | Intermediate          | The ECS is being forcibly restarted.                                                                               |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Reverting resizing      | Intermediate          | The ECS is rolling back a resizing operation.                                                                      |
   +-------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
