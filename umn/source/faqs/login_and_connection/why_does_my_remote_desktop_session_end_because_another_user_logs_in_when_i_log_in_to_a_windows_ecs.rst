Why Does My Remote Desktop Session End Because Another User Logs In When I Log In to a Windows ECS?
===================================================================================================

Symptom
-------

An error message is displayed indicating that your remote desktop session has ended because another user has connected to the remote computer.

| **Figure 1** Ended remote desktop session
| |image1|

Windows Server 2008
-------------------

#. Choose **Start** > **Administrative Tools** > **Remote Desktop Services** > **Remote Desktop Session Host Configuration**.\ **Figure 2** Remote Desktop Session Host Configuration
   |image2|
#. Double-click **Restrict each user to a single session** and deselect **Restrict each user to a single session**, and click **OK**.\ **Figure 3** Modifying the configuration
   |image3|

Windows Server 2012
-------------------

#. Choose **Start** > **Run**. In the **Run** dialog box, enter **gpedit.msc** and click **OK** to start Local Group Policy Editor.
#. Choose **Computer Configuration** > **Administrative Templates** > **Windows Components** > **Remote Desktop Services** > **Remote Desktop Session Host** > **Connections**.\ **Figure 4** Connections
   |image4|
#. Double-click **Restrict Remote Desktop Services users to a single Remote Desktop Services session**, change the value to **Disabled**, and click **OK**.\ **Figure 5** Modifying the configuration
   |image5|
#. Run **gpupdate/force** to update the group policy.


.. |image1| image:: /_static/images/en-us_image_0288997370.png

.. |image2| image:: /_static/images/en-us_image_0288997371.png
   :class: imgResize

.. |image3| image:: /_static/images/en-us_image_0288997372.png
   :class: imgResize

.. |image4| image:: /_static/images/en-us_image_0288997374.png
   :class: imgResize

.. |image5| image:: /_static/images/en-us_image_0288997375.png
   :class: imgResize

