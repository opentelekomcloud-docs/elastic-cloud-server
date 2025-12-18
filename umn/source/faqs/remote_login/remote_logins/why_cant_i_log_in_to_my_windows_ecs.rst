:original_name: en-us_topic_0018073217.html

.. _en-us_topic_0018073217:

Why Can't I Log In to My Windows ECS?
=====================================

Symptom
-------

A Windows ECS fails to be logged in to due to some reasons. For example, the network is abnormal, the firewall blocks the local port required for remote desktop, or the ECS vCPUs are overloaded.

This section describes how to troubleshoot Windows ECS login failures.

If you cannot log in to your Windows ECS, follow the instructions provided in :ref:`Checking the VNC Login <en-us_topic_0018073217__section16351720103416>`. Then, locate the login fault by referring to :ref:`Fault Locating <en-us_topic_0018073217__section51421019195617>`.

.. _en-us_topic_0018073217__section16351720103416:

Checking the VNC Login
----------------------

Check whether you can log in to the ECS using VNC on the management console.

#. Log in to the management console.

#. Choose **Computing** > **Elastic Cloud Server**.

#. In the **Operation** column of the target ECS, click **Remote Login**.


   .. figure:: /_static/images/en-us_image_0000002259727498.png
      :alt: **Figure 1** Remote login

      **Figure 1** Remote login

#. (Optional) When the system displays "Press CTRL+ALT+DELETE to log on", click **Send CtrlAltDel** in the upper part of the remote login page to log in to the ECS.


   .. figure:: /_static/images/en-us_image_0042322120.png
      :alt: **Figure 2** Send CtrlAltDel

      **Figure 2** Send CtrlAltDel

If the VNC login still fails, record the resource details and fault occurred time for further fault locating and analysis.

.. _en-us_topic_0018073217__section51421019195617:

Fault Locating
--------------

If you can log in to the ECS using VNC but cannot log in to it using a remote desktop connection, locate the fault by referring to this section.

The following fault causes are sequenced based on their occurrence probability.

If the fault persists after you have ruled out a cause, check other causes.

.. table:: **Table 1** Possible causes and solutions

   +------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Possible Cause                                                               | Solution                                                                                                                                                                                                                                       |
   +==============================================================================+================================================================================================================================================================================================================================================+
   | The ECS is frozen or stopped.                                                | Make sure that the ECS is in the **Running** state. For details, see :ref:`Checking the ECS Status <en-us_topic_0018073217__section171182458381>`.                                                                                             |
   +------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The entered username or password is incorrect.                               | The default username for Windows ECSs is **Administrator**. For details, see :ref:`Checking the Login Mode <en-us_topic_0018073217__section14258101291715>`.                                                                                   |
   +------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The ECS is overloaded.                                                       | If the bandwidth or CPU usage of the ECS is excessively high, login failures may occur. For details, see :ref:`Checking Whether the ECS Is Overloaded <en-us_topic_0018073217__section1522711115588>`.                                         |
   +------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The ECS has no EIP bound.                                                    | To log in to an ECS using RDP or MSTSC, ensure that the ECS has an EIP bound. For details, see :ref:`Checking Whether an ECS Has an EIP Bound <en-us_topic_0018073217__section129793013377>`.                                                  |
   +------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The access is blocked by the Internet service provider (ISP).                | Check whether you can access the ECS using another hotspot or network. For details, see :ref:`Checking Whether the Network Is Normal <en-us_topic_0018073217__section289137105711>`.                                                           |
   +------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The access is blocked by the firewall.                                       | Disable the firewall and try again. For details, see :ref:`Checking Whether the Firewall Is Correctly Configured <en-us_topic_0018073217__section1130118816394>`.                                                                              |
   +------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The remote login port has been disabled in the security group or on the ECS. | Check whether the security group and the ECS allow traffic on the remote login port. For details, see :ref:`Checking Whether the Remote Access Port Is Correctly Configured <en-us_topic_0018073217__section21752310487>`.                     |
   +------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | An IP address whitelist for SSH logins has been configured.                  | Check whether an SSH login IP address whitelist is configured after HSS is enabled. For details, see :ref:`Checking the IP Address Whitelist for SSH Logins (with HSS Enabled) <en-us_topic_0018073217__section9583105919232>`.                |
   +------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The remote desktop protocol has been disabled on the ECS.                    | Make sure that the remote desktop protocol has been enabled on the ECS (only required for RDP and MSTSC logins). For details, see :ref:`Checking the Remote Desktop Protocol on the ECS <en-us_topic_0018073217__section5362274449>`.          |
   +------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The access is blocked by third-party antivirus software.                     | Disable or uninstall the third-party antivirus software and try again. For details, see :ref:`Checking Whether the Access Is Blocked by Antivirus Software <en-us_topic_0018073217__section58504535542>`.                                      |
   +------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The cause is displayed in the error message.                                 | If an error message is displayed during remote login, check the operation guide based on the error information. For details, see :ref:`Checking Whether an Error Occurred During a Remote Login <en-us_topic_0018073217__section23854594274>`. |
   +------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0018073217__section171182458381:

