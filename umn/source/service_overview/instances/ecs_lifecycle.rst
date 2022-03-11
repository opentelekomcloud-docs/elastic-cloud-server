ECS Lifecycle
=============

The ECS lifecycle refers to the entire journey an ECS goes through, from creation to deletion (or release).



.. _EN-US_TOPIC_0140323150__table198821178160:

.. table:: **Table 1** ECS statuses

   +------------------------+------------------+---------------------------------------+
   | Status                 | Status Attribute | Description                           |
   +========================+==================+=======================================+
   | Creating               | Intermediate     | The ECS is being created but has not  |
   |                        |                  | been running.                         |
   +------------------------+------------------+---------------------------------------+
   | Starting               | Intermediate     | The ECS is between the **Stopped**    |
   |                        |                  | and **Running** states.               |
   +------------------------+------------------+---------------------------------------+
   | Running                | Stable           | The ECS is running properly.          |
   +------------------------+------------------+---------------------------------------+
   | Stopping               | Intermediate     | The ECS is between the **Running**    |
   |                        |                  | and **Stopped** states.               |
   +------------------------+------------------+---------------------------------------+
   | Stopped                | Stable           | The ECS has been properly stopped.    |
   +------------------------+------------------+---------------------------------------+
   | Restarting             | Intermediate     | The ECS is being restarted.           |
   +------------------------+------------------+---------------------------------------+
   | Resizing               | Intermediate     | The ECS has received a resizing       |
   |                        |                  | request and has started to resize.    |
   +------------------------+------------------+---------------------------------------+
   | Verifying resizing     | Intermediate     | The ECS is verifying the modified     |
   |                        |                  | configuration.                        |
   +------------------------+------------------+---------------------------------------+
   | Deleting               | Intermediate     | The ECS is being deleted.             |
   |                        |                  |                                       |
   |                        |                  | If the ECS remains in this state for  |
   |                        |                  | a long time, exceptions may have      |
   |                        |                  | occurred. In such a case, contact the |
   |                        |                  | administrator.                        |
   +------------------------+------------------+---------------------------------------+
   | Deleted                | Intermediate     | The ECS has been deleted. An ECS in   |
   |                        |                  | this state cannot provide services    |
   |                        |                  | and will be promptly cleared from the |
   |                        |                  | system.                               |
   +------------------------+------------------+---------------------------------------+
   | Faulty                 | Stable           | An exception has occurred on the ECS. |
   |                        |                  | Contact the administrator.            |
   +------------------------+------------------+---------------------------------------+
   | Reinstalling OS        | Intermediate     | The ECS has received a request to     |
   |                        |                  | reinstall the OS and has begun the    |
   |                        |                  | reinstallation.                       |
   +------------------------+------------------+---------------------------------------+
   | Reinstalling OS failed | Stable           | The ECS received a request to         |
   |                        |                  | reinstall the OS, but due to          |
   |                        |                  | exceptions, the reinstallation        |
   |                        |                  | failed. Contact the administrator.    |
   +------------------------+------------------+---------------------------------------+
   | Changing OS            | Intermediate     | The ECS received a request to change  |
   |                        |                  | the OS and has begun implementing the |
   |                        |                  | changes.                              |
   +------------------------+------------------+---------------------------------------+
   | OS change failed       | Stable           | The ECS has received a request to     |
   |                        |                  | change the OS, but due to exceptions, |
   |                        |                  | the change failed to be implemented.  |
   |                        |                  | Contact the administrator.            |
   +------------------------+------------------+---------------------------------------+
   | Forcibly restarting    | Intermediate     | The ECS is being forcibly restarted.  |
   +------------------------+------------------+---------------------------------------+
   | Rolling back resizing  | Intermediate     | The ECS is rolling back a resizing    |
   |                        |                  | operation.                            |
   +------------------------+------------------+---------------------------------------+

