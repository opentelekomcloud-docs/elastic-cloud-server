:original_name: en-us_topic_0145756657.html

.. _en-us_topic_0145756657:

Why No Audio File Can Be Properly Played on My Windows ECS Logged In Using VNC?
===============================================================================

Symptom
-------

When I logged in to my Windows ECS using MSTSC, audio files can be properly played. However, when I logged in to that ECS using VNC, audio files failed to be played.

Possible Causes
---------------

VNC does not support audio playing.

Solution
--------

Use your local PC (running Windows 7, for example) to play the audio files.

#. Start your local PC.

   .. note::

      Start your local PC, instead of logging in to your Windows ECS.

#. Press **Win+R** to start the **Run** text box.

#. Enter **mstsc** and click **OK**.

   The **Remote Desktop Connection** window is displayed.


   .. figure:: /_static/images/en-us_image_0145757646.png
      :alt: **Figure 1** Remote Desktop Connection

      **Figure 1** Remote Desktop Connection

#. Click **Options** in the lower left corner and click the **Local Resources** tab.


   .. figure:: /_static/images/en-us_image_0145757616.png
      :alt: **Figure 2** Local Resources

      **Figure 2** Local Resources

#. In the **Remote audio** pane, click **Settings**.


   .. figure:: /_static/images/en-us_image_0145757655.png
      :alt: **Figure 3** Setting remote audio playback

      **Figure 3** Setting remote audio playback

#. In the **Remote audio playback** pane, select **Play on this computer**.
