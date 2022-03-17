Why Does the System Display Error Code 0x1104 When I Log In to a Windows ECS?
=============================================================================

Symptom
-------

The system displays an error message indicating that a protocol error (code: 0x1104) is detected when you use MSTSC to access an ECS running Windows Server 2008.

.. figure:: /_static/images/en-us_image_0288997598.png
   :alt: Click to enlarge
   :figclass: imgResize


   **Figure 1** Protocol error (code: 0x1104)

Possible Causes
---------------

-  Port 3389 of the security group on the ECS is disabled.
-  The firewall on the ECS is disabled.
-  Port 3389 on the ECS is used by other processes.
-  The Remote Desktop Session Host is incorrectly configured.

Solution
--------

#. Check security group settings.

   Check whether port 3389 is allowed in inbound direction. If it is allowed, go to `2 <#enustopic0264235942enustopic0138293293li18622172719193>`__.

#. Check whether the firewall is disabled:

   a. Log in to the Windows ECS.

   b. Click the Windows icon in the lower left corner of the desktop and choose **Control Panel** > **Windows Firewall**.

      |image1|

   c. Click **Turn Windows Firewall on or off**.

      View and set the firewall status.

      |image2|

   If the firewall is enabled, go to `3 <#enustopic0264235942enustopic0138293293li15622182714191>`__.

#. Log in to the ECS using VNC and check the port.

   a. Open the **cmd** window and run the following command:

      **netstat -ano \|findstr: 3389**

      .. figure:: /_static/images/en-us_image_0288997604.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 2** Checking port 3389

      As shown in `Figure 2 <#enustopic0264235942enustopic0138293293fig1562219275192>`__, port 3389 is used by the process with ID of 4.

   b. Open Task Manager and find the process with ID of 4 is the System process.

   c. Generally, the IIS and SQL Server run as the System process. Run the following HTTP command for further check.

      **netsh http show servicestate**

      .. figure:: /_static/images/en-us_image_0288997606.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 3** Checking System process

   d. If port 3389 is used by HTTP protocols, it indicates that the port is used by IIS.

   e. Enter **http://127.0.0.1:3389** in the address box of the browser and press **Enter**. Check whether the website can be visited normally.

   f. Change the port used by IIS and restart IIS.

#. If no error occurs during the preceding steps, go to step `5 <#enustopic0264235942enustopic0138293293li19441439143520>`__ to check whether error 0x1104 is caused by the configuration of Remote Desktop Session Host.

#. Check the remote desktop session host configuration.

   a. Log in to the ECS using VNC.

   b. Open the **cmd** window and enter **gpedit.msc**.

   c. Click **OK** to start Local Group Policy Editor.

   d. Choose **Computer Configuration** > **Administrative Templates** > **Windows Components** > **Remote Desktop Services**.

      .. figure:: /_static/images/en-us_image_0288997608.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 4** Remote Desktop Services

   e. **Remote Desktop Session Host** > **Security**.

      .. figure:: /_static/images/en-us_image_0288997610.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 5** Remote (RDP) Connection requires the use of the specified security layer

   f. Set **Require use of specific security layer for remote (RDP) connections** to **Enabled** and **Security layer** to **RDP**.

      .. figure:: /_static/images/en-us_image_0288997612.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 6** Setting security layer

   g. Click **OK**.

   h. After the configuration is complete, open the **cmd** window.

   i. Run the following command to update the group policy:

      **gpupdate**

      .. figure:: /_static/images/en-us_image_0288997614.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 7** Updating the group policy



.. |image1| image:: /_static/images/en-us_image_0288997600.png
   :class: imgResize

.. |image2| image:: /_static/images/en-us_image_0288997602.png
   :class: imgResize

