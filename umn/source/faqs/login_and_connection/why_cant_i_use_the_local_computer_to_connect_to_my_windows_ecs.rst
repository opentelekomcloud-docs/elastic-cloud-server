Why Can't I Use the Local Computer to Connect to My Windows ECS?
================================================================

Symptom
-------

An error message is displayed indicating that your local computer cannot connect to the remote computer.

| **Figure 1** Cannot connect to the remote computer
| |image1|

Possible Causes
---------------

-  Port 3389 of the security group on the ECS is disabled. For details, see `Checking Port Configuration on the ECS <#EN-US_TOPIC_0264235939__en-us_topic_0250947106_section143451864405>`__.
-  The firewall on the ECS is disabled. For details, see `Checking Whether the Firewall Is Correctly Configured <#EN-US_TOPIC_0264235939__en-us_topic_0250947106_section1130118816394>`__.
-  The remote desktop connection is not correctly configured. For details, see `Checking Remote Desktop Connection Settings <#EN-US_TOPIC_0264235939__en-us_topic_0250947106_section1912111262434>`__.
-  Remote Desktop Services are not started. For solution, see `Checking Remote Desktop Services <#EN-US_TOPIC_0264235939__en-us_topic_0250947106_section42842535476>`__.
-  Remote Desktop Session Host is not correctly configured. For details, see `Checking Remote Desktop Session Host Configuration <#EN-US_TOPIC_0264235939__en-us_topic_0250947106_section108021655155012>`__.

Checking Port Configuration on the ECS
--------------------------------------

Check whether port 3389 (used by default) on the ECS is accessible.

Ensure that port 3389 has been added in the inbound rule.

On the page providing details about the ECS, click the **Security Groups** tab and view port 3389 in the inbound rule of the security group.

Checking Whether the Firewall Is Correctly Configured
-----------------------------------------------------

Check whether the firewall is enabled on the ECS.

#. Log in to the ECS using VNC available on the management console.

#. Click the Windows icon in the lower left corner of the desktop and choose **Control Panel** > **Windows Firewall**.\ **Figure 2** Windows Firewall
   |image2|

#. Click **Turn Windows Firewall on or off**.

   View and set the firewall status.

   | **Figure 3** Checking firewall status
   | |image3|

   To enable Windows firewall, perform the following steps:

#. Click **Advanced settings**.

#. Check **Inbound Rules** and ensure that the following rules are enabled:

   -  Remote Desktop - User Mode (TCP-In), Public
   -  Remote Desktop - User Mode (TCP-In), Domain, Private

   | **Figure 4** Inbound Rules
   | |image4|

   If the port configured in the inbound rule of the firewall is different from that configured on the remote server, the remote login will fail. If this occurs, add the port configured on the remote server in the inbound rule of the firewall.

|image5|

The default port is 3389. If you use another port, add that port in the inbound rule of the firewall.

After you perform the preceding operations, try to remotely log in to the ECS again.

Checking Remote Desktop Connection Settings
-------------------------------------------

Modify the remote desktop connection settings on the Windows ECS:

#. Log in to the ECS.
#. Click **Start** in the lower left corner, right-click **Computer**, and choose **Properties** from the shortcut menu.
#. In the left navigation pane, choose **Remote settings**.
#. Click the **Remote** tab. In the **Remote Desktop** pane, select **Allow connections from computers running any version of Remote Desktop (less secure)**.\ **Figure 5** Remote settings
   |image6|
#. Click **OK**.

Checking Remote Desktop Services
--------------------------------

#. Open the Windows search box, enter **services**, and select **Services**.
#. In the **Services** window, restart **Remote Desktop Services**. Ensure that **Remote Desktop Services** is in the **Running** status.\ **Figure 6** Remote Desktop Services
   |image7|

Checking Remote Desktop Session Host Configuration
--------------------------------------------------

#. Open the **cmd** window and enter **gpedit.msc**.
#. Click **OK** to start Local Group Policy Editor.
#. Choose **Computer Configuration** > **Administrative Templates** > **Windows Components** > **Remote Desktop Services**.
#. Choose **Remote Desktop Session Host** > **Security** > **Require use of specific security layer for remote (RDP) connections**.\ **Figure 7** Require use of specific security layer for remote (RDP) connections
   |image8|
#. Set **Require use of specific security layer for remote (RDP) connections** to **Enabled** and **Security layer** to **RDP**.\ **Figure 8** Setting security layer to RDP
   |image9|



.. |image1| image:: /_static/images/en-us_image_0288997242.png
   :class: imgResize

.. |image2| image:: /_static/images/en-us_image_0288997243.png
   :class: imgResize

.. |image3| image:: /_static/images/en-us_image_0288997244.png
   :class: imgResize

.. |image4| image:: /_static/images/en-us_image_0288997245.png
   :class: imgResize

.. |image5| image:: /_static/images/note_3.0-en-us.png
.. |image6| image:: /_static/images/en-us_image_0288997246.png
   :class: imgResize

.. |image7| image:: /_static/images/en-us_image_0288997248.png
   :class: imgResize

.. |image8| image:: /_static/images/en-us_image_0288997249.png
   :class: imgResize

.. |image9| image:: /_static/images/en-us_image_0288997250.png
   :class: imgResize