Checking the ECS Status
-----------------------

Check whether the ECS is in the **Running** state on the management console. If the ECS is stopped, start it and try to log in to the ECS again.


.. figure:: /_static/images/en-us_image_0000002259864122.png
   :alt: **Figure 3** Checking the ECS status

   **Figure 3** Checking the ECS status

.. _en-us_topic_0018073217__section14258101291715:

Checking the Login Mode
-----------------------

Check the login mode you set when you created the ECS.


.. figure:: /_static/images/en-us_image_0000002294405293.png
   :alt: **Figure 4** Login Mode

   **Figure 4** Login Mode

-  **Key pair**: If your ECS is authenticated using a key pair, use the key pair to obtain a password before logging in.

   #. Locate the ECS whose password is to be obtained, choose **More** > **Get Password** in the **Operation** column.
   #. Copy the content of the private key file and paste it into the text box. Click **Get Password** to obtain a new random password.

.. _en-us_topic_0018073217__section1522711115588:

Checking Whether the ECS Is Overloaded
--------------------------------------

If the bandwidth or CPU usage of the ECS is excessively high, login failures may occur.

If you have created an alarm rule in Cloud Eye, the system automatically sends an alarm notification to you when the bandwidth or CPU usage reaches the threshold specified in the rule.

To resolve this issue, perform the operations described in :ref:`Why Is My Windows ECS Running Slowly? <en-us_topic_0167429328>`

-  If the login failure is caused by high CPU usage, perform the following operations to reduce the CPU usage:

   -  Stop certain processes that are not used temporarily and try again.
   -  Verify that the Windows Update process is not running on the backend.
   -  Restart the ECS.
   -  Reinstall the ECS OS. Back up important data before the reinstallation.
   -  If the ECS OS cannot be reinstalled due to important data, replace the disk attached to the ECS. To do so, back up data on the original disk, detach the disk from the ECS, attach the new disk to the ECS, and copy data to the new disk.

   You can also upgrade the vCPUs and memory by :ref:`modifying ECS specifications <en-us_topic_0013771092>`.

-  If the login fails because the bandwidth exceeds the limit, perform the following operations:

   For instructions about how to increase the bandwidth, see :ref:`Modifying an EIP Bandwidth <en-us_topic_0093492521>`.

After you perform the preceding operations, try to remotely log in to the ECS again.

.. _en-us_topic_0018073217__section129793013377:

Checking Whether an ECS Has an EIP Bound
----------------------------------------

An ECS can access the Internet only after it has an EIP bound.

Before logging in to an ECS using MSTSC, make sure that an EIP has been bound to the ECS. For details, see `Assigning an EIP and Binding It to an ECS <https://docs.otc.t-systems.com/elastic-ip/umn/elastic_ip/assigning_an_eip_and_binding_it_to_an_ecs.html>`__.

.. note::

   If you log in to an ECS over an intranet, for example, using VPN or Direct Connect, you do not need to bind an EIP to the ECS.

.. _en-us_topic_0018073217__section289137105711:

Checking Whether the Network Is Normal
--------------------------------------

Use a local PC in another network or use another hotspot to access the ECS. Check whether the fault occurs on the local network. If so, contact the carrier to resolve this issue.

After you perform the preceding operations, try to remotely log in to the ECS again.

.. _en-us_topic_0018073217__section1130118816394:

Checking Whether the Firewall Is Correctly Configured
-----------------------------------------------------

Check whether the firewall is enabled.

#. Log in to the Windows ECS.

#. Click the Windows icon in the lower left corner of the desktop and choose **Control Panel** > **System and Security** > **Windows Firewall**.


   .. figure:: /_static/images/en-us_image_0281696224.png
      :alt: **Figure 5** Windows Firewall

      **Figure 5** Windows Firewall

#. Click **Check firewall status** and select **Turn on Windows Firewall** or **Turn off Windows Firewall**.

   View and set the firewall status.


   .. figure:: /_static/images/en-us_image_0281696226.png
      :alt: **Figure 6** Turning off a firewall

      **Figure 6** Turning off a firewall

Ensure that the remote access port on the local end is allowed on the firewall. The default port is TCP 3389.

If the port configured in the inbound rule of the firewall is different from that configured on the remote server, the remote login will fail. If this occurs, add the port configured on the remote server in the inbound rule of the firewall.

