:original_name: en-us_topic_0277132844.html

.. _en-us_topic_0277132844:

What Should I Do If Error Message "Disconnected: No supported authentication methods available" Is Displayed When I Remotely Log In to a Linux ECS?
===================================================================================================================================================

Symptom
-------

When I attempted to remotely log in to a Linux ECS, the system displayed error message "Disconnected: No supported authentication methods available".

.. _en-us_topic_0277132844__fig2069165133516:

.. figure:: /_static/images/en-us_image_0277132897.png
   :alt: Click to enlarge
   :figclass: imgResize


   **Figure 1** No supported authentication methods available

Possible Causes
---------------

A policy that denies password-authenticated logins is enabled on the SSH server.

Solution
--------

#. Open the **/etc/ssh/sshd_config** file and check the following settings:

   **vi /etc/ssh/sshd_config**

#. Modify the following settings:

   Change **PasswordAuthentication no** to **PasswordAuthentication yes**.

   Alternatively, delete the comment tag (#) before **PasswordAuthentication yes**.

#. Restart SSH.

   -  CentOS 6

      **service sshd restart**

   -  CentOS 7

      **systemctl restart sshd**
