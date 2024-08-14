:original_name: en-us_topic_0277097520.html

.. _en-us_topic_0277097520:

Why Am I Seeing the Error Message "Access denied" When I Remotely Log In to a Linux ECS?
========================================================================================

Symptom
-------

When you attempt to remotely log in to a Linux ECS, the system displays the error message "Access denied".

Possible Causes
---------------

-  Incorrect username or password.
-  A policy that denies logins from user **root** is enabled on the SSH server.

Solution
--------

-  If the username or password is incorrect

   Check the username and password.

-  If a policy that denies logins from user **root** is enabled on the SSH server,

   #. Edit the **/etc/ssh/sshd_config** file and check the following settings to ensure that the SSH logins from user **root** are allowed:

      .. code-block::

         PermitRootLogin yes

   #. Restart SSH.

      -  CentOS 6

         **service sshd restart**

      -  CentOS 7

         **systemctl restart sshd**
