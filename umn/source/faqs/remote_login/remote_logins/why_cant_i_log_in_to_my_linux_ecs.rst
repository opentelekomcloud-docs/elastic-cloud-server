:original_name: en-us_topic_0105127983.html

.. _en-us_topic_0105127983:

Why Can't I Log In to My Linux ECS?
===================================

Symptom
-------

A Linux ECS cannot be logged in to due to some reasons. For example, the network is abnormal, the firewall does not allow access to the local port for accessing the remote desktop, or the ECS vCPUs are overloaded.

This section describes how to troubleshoot login failures on a Linux ECS.

If you cannot log in to your Linux ECS, follow the instructions provided in :ref:`Checking the VNC Login <en-us_topic_0105127983__section16351720103416>`. Then, locate the login fault by referring to :ref:`Fault Locating <en-us_topic_0105127983__section51421019195617>`.

.. _en-us_topic_0105127983__section16351720103416:

Checking the VNC Login
----------------------

Check whether you can log in to the ECS using VNC on the management console.

#. Log in to the management console.

#. Under **Computing**, choose **Elastic Cloud Server**.

#. In the **Operation** column of the target ECS, click **Remote Login**.


   .. figure:: /_static/images/en-us_image_0000002259727498.png
      :alt: **Figure 1** Remote login

      **Figure 1** Remote login

#. (Optional) When the system displays "Press CTRL+ALT+DELETE to log on", click **Send CtrlAltDel** in the upper part of the remote login page to log in to the ECS.

   .. note::

      Do not press **CTRL+ALT+DELETE** on the physical keyboard because this operation does not take effect.

If the VNC login still fails, record the resource details and fault occurred time for further fault locating and analysis.

.. _en-us_topic_0105127983__section51421019195617:

Fault Locating
--------------

If you can log in to the ECS using VNC but cannot log in to the ECS using a remote desktop connection, locate the fault as follows.

The following fault causes are sequenced based on their occurrence probability.

If the fault persists after you have ruled out a cause, check other causes.

.. table:: **Table 1** Possible causes and solutions

   +--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Possible Cause                                                                 | Solution                                                                                                                                                                                                                                        |
   +================================================================================+=================================================================================================================================================================================================================================================+
   | The ECS is frozen or stopped.                                                  | Make sure that the ECS is in the **Running** state. For details, see :ref:`Checking the ECS Status <en-us_topic_0105127983__section171182458381>`.                                                                                              |
   +--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The entered username or password is incorrect.                                 | The default username for Linux ECSs is **root**. For details, see :ref:`Checking the Login Mode <en-us_topic_0105127983__section14258101291715>`.                                                                                               |
   +--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The ECS is overloaded.                                                         | If the bandwidth or CPU usage of the ECS is excessively high, login failures may occur. For details, see :ref:`Checking Whether the ECS Is Overloaded <en-us_topic_0105127983__section1522711115588>`.                                          |
   +--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The ECS has no EIP bound.                                                      | To log in to an ECS using RDP or MSTSC, ensure that the ECS has an EIP bound. For details, see :ref:`Checking Whether an ECS Has an EIP Bound <en-us_topic_0105127983__section129793013377>`.                                                   |
   +--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The access is blocked by the ISP.                                              | Check whether you can access the ECS using another hotspot or network. For details, see :ref:`Checking Whether the Network Is Normal <en-us_topic_0105127983__section289137105711>`.                                                            |
   +--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The security group of the ECS denies inbound traffic on the remote login port. | Check whether the security group allows inbound traffic on the remote login port. For details, see :ref:`Checking Whether the Security Group Is Correctly Configured <en-us_topic_0105127983__section830193612460>`.                            |
   +--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The remote access port is incorrectly configured.                              | Check whether the remote access port is correctly configured on the local computer and the ECS. For details, see :ref:`Checking Whether the Remote Access Port Is Correctly Configured <en-us_topic_0105127983__section21752310487>`.           |
   +--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | An IP address whitelist for SSH logins has been configured.                    | Check whether an SSH login IP address whitelist is configured after HSS is enabled. For details, see :ref:`Checking the IP Address Whitelist for SSH Logins (with HSS Enabled) <en-us_topic_0105127983__section9583105919232>`.                 |
   +--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | An OS fault has occurred.                                                      | The file system is damaged. For details, see :ref:`Checking Whether an OS Fault Has Occurred <en-us_topic_0105127983__section1977334311553>`.                                                                                                   |
   +--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The access is blocked by third-party antivirus software.                       | Disable or uninstall the third-party antivirus software and try again. For details, see :ref:`Checking Whether the Access Is Blocked by Antivirus Software <en-us_topic_0105127983__section58504535542>`.                                       |
   +--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The cause is displayed in the error message.                                   | If an error message is displayed during remote login, check the operation guide based on the error information. For details, see :ref:`Checking Whether an Error Occurred During a Remote Login <en-us_topic_0105127983__section331935012531>`. |
   +--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0105127983__section171182458381:

Checking the ECS Status
-----------------------

Check whether the ECS is in the **Running** state on the management console. If the ECS is stopped, start it and try to log in to the ECS again.


.. figure:: /_static/images/en-us_image_0000002259864122.png
   :alt: **Figure 2** Checking the ECS status

   **Figure 2** Checking the ECS status

.. _en-us_topic_0105127983__section14258101291715:

Checking the Login Mode
-----------------------

Check the login mode you set when you created the ECS.


.. figure:: /_static/images/en-us_image_0000002294960765.png
   :alt: **Figure 3** Login Mode

   **Figure 3** Login Mode

