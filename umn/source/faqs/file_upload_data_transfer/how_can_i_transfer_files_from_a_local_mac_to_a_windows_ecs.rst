How Can I Transfer Files from a Local Mac to a Windows ECS?
===========================================================

Scenarios
---------

This section describes how to use Microsoft Remote Desktop for Mac to transfer files from a local Mac to a Windows ECS.

Prerequisites
-------------

-  The remote access tool supported by Mac has been installed on the local Mac. This section uses Microsoft Remote Desktop for Mac as an example. `Download Microsoft Remote Desktop for Mac <https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-mac>`__.

-  The target ECS has had an EIP bound.

-  When you log in to the ECS for the first time, ensure that RDP has been enabled on it. To do so, use VNC to log in to the ECS, enable RDP, and access the ECS using MSTSC.\ |image1|

   By default, RDP has been enabled on the ECSs created using a public image.

Procedure
---------

#. Start Microsoft Remote Desktop.

#. Click **Add Desktop**.\ **Figure 1** Add Desktop
   |image2|

#. Set login parameters.

   -  **PC name**: Enter the EIP bound to the target Windows ECS.
   -  **User account**: Select **Add User Account** from the drop-down list.The **Add a User Account** dialog box is displayed.

      a. Enter username **administrator** and password for logging in to the Windows ECS and click **Add**.\ **Figure 2** Add user account
         |image3|
         **Figure 3** Add PC
         |image4|

#. 

   .. container::
   

      Select the folder to be uploaded.

      a. Click **Folders** and switch to the folder list.
      b. Click |image5| in the lower left corner, select the folder to be uploaded, and click **Add**.

#. On the **Remote Desktop** page, double-click the icon of the target Windows ECS.\ **Figure 4** Double-click for login
   |image6|

#. Confirm the information and click **Continue**.

   You have connected to the Windows ECS.

   View the shared folder on the ECS.

   Copy the files to be uploaded to the ECS. Alternatively, download the files from the ECS to your local Mac.


.. |image1| image:: /_static/images/note_3.0-en-us.png
.. |image2| image:: /_static/images/en-us_image_0295099237.png
   :class: imgResize

.. |image3| image:: /_static/images/en-us_image_0295099238.png

.. |image4| image:: /_static/images/en-us_image_0295099198.png
   :class: imgResize

.. |image5| image:: /_static/images/en-us_image_0295095212.png

.. |image6| image:: /_static/images/en-us_image_0295099239.png
   :class: imgResize

