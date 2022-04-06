.. _en-us_topic_0000001189572473:

Why Do I Fail to Connect to a Linux ECS Using WinSCP?
=====================================================



.. _en-us_topic_0000001189572473__section17182131218710:

Symptom
-------

Connecting to a Linux ECS using WinSCP fails, while using SSH tools like Xshell succeeds.



.. _en-us_topic_0000001189572473__fig1580004542818:

.. figure:: /_static/images/en-us_image_0000001189705789.png
   :alt: Click to enlarge
   :figclass: imgResize


   **Figure 1** Connection error using WinSCP



.. _en-us_topic_0000001189572473__section826114231988:

Root Cause
----------

If you can connect to a Linux ECS using SSH tools, the SSH tools run properly. Check the SFTP configuration file because WinSCP allows you to connect your Linux ECS via SFTP protocol.

Run the following command to view the **/etc/ssh/sshd_config** file:

**vi /etc/ssh/sshd_config**

Check the SFTP configuration and the configuration file is **/usr/libexec/openssh/sftp-server**.



.. _en-us_topic_0000001189572473__fig6965144916501:

.. figure:: /_static/images/en-us_image_0000001150707636.png
   :alt: Click to enlarge
   :figclass: imgResize


   **Figure 2** SFTP configuration file

If the SFTP configuration file does not exist or the file permission is not 755, connecting to a Linux ECS using WinSCP will fail.



.. _en-us_topic_0000001189572473__section66451427981:

Solution
--------

-  If the SFTP configuration file does not exist, you can transfer the file from an ECS that runs properly to your Linux ECS using SCP or other file transfer tools.

-  If the file permission is not 755, you can run the following command to change the file permission to 755:

   **chmod 755 -R** **/usr/libexec/openssh/sftp-server**