-  **Key pair**

   -  For the first login, use an SSH key. For details, see :ref:`Logging In to a Linux ECS Using an SSH Key Pair <en-us_topic_0017955380>`.
   -  For a non-first login, if you want to use the remote login function (VNC) provided by the management console, log in to the ECS using the SSH key and set the password.

.. _en-us_topic_0105127983__section1522711115588:

Checking Whether the ECS Is Overloaded
--------------------------------------

If the bandwidth or CPU usage of the ECS is excessively high, login failures may occur.

If you have created an alarm rule in Cloud Eye, the system automatically sends an alarm notification to you when the bandwidth or CPU usage reaches the threshold specified in the rule.

To resolve this issue, perform the operations described in :ref:`Why Is My Linux ECS Running Slowly? <en-us_topic_0167429329>`

-  If the login failure is caused by high CPU usage, perform the following operations to reduce the CPU usage:

   -  Stop certain processes that are not used temporarily and try again.
   -  Restart the ECS.
   -  Reinstall the ECS OS. Back up important data before the reinstallation.
   -  If the ECS OS cannot be reinstalled due to important data, replace the disk attached to the ECS. To do so, back up data on the original disk, detach the disk from the ECS, attach the new disk to the ECS, and copy data to the new disk.

   You can also upgrade the vCPUs and memory by :ref:`modifying ECS specifications <en-us_topic_0013771092>`.

-  If the login fails because the bandwidth exceeds the limit, perform the following operations:

   For instructions about how to increase the bandwidth, see :ref:`Modifying an EIP Bandwidth <en-us_topic_0093492521>`.

After you perform the preceding operations, try to remotely log in to the ECS again.

.. _en-us_topic_0105127983__section129793013377:

Checking Whether an ECS Has an EIP Bound
----------------------------------------

If you need to use a remote login tool (such as PuTTY or Xshell) to access the ECS, bind an EIP to the ECS.

For details, see `Assigning an EIP and Binding It to an ECS <https://docs.otc.t-systems.com/elastic-ip/umn/elastic_ip/assigning_an_eip_and_binding_it_to_an_ecs.html>`__.

.. _en-us_topic_0105127983__section289137105711:

Checking Whether the Network Is Normal
--------------------------------------

Use a local PC in another network or use another hotspot to access the ECS. Check whether the fault occurs on the local network. If so, contact the carrier to resolve this issue.

After you perform the preceding operations, try to remotely log in to the ECS again.

.. _en-us_topic_0105127983__section830193612460:

Checking Whether the Security Group Is Correctly Configured
-----------------------------------------------------------

Check whether the local host can access port 22 on the ECS.

Run the following command to check whether port 22 is accessible:

**telnet ECS private IP address**

If port 22 is inaccessible, check whether port 22 is opened in the security group rule.

On the ECS details page, click the **Security Groups** tab and check that port 22 is configured in the inbound rule of the security group.


.. figure:: /_static/images/en-us_image_0000002260436902.png
   :alt: **Figure 4** Checking remote access ports

   **Figure 4** Checking remote access ports

For details about how to modify a security group rule, see `Modifying a Security Group Rule <https://docs.otc.t-systems.com/virtual-private-cloud/umn/access_control/security_group/managing_security_group_rules/modifying_a_security_group_rule.html#vpc-securitygroup-0005>`__.

After you perform the preceding operations, try to remotely log in to the ECS again.

.. _en-us_topic_0105127983__section21752310487:

Checking Whether the Remote Access Port Is Correctly Configured
---------------------------------------------------------------

Check ECS settings.

#. Check whether the sshd process is running.

#. Check whether your local PC is denied by the ECS.

   a. Log in to the ECS and run the following command:

      **vi /etc/hosts.deny**

   b. If the IP address of the local PC is in the **hosts.deny** file, the ECS denies connection attempts from the local PC. In such a case, delete the IP address from the file.

#. Open the **/etc/ssh/ssh_config** file in the local PC and view the default login port. Then, open the **/etc/ssh/sshd_config** file in the ECS and check whether the SSH port is the default port 22.

   |image1|

After you perform the preceding operations, try to remotely log in to the ECS again.

.. _en-us_topic_0105127983__section9583105919232:

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

.. _en-us_topic_0105127983__section1977334311553:

Checking Whether an OS Fault Has Occurred
-----------------------------------------

-  Password injection failure

   The password failed to be injected using Cloud-Init.

-  File system damaged after a forcible stop

   There is a low probability that the file system is damaged after a forcible stop, which causes the ECS fails to be restarted. For details, see :ref:`Why Does a Forcibly-Stopped Linux ECS Fail to Be Restarted? <en-us_topic_0102008259>`

After you perform the preceding operations, try to remotely log in to the ECS again.

.. _en-us_topic_0105127983__section58504535542:

Checking Whether the Access Is Blocked by Antivirus Software
------------------------------------------------------------

Third-party antivirus software may lead to a failure in accessing the ECS.

If third-party antivirus software is running, check whether the remote connection is blocked by the software. If the remote connection is blocked, add the EIP bound to the ECS to the whitelist of the antivirus software and try to access the ECS again.

You can also disable or uninstall the third-party antivirus software and try to remotely log in to the ECS again.

.. _en-us_topic_0105127983__section331935012531:

Checking Whether an Error Occurred During a Remote Login
--------------------------------------------------------

If an error message is displayed during remote login, check the operation guide based on the error information.

If the fault persists, record the resource details and fault occurred time, and contact technical support for assistance.

If the fault persists after the preceding operations are performed, record the resource details and fault occurred time, and contact customer service for technical support.

.. |image1| image:: /_static/images/en-us_image_0164069962.png
