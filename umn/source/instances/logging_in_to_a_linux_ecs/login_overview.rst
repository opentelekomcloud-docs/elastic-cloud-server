.. _en-us_topic_0013771089:

Login Overview
==============



.. _en-us_topic_0013771089__section15584113212291:

Constraints
-----------

-  Only a running ECS can be logged in.
-  For ECSs created using public images, login usernames, passwords, and constraints vary depending on OSs running on the ECSs. For details, see `Public Images Introduction <https://docs.otc.t-systems.com/en-us/ims/index.html>`__.



.. _en-us_topic_0013771089__section95820318444:

Login Modes
-----------

Select a login mode as required and log in to the target ECS.



.. _en-us_topic_0013771089__table69409501234:

.. table:: **Table 1** Linux ECS login modes

   +-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
   | ECS OS          | Local OS        | Connection Method                                                                                                                       | Requirement                      |
   +=================+=================+=========================================================================================================================================+==================================+
   | Linux           | Windows         | Use a remote login tool, such as PuTTY or Xshell.                                                                                       | The target ECS has an EIP bound. |
   |                 |                 |                                                                                                                                         |                                  |
   |                 |                 | -  Password-authenticated: :ref:`Logging In to the Linux ECS from a Local Windows Server <en-us_topic_0017955633__section62068112020>`  |                                  |
   |                 |                 | -  Key-pair-authenticated: :ref:`Logging In to the Linux ECS from Local Windows <en-us_topic_0017955380__section47918167111724>`        |                                  |
   +-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
   |                 | Linux           | Run commands.                                                                                                                           |                                  |
   |                 |                 |                                                                                                                                         |                                  |
   |                 |                 | -  Password-authenticated: :ref:`Logging In to the Linux ECS from a Local Linux Server <en-us_topic_0017955633__section20811823174313>` |                                  |
   |                 |                 | -  Key-pair-authenticated: :ref:`Logging In to the Linux ECS from Local Linux <en-us_topic_0017955380__section3666784111724>`           |                                  |
   +-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
   |                 | Windows         | Use the remote login function available on the management console.                                                                      | No EIP is required.              |
   |                 |                 |                                                                                                                                         |                                  |
   |                 |                 | :ref:`Login Using VNC <en-us_topic_0093263550>`                                                                                         |                                  |
   +-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
