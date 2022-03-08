Login Overview
==============

Constraints
-----------

- Only a running ECS can be logged in.

- For ECSs created using public images, login usernames, passwords, and
  constraints vary depending on OSs running on the ECSs. For details, see
  `Public Images Introduction
  <https://docs.otc.t-systems.com/en-us/ims/index.html>`__.

Login Modes
-----------

Select a login mode as required and log in to the target ECS.



.. _EN-US_TOPIC_0013771089__table69409501234:

.. table:: **Table 1** Linux ECS login modes

   +--------+----------+------------------------------------------------------------------------------------+----------------------------------+
   | ECS OS | Local OS | Connection Method                                                                  | Requirement                      |
   +========+==========+====================================================================================+==================================+
   | Linux  | Windows  | Use a remote login tool, such as PuTTY or Xshell.                                  | The target ECS has an EIP bound. |
   |        |          |                                                                                    |                                  |
   |        |          | - Password-authenticated: `Logging In to the Linux ECS from a Local Windows Server |                                  |
   |        |          |   <en-us_topic_0017955633.html#EN-US_TOPIC_0017955633__section62068112020>`__      |                                  |
   |        |          | - Key-pair-authenticated: `Logging In to the Linux ECS from Local Windows          |                                  |
   |        |          |   <en-us_topic_0017955380.html#EN-US_TOPIC_0017955380__section47918167111724>`__   |                                  |
   +--------+----------+------------------------------------------------------------------------------------+----------------------------------+
   |        | Linux    | Run commands.                                                                      |                                  |
   |        |          |                                                                                    |                                  |
   |        |          | - Password-authenticated: `Logging In to the Linux ECS from a Local Linux Server   |                                  |
   |        |          |   <en-us_topic_0017955633.html#EN-US_TOPIC_0017955633__section20811823174313>`__   |                                  |
   |        |          | - Key-pair-authenticated: `Logging In to the Linux ECS from Local Linux            |                                  |
   |        |          |   <en-us_topic_0017955380.html#EN-US_TOPIC_0017955380__section3666784111724>`__    |                                  |
   +--------+----------+------------------------------------------------------------------------------------+----------------------------------+
   |        | Windows  | Use the remote login function available on the management console.                 | No EIP is required.              |
   |        |          |                                                                                    |                                  |
   |        |          | `Login Using VNC <en-us_topic_0093263550.html>`__                                  |                                  |
   +--------+----------+------------------------------------------------------------------------------------+----------------------------------+
