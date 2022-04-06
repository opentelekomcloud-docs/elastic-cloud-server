.. _en-us_topic_0277097520:

Why Am I Seeing the Error Message "Access denied" When I Remotely Log In to a Linux ECS?
========================================================================================



.. _en-us_topic_0277097520__section118312613216:

Symptom
-------

When you attempt to remotely log in to a Linux ECS, the system displays the error message "Access denied".



.. _en-us_topic_0277097520__section1851618545810:

Possible Causes
---------------

-  Incorrect username or password.
-  A policy that denies logins from user **root** is enabled on the SSH server.



.. _en-us_topic_0277097520__section1286672717516:

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
