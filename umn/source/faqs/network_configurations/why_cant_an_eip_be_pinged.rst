Why Can't an EIP Be Pinged?
===========================

Symptom
-------

After you purchase an EIP and bind it to an ECS, the ping operation to the EIP fails, or the ECS fails to access the Internet.

Fault Locating
--------------

The following fault causes are sequenced based on their occurrence probability.

If the fault persists after you have ruled out a cause, check other causes.

.. figure:: /_static/images/en-us_image_0293553366.png
   :alt: Click to enlarge
   :figclass: imgResize


   **Figure 1** Method of locating the failure to ping an EIP



.. _ENUSTOPIC0105130172table6168184132811:

.. container:: table-responsive

   .. table:: **Table 1** Method of locating the failure to ping an EIP

      +--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Possible Cause                                               | Solution                                                                                                                                                                                                                                                                                  |
      +==============================================================+===========================================================================================================================================================================================================================================================================================+
      | ICMP access rules are not added to the security group.       | Add ICMP access rules to the security group. For details, see `Checking Security Group Rules <#checking-security-group-rules>`__.                                                                                                                                                         |
      +--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Ping operations are prohibited on the firewall.              | Allow ping operations on the firewall. For details, see `Checking Firewall Settings <#checking-firewall-settings>`__.                                                                                                                                                                     |
      +--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Ping operations are prohibited on the ECS.                   | Allow ping operations on the ECS. For details, see `Checking Whether Ping Operations Have Been Disabled on the ECS <#checking-whether-ping-operations-have-been-disabled-on-the-ecs>`__.                                                                                                  |
      +--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Network ACL is associated.                                   | If the VPC is associated with a network ACL, check the network ACL rules. For details, see `Checking ACL Rules <#checking-acl-rules>`__.                                                                                                                                                  |
      +--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | A network exception occurred.                                | Use another ECS in the same region to check whether the local network is functional. For details, see `Checking Whether the Network Is Functional <#checking-whether-the-network-is-functional>`__.                                                                                       |
      +--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Routes are incorrectly configured if multiple NICs are used. | If the network is inaccessible due to an extension NIC, the fault is generally caused by incorrect route configurations. To resolve this issue, see `Checking the ECS Route Configuration If Multiple NICs Are Used <#checking-the-ecs-route-configuration-if-multiple-nics-are-used>`__. |
      +--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Checking Security Group Rules
-----------------------------

The ping operations use the ICMP protocol. Check whether the security group accommodating the ECS allows ICMP traffic in the inbound direction.

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the **Elastic Cloud Server** page, click the name of the target ECS.

   The page providing details about the ECS is displayed.

#. Click the **Security Groups** tab, expand the information of the security group, and view security group rules.

#. Click the security group ID.

   The system automatically switches to the **Security Group** page.

#. On the **Inbound Rules** tab, click **Add Rule**. In the displayed dialog box, set required parameters to add an inbound rule. 

.. _ENUSTOPIC0105130172table156272235264:

   .. container:: table-responsive

      .. table:: **Table 2** Security group rules

         +--------------------+-----------------+---------------------+---------------------------------------+
         | Transfer Direction | Type            | Protocol/Port Range | Source                                |
         +====================+=================+=====================+=======================================+
         | Inbound            | IPv4            | ICMP/Any            | 0.0.0.0/0                             |
         |                    |                 |                     |                                       |
         |                    |                 |                     | 0.0.0.0/0 indicates all IP addresses. |
         +--------------------+-----------------+---------------------+---------------------------------------+

#. Click **OK** to complete the security rule configuration.

Checking Firewall Settings
--------------------------

If a firewall is enabled on the ECS, check whether the firewall blocks the ping operations.

**Linux**

#. Consider CentOS 7 as an example. Run the following command to check the firewall status:

   **firewall-cmd --state**

   If **running** is displayed in the command output, the firewall has been enabled.

