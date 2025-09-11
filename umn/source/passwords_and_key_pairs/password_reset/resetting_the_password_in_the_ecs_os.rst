:original_name: en-us_topic_0122627689.html

.. _en-us_topic_0122627689:

Resetting the Password in the ECS OS
====================================

Scenarios
---------

This section describes how to reset the password for logging in to an ECS in the OS when the password is about to expire, the password is forgotten, or you are logging in to the ECS for the first time. It is a good practice to change the initial password upon the first login.

Prerequisites
-------------

The ECS can be logged in.

Background
----------

:ref:`Table 1 <en-us_topic_0122627689__en-us_topic_0021426802_table4381109318958>` shows the ECS password complexity requirements.

.. _en-us_topic_0122627689__en-us_topic_0021426802_table4381109318958:

.. table:: **Table 1** Password complexity requirements

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

Windows ECS
-----------

For a Windows ECS, log in to the ECS using the old password and reset the password in the OS.

#. Log in to the Windows ECS.

   For details, see :ref:`Login Overview (Windows) <en-us_topic_0092494943>`.

#. Press **Win+R** to start the **Run** dialog box.

#. Enter **cmd** to open the command-line interface (CLI) window.

#. Enter a new password that meets the requirements listed in :ref:`Table 1 <en-us_topic_0122627689__en-us_topic_0021426802_table4381109318958>`.

   **net user** **Administrator** *new-password*

Resetting the Password of a Linux ECS
-------------------------------------

#. Use the existing key file to log in to the ECS as user **root** through SSH.

   For details, see :ref:`Logging In to a Linux ECS Using an SSH Key Pair <en-us_topic_0017955380>`.

#. Run the following command to reset the password of user **root**:

   **passwd**

   To reset the password of another user, replace **passwd** with **passwd username**.

#. Enter a new password that meets the requirements listed in :ref:`Table 1 <en-us_topic_0122627689__en-us_topic_0021426802_table4381109318958>` as prompted.

   .. code-block::

      New password:
      Retype new password:

   If the following information is displayed, the password has been changed:

   .. code-block::

      passwd: all authentication tokens updates successfully
