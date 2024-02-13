:original_name: en-us_topic_0017955381.html

.. _en-us_topic_0017955381:

Login Using MSTSC
=================

Scenarios
---------

This section describes how to use the remote login tool MSTSC to log in to a Windows ECS from a local computer.

Prerequisites
-------------

-  The target ECS is running.
-  You have obtained the password for logging in to the Windows ECS. For details, see :ref:`Obtaining the Password for Logging In to a Windows ECS <en-us_topic_0031107266>`.
-  You have bound an EIP to the ECS. For details, see :ref:`Binding an EIP <en-us_topic_0174917535>`.

-  Access to port 3389 is allowed in the inbound direction of the security group to which the ECS belongs. For details, see :ref:`Configuring Security Group Rules <en-us_topic_0030878383>`.
-  The network connection between the login tool and the target ECS is normal. For example, the default port 3389 is not blocked by the firewall.
-  Remote Desktop Protocol (RDP) needs to be enabled on the target ECS. For ECSs created using public images, RDP has been enabled by default. For instructions about how to enable RDP, see :ref:`Enabling RDP <en-us_topic_0017955381__section65216898112059>`.

Logging In to a Windows ECS Using MSTSC
---------------------------------------

If your local server runs Windows, you can use the remote desktop connection tool MSTSC delivered with the Windows OS to log in to a Windows ECS.

#. Click the start menu on the local server.

#. In the **Search programs and files** text box, enter **mstsc**.

#. In the **Remote Desktop Connection** dialog box, click **Show Options**.


   .. figure:: /_static/images/en-us_image_0295941039.png
      :alt: **Figure 1** Show Options

      **Figure 1** Show Options

#. Enter the EIP and username (**Administrator** by default) of the target ECS.

   .. note::

      If you do not want to enter the username and password in follow-up logins, select **Allow me to save credentials**.


   .. figure:: /_static/images/en-us_image_0295941040.png
      :alt: **Figure 2** Remote Desktop Connection

      **Figure 2** Remote Desktop Connection

#. (Optional) To use local server resources in a remote session, configure parameters on the **Local Resources** tab.

   To copy data from the local server to your ECS, select **Clipboard**.


   .. figure:: /_static/images/en-us_image_0295941041.png
      :alt: **Figure 3** Clipboard

      **Figure 3** Clipboard

   To copy files from the local server to your ECS, click **More** and select your desired disks.


   .. figure:: /_static/images/en-us_image_0295940977.png
      :alt: **Figure 4** Drives

      **Figure 4** Drives

#. (Optional) Click the **Display** tab and then adjust the size of the remote desktop.


   .. figure:: /_static/images/en-us_image_0295940978.png
      :alt: **Figure 5** Adjusting the size of the desktop

      **Figure 5** Adjusting the size of the desktop

#. Click **Connect** and enter the login password as prompted to log in to the ECS.

   To ensure system security, change the login password after you log in to the ECS for the first time.

#. (Optional) Copy local files to the Windows ECS using clipboard. If the file size is greater than 2 GB, an error will occur.

   To resolve this issue, see `troubleshooting cases <https://learn.microsoft.com/en-us/troubleshoot/windows-server/remote/copying-2-gb-file-by-clipboard-redirection-fails>`__.

.. _en-us_topic_0017955381__section65216898112059:

Enabling RDP
------------

For your first login, use VNC to log in and enable RDP for your ECS. Then, use MSTSC to log in.

.. note::

   By default, RDP has been enabled on the ECSs created using a public image.

#. Log in to the Windows ECS using VNC.

   For details, see :ref:`Login Using VNC <en-us_topic_0027268511>`.

#. Click **Start** in the task bar and choose **Control Panel** > **System and Security** > **System** > **Remote settings**.

   The **System Properties** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0049287308.png
      :alt: **Figure 6** System Properties

      **Figure 6** System Properties

#. Click the **Remote** tab and select **Allow remote connections to this computer**.

#. Click **OK**.
