Why Is My Remote Session Interrupted by a Protocol Error?
=========================================================

Symptom
-------

An error message is displayed indicating that the remote session will be disconnected because of a protocol error.

| **Figure 1** Protocol error
| |image1|

Possible Causes
---------------

The registry subkey Certificate is damaged.

Solution
--------

#. In the **Run** dialog box, enter **regedit** and click **OK** to open the registry editor.\ **Figure 2** Opening the registry editor
   |image2|
#. Choose **HKEY_LOCAL_MACHINE** > **SYSTEM** > **ControlSet001** > **Control** > **Terminal Server** > **RCM**.
#. Delete **Certificate**.\ **Figure 3** Deleting Certificate
   |image3|
#. Restart the ECS.
#. Choose **Start** > **Administrative Tools** > **Remote Desktop Services** > **Remote Desktop Session Host Configuration**.\ **Figure 4** Opening Remote Desktop Session Host Configuration
   |image4|
#. Right-click **RDP-Tcp** and choose **Properties**. In the displayed dialog box, click **General** and set **Security layer** to **RDP Security Layer**.\ **Figure 5** RDP-Tcp properties
   |image5|


.. |image1| image:: /_static/images/en-us_image_0288997423.png

.. |image2| image:: /_static/images/en-us_image_0288997424.png
   :class: imgResize

.. |image3| image:: /_static/images/en-us_image_0288997425.png
   :class: imgResize

.. |image4| image:: /_static/images/en-us_image_0288997426.png
   :class: imgResize

.. |image5| image:: /_static/images/en-us_image_0288997427.png
   :class: imgResize

