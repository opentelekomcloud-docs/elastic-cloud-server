Login Overview
==============

Constraints
-----------

-  Only a running ECS can be logged in.
-  For ECSs created using public images, login usernames, passwords, and constraints vary depending on OSs running on the ECSs. For details, see `Public Images Introduction <https://docs.otc.t-systems.com/en-us/ims/index.html>`__.

Login Modes
-----------

Select a login mode as required and log in to the target ECS.



.. _ENUSTOPIC0013771089table69409501234:

.. table:: **Table 1** Linux ECS login modes

   +-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
   | ECS OS          | Local OS        | Connection Method                                                                                                                                                                                                           | Requirement                      |
   +=================+=================+=============================================================================================================================================================================================================================+==================================+
   | Linux           | Windows         | Use a remote login tool, such as PuTTY or Xshell.                                                                                                                                                                           | The target ECS has an EIP bound. |
   |                 |                 |                                                                                                                                                                                                                             |                                  |
   |                 |                 | -  Password-authenticated: `Logging In to the Linux ECS from a Local Windows Server <../../instances/logging_in_to_a_linux_ecs/login_using_an_ssh_password.html#logging-in-to-the-linux-ecs-from-a-local-windows-server>`__ |                                  |
   |                 |                 | -  Key-pair-authenticated: `Logging In to the Linux ECS from Local Windows <../../instances/logging_in_to_a_linux_ecs/login_using_an_ssh_key.html#logging-in-to-the-linux-ecs-from-local-windows>`__                        |                                  |
   +-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
   |                 | Linux           | Run commands.                                                                                                                                                                                                               |                                  |
   |                 |                 |                                                                                                                                                                                                                             |                                  |
   |                 |                 | -  Password-authenticated: `Logging In to the Linux ECS from a Local Linux Server <../../instances/logging_in_to_a_linux_ecs/login_using_an_ssh_password.html#logging-in-to-the-linux-ecs-from-a-local-linux-server>`__     |                                  |
   |                 |                 | -  Key-pair-authenticated: `Logging In to the Linux ECS from Local Linux <../../instances/logging_in_to_a_linux_ecs/login_using_an_ssh_key.html#logging-in-to-the-linux-ecs-from-local-linux>`__                            |                                  |
   +-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
   |                 | Windows         | Use the remote login function available on the management console.                                                                                                                                                          | No EIP is required.              |
   |                 |                 |                                                                                                                                                                                                                             |                                  |
   |                 |                 | `Login Using VNC <../../instances/logging_in_to_a_linux_ecs/login_using_vnc.html>`__                                                                                                                                        |                                  |
   +-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+


