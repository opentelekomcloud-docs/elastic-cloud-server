:original_name: en-us_topic_0122627689.html

.. _en-us_topic_0122627689:

Changing the Login Password on an ECS
=====================================

Scenarios
---------

This section describes how to change the password for logging in to an ECS when the password is about to expire, the password is forgotten, or you are logging in to the ECS for the first time. It is a good practice to change the initial password upon the first login.

Prerequisites
-------------

The ECS can be logged in.

Background
----------

:ref:`Table 1 <en-us_topic_0122627689__en-us_topic_0021426802_table4381109318958>` shows the ECS password complexity requirements.

.. _en-us_topic_0122627689__en-us_topic_0021426802_table4381109318958:

.. table:: **Table 1** Password complexity requirements

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

Windows
-------

#. Log in to the ECS.

   For details, see :ref:`Login Overview <en-us_topic_0092494943>`.

#. Press **Win+R** to start the **Run** dialog box.

#. Enter **cmd** to open the command-line interface (CLI) window.

#. Run the following command to change the password (the new password must meet the requirements described in :ref:`Table 1 <en-us_topic_0122627689__en-us_topic_0021426802_table4381109318958>`):

   **net user** **Administrator** *New password*

Linux
-----

#. Use the existing key file to log in to the ECS as user **root** through SSH.

   For details, see :ref:`Login Using an SSH Key <en-us_topic_0017955380>`.

#. Run the following command to reset the password of user **root**:

   **passwd**

   To reset the password of another user, replace **passwd** with **passwd username**.

#. Enter the new password as prompted. Ensure that the new password meets the requirements described in :ref:`Table 1 <en-us_topic_0122627689__en-us_topic_0021426802_table4381109318958>`.

   .. code-block::

      New password:
      Retype new password:

   If the following information is displayed, the password has been changed:

   .. code-block::

      passwd: all authentication tokens updates successfully