.. note::

   The default port is 3389. If you use another port, add that port in the inbound rule of the firewall.

After you perform the preceding operations, try to remotely log in to the ECS again.

.. _en-us_topic_0018073217__section21752310487:

Checking Whether the Remote Access Port Is Correctly Configured
---------------------------------------------------------------

#. Check whether port 3389 (used by default) on the ECS is accessible.

   Ensure that port 3389 has been added in the inbound rule.

   On the ECS details page, click the **Security Groups** tab and check port 3389 in the inbound rule of the security group.


   .. figure:: /_static/images/en-us_image_0000002385621273.png
      :alt: **Figure 7** Checking remote access ports

      **Figure 7** Checking remote access ports

   If you need to modify security group rules, see `Modifying a Security Group Rule <https://docs.otc.t-systems.com/virtual-private-cloud/umn/access_control/security_group/managing_security_group_rules/modifying_a_security_group_rule.html#vpc-securitygroup-0005>`__.

#. Check whether the remote connection port is changed.

   a. Choose **Start** > **Run**, enter **cmd**, and press **Enter**. In the CLI, enter **regedit** to open **Registry Editor**.

   b. In **HKEY_LOCAL_MACHINE\\System\\CurrentControlSet\\Control\\TerminalServer\\WinStations\\RDP Tcp\\PortNumber**, check whether the port is the default port 3389. If not, change the port to port 3389.

      |image1|

#. Check whether the number of connections is limited.

   Check the internal remote desktop configuration of the ECS.

   a. Choose **Start** > **Run**, enter **cmd**, and press **Enter**. In the CLI, enter **gpedit.msc** to open **Local Group Policy Editor**.

   b. Choose **Computer Configuration** > **Administrative Templates** > **Windows Components** > **Remote Desktop Services** > **Remote Desktop Session Host** > **Connections**. Then, in the **Limit number of connections** dialog box, check whether the number of connections is limited.

      |image2|

      .. note::

         If **Limit number of connections** is set to **Enabled**, a remote connection to the Windows ECS may fail when the number of connections exceeds the limit. In such a case, disable **Limit number of connections** or set a larger limit for connections.

After you perform the preceding operations, try to remotely log in to the ECS again.

.. _en-us_topic_0018073217__section9583105919232:

Checking the IP Address Whitelist for SSH Logins (with HSS Enabled)
-------------------------------------------------------------------

After HSS is enabled, you can configure an IP address whitelist for SSH logins as required. The IP address whitelist controls SSH access to ECSs, effectively preventing account cracking.

After you configure the allowlist, SSH logins will be allowed only from IP addresses in the allowlist.

#. On the **Events** page, check whether a local host IP address is intercepted due to brute force cracking.

#. Check whether the IP address whitelist for SSH logins has been enabled. If it has been enabled, ensure that the IP address of the local host has been added to the IP address whitelist.

   .. caution::

      -  Before enabling this function, ensure that all IP addresses that need to initiate SSH logins are added to the allowlist. Otherwise, you cannot remotely log in to your ECS through SSH.
      -  Exercise caution when adding a local IP address to the allowlist. This will make HSS no longer restrict access from this IP address to your ECSs.

   For more details, see `Configuring Server Login Protection <https://docs.otc.t-systems.com/host-security-service/umn/enabling_hss/common_security_configuration/configuring_server_login_protection.html#hss-01-0566>`__.

.. _en-us_topic_0018073217__section5362274449:

Checking the Remote Desktop Protocol on the ECS
-----------------------------------------------

Make sure that the remote desktop protocol has been enabled on the ECS (only required for MSTSC logins).

Log in to the ECS using VNC and enable the remote desktop protocol.

.. _en-us_topic_0018073217__section58504535542:

Checking Whether the Access Is Blocked by Antivirus Software
------------------------------------------------------------

Third-party antivirus software may lead to a failure in accessing the ECS.

If third-party antivirus software is running, check whether the remote connection is blocked by the software. If the remote connection is blocked, add the EIP bound to the ECS to the whitelist of the antivirus software and try to access the ECS again.

You can also disable or uninstall the third-party antivirus software and try to remotely log in to the ECS again.

.. _en-us_topic_0018073217__section23854594274:

Checking Whether an Error Occurred During a Remote Login
--------------------------------------------------------

If an error message is displayed during remote login, check the operation guide based on the error information.

If the fault persists, record the resource details and fault occurred time, and contact technical support for assistance

If the fault persists after the preceding operations are performed, record the resource details and fault occurred time, and contact customer service for technical support.

.. |image1| image:: /_static/images/en-us_image_0167092298.png
.. |image2| image:: /_static/images/en-us_image_0167101550.png
