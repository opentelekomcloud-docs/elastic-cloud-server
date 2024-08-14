:original_name: en-us_topic_0244854543.html

.. _en-us_topic_0244854543:

How Can I Change a Remote Login Port?
=====================================

Scenarios
---------

This section describes how to change a port for remote logins.

Windows
-------

The following procedure uses an ECS running Windows Server 2012 as an example. The default login port of a Windows ECS is 3389. To change it to port 2020, for example, do as follows:

#. Modify the security group rule.

   a. Log in to the management console.

   b. Click |image1| in the upper left corner and select your region and project.

   c. Under **Computing**, click **Elastic Cloud Server**.

   d. On the ECS list, click the name of an ECS for which you want to modify the security group rule.

   e. On the ECS details page, click the security group in the **Security Groups** area to go to the security group details page.

   f. On the **Inbound Rules** tab, click **Add Rule**. In the displayed dialog box, set **Protocol & Port** as follows:

      -  **Protocols**: TCP (Custom ports)
      -  **Port**: 2020

      For details, see "Adding a Security Group Rule" in the *Virtual Private Cloud User Guide*.

#. Log in to the ECS.

#. In the **Run** dialog box, enter **regedit** to access the registry editor.

#. In **Registry Editor**, choose **HKEY_LOCAL_MACHINE** > **SYSTEM** > **CurrentControlSet** > **Control** > **Terminal Server** > **Wds** > **rdpwd** > **Tds** > **tcp** and double-click **PortNumber**.

   a. In the dialog box that is displayed, set **Base** to **Decimal**.

   b. Change the value in **Value data** to the new port number, which is **2020** in this example.


      .. figure:: /_static/images/en-us_image_0244859999.png
         :alt: **Figure 1** Changing the port number to 2020

         **Figure 1** Changing the port number to 2020

#. In **Registry Editor**, choose **HKEY_LOCAL_MACHINE** > **SYSTEM** > **CurrentControlSet** > **Control** > **Terminal Server** > **WinStations** > **RDP-Tcp** and double-click **PortNumber**.

   a. In the dialog box that is displayed, set **Base** to **Decimal**.

   b. Change the value in **Value data** to the new port number, which is **2020** in this example.


      .. figure:: /_static/images/en-us_image_0244859999.png
         :alt: **Figure 2** Changing the port number to 2020

         **Figure 2** Changing the port number to 2020

#. (Skip this step if the firewall is disabled.) Modify the inbound rules of the firewall.

   Choose **Control Panel** > **Windows Firewall** > **Advanced Settings** > **Inbound Rules** > **New Rule**.

   -  **Rule Type**: **Port**
   -  Protocol in **Protocol and Ports**: **TCP**
   -  Port in **Protocol and Ports**: **Specific local ports**, **2020** in this example
   -  **Action**: **Allow the connection**
   -  **Profile**: Default settings
   -  **Name**: **RDP-2020**

   After the configuration, refresh the page to view the new rule.

#. Open the Windows search box, enter **services**, and select **Services**.


   .. figure:: /_static/images/en-us_image_0000001292832517.png
      :alt: **Figure 3** Selecting Services

      **Figure 3** Selecting Services

#. In the **Services** window, restart **Remote Desktop Services** or the ECS.

#. Use "IP address:Port" to remotely access the ECS.

Linux
-----

The following procedure uses an ECS running CentOS 7.3 as an example. The default login port of a Linux ECS is 22. To change it to port 2020, for example, do as follows:

#. Modify the security group rule.

   a. Log in to the management console.

   b. Click |image2| in the upper left corner and select your region and project.

   c. Under **Computing**, click **Elastic Cloud Server**.

   d. On the ECS list, click the name of an ECS for which you want to modify the security group rule.

   e. On the ECS details page, click the security group in the **Security Groups** area to go to the security group details page.

   f. On the **Inbound Rules** tab, click **Add Rule**. In the displayed dialog box, set **Protocol & Port** as follows:

      -  **Protocols**: TCP (Custom ports)
      -  **Port**: 2020

      For details, see "Adding a Security Group Rule" in the *Virtual Private Cloud User Guide*.

#. Log in to the ECS.

#. Run the following command to edit the sshd configuration file:

   **vi /etc/ssh/sshd_config**

#. Delete the comment tag (#) from the **#port 22** line and change **22** to **2020**.


   .. figure:: /_static/images/en-us_image_0244856480.png
      :alt: **Figure 4** Changing the port number to 2020

      **Figure 4** Changing the port number to 2020

#. Press **Esc** to exit Insert mode and enter **:wq!** to save the settings and exit.

#. Run either of the following commands to restart sshd:

   **service sshd restart**

   Or

   **systemctl restart sshd**

#. Skip this step if the firewall is disabled. Configure the firewall.

   The firewall varies depending on the CentOS version. CentOS 7 uses firewalld, and CentOS 6 uses iptables. The following operations use CentOS 7 as an example.

   Run the **firewall-cmd --state** command to check the firewall status.

   -  (Recommended) Method 1: Add information about a new port to firewalld.

      a. Run the following commands to add a rule for port 2020:

         **firewall-cmd --zone=public --add-port=2020/tcp --permanent**

         **firewall-cmd --reload**

      b. View the added port. The TCP connection of port 2020 will have been added.

         **firewall-cmd --list-all**

      c. Restart firewalld.

         **systemctl restart firewalld.service**

   -  Method 2: Disable the firewall and the function of automatically enabling the firewall upon ECS startup.

      **systemctl stop firewalld**

      **systemctl disable firewalld**

#. Run the following command to check whether the port is open:

   **telnet EIP Port**

   For example: **telnet xx.xx.xx.xx 2020**

.. |image1| image:: /_static/images/en-us_image_0210779229.png
.. |image2| image:: /_static/images/en-us_image_0210779229.png
