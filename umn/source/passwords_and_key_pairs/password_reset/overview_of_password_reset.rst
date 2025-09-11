:original_name: en-us_topic_0035643949.html

.. _en-us_topic_0035643949:

Overview of Password Reset
==========================

What Is a Password?
-------------------

Passwords are used to log in to ECSs. If you select the password login mode when creating an ECS, you can use the username and password to log in to the ECS. The password is very important. Keep it secure.

You can set a password when creating an ECS. If you do not set a password during the creation or if the password is lost or expired, you can reset the password.

You can reset the password in any of the following scenarios:

-  The password is lost.
-  The password has expired.
-  You intend to change the initial password at the first login.
-  You selected **Set password later** or **Key pair** for **Login Mode** during ECS creation.

Password Reset Scenarios
------------------------

:ref:`Table 1 <en-us_topic_0035643949__table15251728124719>` describes the methods of resetting passwords for ECSs.

.. _en-us_topic_0035643949__table15251728124719:

.. table:: **Table 1** Password reset methods

   +----------------------------------------------------------------------------------------+----------------------------------------------------+
   | Scenario                                                                               | Prerequisites                                      |
   +========================================================================================+====================================================+
   | :ref:`Resetting the Password in the ECS OS <en-us_topic_0122627689>`                   | N/A                                                |
   |                                                                                        |                                                    |
   |                                                                                        | .. note::                                          |
   |                                                                                        |                                                    |
   |                                                                                        |    The reference is for Windows or Linux ECSs.     |
   +----------------------------------------------------------------------------------------+----------------------------------------------------+
   | :ref:`Resetting the Password for Logging In to a Windows ECS <en-us_topic_0021426802>` | The password reset plug-in has not been installed. |
   +----------------------------------------------------------------------------------------+----------------------------------------------------+
   | :ref:`Resetting the Password for Logging In to a Linux ECS <en-us_topic_0021427650>`   | The password reset plug-in has not been installed. |
   +----------------------------------------------------------------------------------------+----------------------------------------------------+

Password Complexity Requirements
--------------------------------

:ref:`Table 2 <en-us_topic_0035643949__en-us_topic_0021426802_table4381109318958>` shows the ECS password complexity requirements.

.. _en-us_topic_0035643949__en-us_topic_0021426802_table4381109318958:

.. table:: **Table 2** Password complexity requirements

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Requirement                                                                                                                                                  |
   +===================================+==============================================================================================================================================================+
   | Password                          | -  Consists of 8 to 26 characters.                                                                                                                           |
   |                                   | -  Contains at least three of the following character types:                                                                                                 |
   |                                   |                                                                                                                                                              |
   |                                   |    -  Uppercase letters                                                                                                                                      |
   |                                   |    -  Lowercase letters                                                                                                                                      |
   |                                   |    -  Digits                                                                                                                                                 |
   |                                   |    -  Special characters: ``$!@%-_=+[]:./^,{}?``                                                                                                             |
   |                                   |                                                                                                                                                              |
   |                                   | -  Cannot contain the username or the username spelled backwards.                                                                                            |
   |                                   | -  Cannot contain more than two consecutive characters in the same sequence as they appear in the username. (This requirement applies only to Windows ECSs.) |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
