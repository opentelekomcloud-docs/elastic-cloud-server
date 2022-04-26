:original_name: en-us_topic_0264235945.html

.. _en-us_topic_0264235945:

Why Is My Remote Session Interrupted by a Protocol Error?
=========================================================

Symptom
-------

An error message is displayed indicating that the remote session will be disconnected because of a protocol error.

.. _en-us_topic_0264235945__en-us_topic_0173587265_en-us_topic_0120795668_fig1256612592310:

.. figure:: /_static/images/en-us_image_0288997423.png
   :alt: **Figure 1** Protocol error


   **Figure 1** Protocol error

Possible Causes
---------------

The registry subkey Certificate is damaged.

Solution
--------

#. In the **Run** dialog box, enter **regedit** and click **OK** to open the registry editor.

   .. _en-us_topic_0264235945__en-us_topic_0173587265_fig429554874215:

   .. figure:: /_static/images/en-us_image_0288997424.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 2** Opening the registry editor

#. Choose **HKEY_LOCAL_MACHINE** > **SYSTEM** > **ControlSet001** > **Control** > **Terminal Server** > **RCM**.

#. Delete **Certificate**.

   .. _en-us_topic_0264235945__en-us_topic_0173587265_fig134336512282:

   .. figure:: /_static/images/en-us_image_0288997425.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 3** Deleting Certificate

#. Restart the ECS.

#. Choose **Start** > **Administrative Tools** > **Remote Desktop Services** > **Remote Desktop Session Host Configuration**.

   .. _en-us_topic_0264235945__en-us_topic_0173587265_fig15551901388:

   .. figure:: /_static/images/en-us_image_0288997426.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 4** Opening Remote Desktop Session Host Configuration

#. Right-click **RDP-Tcp** and choose **Properties**. In the displayed dialog box, click **General** and set **Security layer** to **RDP Security Layer**.

   .. _en-us_topic_0264235945__en-us_topic_0173587265_fig538416200307:

   .. figure:: /_static/images/en-us_image_0288997427.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 5** RDP-Tcp properties
