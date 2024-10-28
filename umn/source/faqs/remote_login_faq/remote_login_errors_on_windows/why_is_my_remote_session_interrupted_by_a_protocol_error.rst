:original_name: en-us_topic_0264235945.html

.. _en-us_topic_0264235945:

Why Is My Remote Session Interrupted by a Protocol Error?
=========================================================

Symptom
-------

An error message is displayed indicating that the remote session will be disconnected because of a protocol error.


.. figure:: /_static/images/en-us_image_0288997423.png
   :alt: **Figure 1** Protocol error

   **Figure 1** Protocol error

Possible Causes
---------------

The registry subkey Certificate is damaged.

Solution
--------

#. In the **Run** dialog box, enter **regedit** and click **OK** to open the registry editor.


   .. figure:: /_static/images/en-us_image_0288997424.png
      :alt: **Figure 2** Opening the registry editor

      **Figure 2** Opening the registry editor

#. Choose **HKEY_LOCAL_MACHINE** > **SYSTEM** > **ControlSet001** > **Control** > **Terminal Server** > **RCM**.

#. Delete **Certificate**.


   .. figure:: /_static/images/en-us_image_0288997425.png
      :alt: **Figure 3** Deleting Certificate

      **Figure 3** Deleting Certificate

#. Restart the ECS.

#. Choose **Start** > **Administrative Tools** > **Remote Desktop Services** > **Remote Desktop Session Host Configuration**.


   .. figure:: /_static/images/en-us_image_0288997426.png
      :alt: **Figure 4** Opening Remote Desktop Session Host Configuration

      **Figure 4** Opening Remote Desktop Session Host Configuration

#. Right-click **RDP-Tcp** and choose **Properties**. In the displayed dialog box, click **General** and set **Security layer** to **RDP Security Layer**.


   .. figure:: /_static/images/en-us_image_0288997427.png
      :alt: **Figure 5** RDP-Tcp properties

      **Figure 5** RDP-Tcp properties
