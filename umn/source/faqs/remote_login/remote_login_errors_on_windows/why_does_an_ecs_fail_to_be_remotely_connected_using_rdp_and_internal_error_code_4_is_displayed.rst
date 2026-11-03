:original_name: en-us_topic_0018124779.html

.. _en-us_topic_0018124779:

Why Does an ECS Fail to Be Remotely Connected Using RDP and Internal Error Code 4 Is Displayed?
===============================================================================================

Symptom
-------

An internal error is displayed when you log in to a Windows ECS and you fail to connect to the ECS remotely. Generally, this problem occurs because the Remote Desktop Services is busy.

Possible Causes
---------------

The Remote Desktop Services is busy.

The remote desktop is disconnected after login but is not logged out. To prevent this problem, log out of the ECS if you do not need to remotely connect to it.

Solution
--------

#. Use VNC provided by the management console to remotely log in to the ECS.

#. Open the Windows search box, enter **services**, and select **Services**.

#. In the **Services** window, restart **Remote Desktop Services**. Ensure that **Remote Desktop Services** is in the **Running** status.


   .. figure:: /_static/images/en-us_image_0000001100835050.png
      :alt: **Figure 1** Remote Desktop Services

      **Figure 1** Remote Desktop Services

#. Remotely connect to the ECS again.

   If the connection still fails, run the cmd command on the local server as the administrator, run the **netsh winsock reset** command to restore the default network connection configurations, and then retry the remote connection.
