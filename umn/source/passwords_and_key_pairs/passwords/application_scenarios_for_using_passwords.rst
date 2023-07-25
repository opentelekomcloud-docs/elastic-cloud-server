:original_name: en-us_topic_0035643949.html

.. _en-us_topic_0035643949:

Application Scenarios for Using Passwords
=========================================

The password for logging in to your ECS is important and please keep it secure. You can reset the password if it is forgotten or expires.

:ref:`Table 1 <en-us_topic_0035643949__table15251728124719>` provides guidance on how to reset your password in different scenarios.

.. _en-us_topic_0035643949__table15251728124719:

.. table:: **Table 1** Resetting a password

   +----------------------------------------------------------------------------------------+----------------------------------------------------+
   | Reference                                                                              | Prerequisites                                      |
   +========================================================================================+====================================================+
   | :ref:`Changing the Login Password on an ECS <en-us_topic_0122627689>`                  | N/A                                                |
   |                                                                                        |                                                    |
   |                                                                                        | .. note::                                          |
   |                                                                                        |                                                    |
   |                                                                                        |    The reference is for Windows or Linux ECSs.     |
   +----------------------------------------------------------------------------------------+----------------------------------------------------+
   | :ref:`Resetting the Password for Logging In to a Windows ECS <en-us_topic_0021426802>` | The password reset plug-in has not been installed. |
   +----------------------------------------------------------------------------------------+----------------------------------------------------+
   | :ref:`Resetting the Password for Logging In to a Linux ECS <en-us_topic_0021427650>`   | The password reset plug-in has not been installed. |
   +----------------------------------------------------------------------------------------+----------------------------------------------------+

Background
----------

:ref:`Table 2 <en-us_topic_0035643949__en-us_topic_0021426802_table4381109318958>` shows the ECS password complexity requirements.

.. _en-us_topic_0035643949__en-us_topic_0021426802_table4381109318958:

.. table:: **Table 2** Password complexity requirements

   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | Parameter             | Requirement                                                                                                                                                  | Example Value                                                 |
   +=======================+==============================================================================================================================================================+===============================================================+
   | Password              | -  Consists of 8 to 26 characters.                                                                                                                           | YNbUwp!dUc9MClnv                                              |
   |                       | -  Contains at least three of the following character types:                                                                                                 |                                                               |
   |                       |                                                                                                                                                              | .. note::                                                     |
   |                       |    -  Uppercase letters                                                                                                                                      |                                                               |
   |                       |    -  Lowercase letters                                                                                                                                      |    The example password is generated randomly. Do not use it. |
   |                       |    -  Digits                                                                                                                                                 |                                                               |
   |                       |    -  Special characters: ``$!@%-_=+[]:./^,{}?``                                                                                                             |                                                               |
   |                       |                                                                                                                                                              |                                                               |
   |                       | -  Cannot contain the username or the username spelled backwards.                                                                                            |                                                               |
   |                       | -  Cannot contain more than two consecutive characters in the same sequence as they appear in the username. (This requirement applies only to Windows ECSs.) |                                                               |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
