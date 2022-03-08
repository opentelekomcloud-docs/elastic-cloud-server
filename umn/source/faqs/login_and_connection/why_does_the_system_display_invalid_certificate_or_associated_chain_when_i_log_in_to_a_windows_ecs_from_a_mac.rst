Why Does the System Display Invalid Certificate or Associated Chain When I Log In to a Windows ECS from a Mac?
==============================================================================================================

Symptom
-------

When you use Microsoft Remote Desktop for Mac to remotely access a Windows ECS, the system displays invalid certificate or associated chain.

| **Figure 1** Microsoft Remote Desktop for Mac
| |image1|

Due to the particularity of the Mac system, you need to perform internal configurations on Mac and the Windows ECS to ensure successful remote connection. When you log in to the Windows ECS using Microsoft Remote Desktop for Mac, the system displays an error message indicating that the certificate or associated chain is invalid.

| **Figure 2** Invalid certificate or associated chain
| |image2|

Possible Causes
---------------

The group policy setting is incorrect on the ECS.

Procedure
---------

#. On the menu bar in the upper left corner, choose **RDC** > **Preferences** to open the preference setting page of the Microsoft Remote Desktop.\ **Figure 3** Preferences setting
   |image3|
#. Select **Security** and modify the parameter settings according the following figure.\ **Figure 4** Security setting
   |image4|
#. Remotely connect to the Windows ECS again. If the error message **Invalid certificate or associated chain** is still displayed, go to `4 <#EN-US_TOPIC_0264235944__en-us_topic_0138877154_li19176131183810>`__.
#. Log in to the Windows ECS using VNC.
#. Press **Win+R** to start the **Open** text box.
#. Enter **gpedit.msc** to access the Local Group Policy Editor.
#. In the left navigation pane, choose **Computer Configuration** > **Administrative Templates** > **Windows Components** > **Remote Desktop Services** > **Remote Desktop Session Host** > **Security**.\ **Figure 5** Remote Desktop Session Host
   |image5|
#. Modify the following parameters as prompted:

   -  Enable **Require use of specific security layer for remote (RDP) connections**.\ **Figure 6** Require use of specific security layer for remote (RDP) connections
      |image6|
   -  Disable **Require user authentication for remote connections by using Network Level Authentication**.\ **Figure 7** Remote connection authentication
      |image7|

#. Close the group policy editor and restart the ECS.


.. |image1| image:: /_static/images/en-us_image_0000001122204673.png
   :class: imgResize

.. |image2| image:: /_static/images/en-us_image_0000001122141457.png
   :class: imgResize

.. |image3| image:: /_static/images/en-us_image_0000001122204675.png
   :class: imgResize

.. |image4| image:: /_static/images/en-us_image_0000001122000977.png
   :class: imgResize

.. |image5| image:: /_static/images/en-us_image_0000001122000979.png
   :class: imgResize

.. |image6| image:: /_static/images/en-us_image_0000001121886253.png
   :class: imgResize

.. |image7| image:: /_static/images/en-us_image_0000001122204677.png
   :class: imgResize

