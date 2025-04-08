:original_name: en-us_topic_0035643949.html

.. _en-us_topic_0035643949:

Application Scenarios for Using Passwords
=========================================

Passwords are used to log in to ECSs. If you select the password login mode when creating an ECS, you can use the username and password to log in to your ECS. The password is very important. Keep it secure.

You can reset the password when:

-  You forgot the password.
-  The password has expired.
-  You selected **Set password later** during the ECS creation.

:ref:`Table 1 <en-us_topic_0035643949__table15251728124719>` provides guidance on how to reset your password in different scenarios.

.. _en-us_topic_0035643949__table15251728124719:

.. table:: **Table 1** Resetting a password

   +-------------------------------------------------------------------------------------------+----------------------------------------------------+
   | Scenario                                                                                  | Prerequisites                                      |
   +===========================================================================================+====================================================+
   | :ref:`Resetting the Password for Logging In to an ECS in the OS <en-us_topic_0122627689>` | N/A                                                |
   |                                                                                           |                                                    |
   |                                                                                           | .. note::                                          |
   |                                                                                           |                                                    |
   |                                                                                           |    The reference is for Windows or Linux ECSs.     |
   +-------------------------------------------------------------------------------------------+----------------------------------------------------+
   | :ref:`Resetting the Password for Logging In to a Windows ECS <en-us_topic_0021426802>`    | The password reset plug-in has not been installed. |
   +-------------------------------------------------------------------------------------------+----------------------------------------------------+
   | :ref:`Resetting the Password for Logging In to a Linux ECS <en-us_topic_0021427650>`      | The password reset plug-in has not been installed. |
   +-------------------------------------------------------------------------------------------+----------------------------------------------------+

Background
----------

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