2. Check whether there is any ICMP rule blocking the ping operations.

   **iptables -L**

   If the command output shown in Figure 2 is displayed, there is no ICMP rule blocking the ping operations.

   .. figure:: /_static/images/en-us_image_0250117342.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 2** Checking firewall rules

   If the ping operations are blocked by an ICMP rule, run the following commands to modify the rule for unblocking:

   **iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT**

   **iptables -A OUTPUT -p icmp --icmp-type echo-reply -j ACCEPT**

**Windows**

#. Log in to the Windows ECS, click the Windows icon in the lower left corner of the desktop, and choose **Control Panel** > **Windows Firewall**.

#. Click **Turn Windows Firewall on or off**.

   View and set the firewall status.

#. If the firewall is **On**, go to `4 <#enustopic0105130172li192824161474>`__.

#. Check the ICMP rule statuses in the firewall.

   a. In the navigation pane on the **Windows Firewall** page, click **Advanced settings**.

   b. Enable the following rules:

      **Inbound Rules**: **File and Printer Sharing (Echo Request - ICMPv4-In)**

      **Outbound Rules**: **File and Printer Sharing (Echo Request - ICMPv4-Out)**

      If IPv6 is enabled, enable the following rules:

      **Inbound Rules**: **File and Printer Sharing (Echo Request - ICMPv6-In)**

      **Outbound Rules**: **File and Printer Sharing (Echo Request - ICMPv6-Out)**

      .. figure:: /_static/images/en-us_image_0250182352.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 3** Inbound Rules

      .. figure:: /_static/images/en-us_image_0250182717.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 4** Outbound Rules

Checking Whether Ping Operations Have Been Disabled on the ECS
--------------------------------------------------------------

**Windows**

Enable ping operations using the CLI.

#. Start the **Run** dialog box. Enter **cmd** and press **Enter**.

#. Run the following command to enable ping operations:

   **netsh firewall set icmpsetting 8**

**Linux**

Check the ECS kernel parameters.

#. Check the **net.ipv4.icmp_echo_ignore_all** value in the **/etc/sysctl.conf** file. Value **0** indicates that ping operations are allowed, and value **1** indicates that ping operations are prohibited.
#. Allow ping operations.

   -  Run the following command to temporarily allow the ping operations:

      #echo 0 >/proc/sys/net/ipv4/icmp_echo_ignore_all

   -  Run the following command to permanently allow the ping operations:

      net.ipv4.icmp_echo_ignore_all=0

Checking ACL Rules
------------------

By default, no ACL is configured for a VPC. If a network ACL is associated with a VPC, check the ACL rules.

#. Check whether the subnet of the ECS has been associated with a network ACL.

   If an ACL name is displayed, the network ACL has been associated with the ECS.

#. Click the ACL name to view its status.

#. If the network ACL is enabled, add an ICMP rule to allow traffic.

   .. note::

      The default network ACL rule denies all incoming and outgoing packets. If a network ACL is disabled, the default rule is still effective.

Checking Whether the Network Is Functional
------------------------------------------

#. Use another ECS in the same region to check whether the local network is functional.

   Use another ECS in the same region to ping the affected EIP. If the EIP can be pinged, the VPC is functional. In such a case, rectify the local network fault and ping the affected EIP again.

#. Check whether the link is accessible.

   A ping failure is caused by packet loss or long delay, which may be caused by link congestion, link node faults, or heavy load on the ECS.

Checking the ECS Route Configuration If Multiple NICs Are Used
--------------------------------------------------------------

Generally, the default route of an OS will preferentially select the primary NIC. If an extension NIC is selected in a route and the network malfunctions, this issue is typically caused by incorrect route configuration.

-  If the ECS has multiple NICs, check whether the default route is available.

   #. Log in to the ECS and run the following command to check whether the default route is available:

      **ip route**

      .. figure:: /_static/images/en-us_image_0250105611.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 5** Default route

   #. If the route is unavailable, run the following command to add it:

      **ip route add default via XXXX dev eth0**

      .. note::

         In the preceding command, *XXXX* specifies a gateway IP address.

-  If the ECS has multiple NICs and the EIP is bound to an extension NIC, configure policy routing on the ECS for network communication with the extension NIC.



.. |image1| image:: /_static/images/en-us_image_0210779229.png

