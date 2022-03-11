Why Do I Fail to Connect to a Linux ECS Using WinSCP?
=====================================================

Symptom
-------

Connecting to a Linux ECS using WinSCP fails, while using SSH tools like Xshell succeeds.

| **Figure 1** Connection error using WinSCP
| |image1|

Root Cause
----------

If you can connect to a Linux ECS using SSH tools, the SSH tools run properly. Check the SFTP configuration file because WinSCP allows you to connect your Linux ECS via SFTP protocol.

Run the following command to view the **/etc/ssh/sshd_config** file:

**vi /etc/ssh/sshd_config**

Check the SFTP configuration and the configuration file is **/usr/libexec/openssh/sftp-server**.

| **Figure 2** SFTP configuration file
| |image2|

If the SFTP configuration file does not exist or the file permission is not 755, connecting to a Linux ECS using WinSCP will fail.

Solution
--------

-  If the SFTP configuration file does not exist, you can transfer the file from an ECS that runs properly to your Linux ECS using SCP or other file transfer tools.

-  If the file permission is not 755, you can run the following command to change the file permission to 755:

   **chmod 755 -R** **/usr/libexec/openssh/sftp-server**



.. |image1| image:: /_static/images/en-us_image_0000001189705789.png
   :class: imgResize

.. |image2| image:: /_static/images/en-us_image_0000001150707636.png
   :class: imgResize

