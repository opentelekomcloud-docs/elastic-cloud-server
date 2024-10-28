:original_name: en-us_topic_0105127960.html

.. _en-us_topic_0105127960:

How Can I Change the Resolution of a Windows ECS?
=================================================

Scenarios
---------

You can change the resolution of Windows ECSs.

Solution 1: Using VNC
---------------------

The operations of changing an ECS resolution vary according to the Windows OS. This section uses the Windows Server 2016 Standard 64-bit edition as an example to describe how to change the resolution of a Windows ECS.

#. Log in to the ECS using VNC.

#. Right-click the desktop and choose **Display settings** from the shortcut menu.


   .. figure:: /_static/images/en-us_image_0165989823.png
      :alt: **Figure 1** Display settings

      **Figure 1** Display settings

#. On the **Settings** page, click the **Display** tab and then **Advanced display settings**.

   .. note::

      If the remote desktop is not fully displayed, set **Change the size of text, apps, and other items** to **100%**.


   .. figure:: /_static/images/en-us_image_0173685655.png
      :alt: **Figure 2** Settings

      **Figure 2** Settings

#. In the **Resolution** drop-down list, select the desired resolution.


   .. figure:: /_static/images/en-us_image_0165991075.png
      :alt: **Figure 3** Setting a resolution

      **Figure 3** Setting a resolution

#. Click **Apply**.

Solution 2: Using MSTSC
-----------------------

Before remotely logging in to your ECS using MSTSC, change the resolution of the Windows ECS.

#. On your local computer (client), click **Start**.

#. In the **Search programs and files** text box, enter **mstsc**.

#. In the **Remote Desktop Connection** window, click **Show Options** in the lower left corner.


   .. figure:: /_static/images/en-us_image_0166005634.png
      :alt: **Figure 4** Remote Desktop Connection

      **Figure 4** Remote Desktop Connection

#. Click the **Display** tab. Then, in the **Display configuration** pane, set the resolution.


   .. figure:: /_static/images/en-us_image_0166005912.png
      :alt: **Figure 5** Display

      **Figure 5** Display

#. Use MSTSC to log in to the ECS.
