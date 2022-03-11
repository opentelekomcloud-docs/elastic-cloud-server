How Can I Use SFTP to Transfer Files Between a Local Linux Computer and a Linux ECS?
====================================================================================

Scenarios
---------

You want to use SFTP to transfer files between a local Linux computer and a Linux ECS. The following uses CentOS as an example.

Procedure
---------

#. Log in to the ECS as user **root**.

#. Run the following command to check the OpenSSH version, which is expected to be 4.8p1 or later:

   **ssh -V**

   Information similar to the following is displayed:

   .. code-block::

      # OpenSSH_7.4p1, OpenSSL 1.0.2k-fips 26 Jan 2017

#. Create a user group and a user (for example, **user1**).

   **groupadd sftp**

   **useradd -g sftp -s /sbin/nologin user1**

#. Set a password for the user.

   **passwd user1**

   | **Figure 1** Setting a password
   | |image1|

#. Assign permissions to directories.

   **chown** **root:sftp /home/user1**

   **chmod 755 -R /home/user1**

   **mkdir /home/user1/upload**

   **chown -R user1:sftp /home/user1/upload**

   **chmod -R 755 /home/user1/upload**

#. Run the following command to edit the **sshd_config** configuration file:

   **vim /etc/ssh/sshd_config**

   Comment out the following information:

   .. code-block::

      #Subsystem sftp /usr/libexec/openssh/sftp-server

   Add the following information:

   .. code-block::

      Subsystem sftp internal-sftp
      Match Group sftp
      ChrootDirectory /home/%u 
      ForceCommand internal-sftp
      AllowTcpForwarding no
      X11Forwarding no

   | **Figure 2** sshd_config file with the added information
   | |image2|

#. Run the following command to restart the ECS:

   **service sshd restart**

   Alternatively, run the following command to restart sshd:

   **systemctl restart sshd**

#. Run the following command on the local computer to set up the connection:

   **sftp root@**\ *IP address*

#. Run the **sftp** command to check the connection.

   |image3|

#. Transfer files or folders.

   To upload files or folders, run the **put -r** command.

   |image4|

   To download files or folders, run the **get -r** command.

   |image5|



.. |image1| image:: /_static/images/en-us_image_0263798009.png
   :class: imgResize

.. |image2| image:: /_static/images/en-us_image_0000001071727803.png
   :class: imgResize

.. |image3| image:: /_static/images/en-us_image_0263798010.png
   :class: imgResize

.. |image4| image:: /_static/images/en-us_image_0263798011.png
   :class: imgResize

.. |image5| image:: /_static/images/en-us_image_0263798012.png
   :class: imgResize

