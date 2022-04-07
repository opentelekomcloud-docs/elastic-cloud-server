.. _en-us_topic_0264235944:

Why Does the System Display Invalid Certificate or Associated Chain When I Log In to a Windows ECS from a Mac?
==============================================================================================================

Symptom
-------

When you use Microsoft Remote Desktop for Mac to remotely access a Windows ECS, the system displays invalid certificate or associated chain.

.. _en-us_topic_0264235944__en-us_topic_0138877154_fig13103521154816:

.. figure:: /_static/images/en-us_image_0000001122204673.png
   :alt: Click to enlarge
   :figclass: imgResize


   **Figure 1** Microsoft Remote Desktop for Mac

Due to the particularity of the Mac system, you need to perform internal configurations on Mac and the Windows ECS to ensure successful remote connection. When you log in to the Windows ECS using Microsoft Remote Desktop for Mac, the system displays an error message indicating that the certificate or associated chain is invalid.

.. _en-us_topic_0264235944__en-us_topic_0138877154_fig135204375528:

.. figure:: /_static/images/en-us_image_0000001122141457.png
   :alt: Click to enlarge
   :figclass: imgResize


   **Figure 2** Invalid certificate or associated chain

Possible Causes
---------------

The group policy setting is incorrect on the ECS.

Procedure
---------

#. On the menu bar in the upper left corner, choose **RDC** > **Preferences** to open the preference setting page of the Microsoft Remote Desktop.

   .. _en-us_topic_0264235944__en-us_topic_0138877154_fig1018664945218:

   .. figure:: /_static/images/en-us_image_0000001122204675.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 3** Preferences setting

#. Select **Security** and modify the parameter settings according the following figure.

   .. _en-us_topic_0264235944__en-us_topic_0138877154_fig121513225316:

   .. figure:: /_static/images/en-us_image_0000001122000977.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 4** Security setting

#. Remotely connect to the Windows ECS again. If the error message **Invalid certificate or associated chain** is still displayed, go to :ref:`4 <en-us_topic_0264235944__en-us_topic_0138877154_li19176131183810>`.

#. .. _en-us_topic_0264235944__en-us_topic_0138877154_li19176131183810:

   Log in to the Windows ECS using VNC.

#. Press **Win+R** to start the **Open** text box.

#. Enter **gpedit.msc** to access the Local Group Policy Editor.

#. In the left navigation pane, choose **Computer Configuration** > **Administrative Templates** > **Windows Components** > **Remote Desktop Services** > **Remote Desktop Session Host** > **Security**.

   .. _en-us_topic_0264235944__en-us_topic_0138877154_fig113613152539:

   .. figure:: /_static/images/en-us_image_0000001122000979.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 5** Remote Desktop Session Host

#. Modify the following parameters as prompted:

   -  Enable **Require use of specific security layer for remote (RDP) connections**.

      .. _en-us_topic_0264235944__en-us_topic_0138877154_fig1461293695320:

      .. figure:: /_static/images/en-us_image_0000001121886253.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 6** Require use of specific security layer for remote (RDP) connections

   -  Disable **Require user authentication for remote connections by using Network Level Authentication**.

      .. _en-us_topic_0264235944__en-us_topic_0138877154_fig135815477530:

      .. figure:: /_static/images/en-us_image_0000001122204677.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 7** Remote connection authentication

#. Close the group policy editor and restart the ECS.
