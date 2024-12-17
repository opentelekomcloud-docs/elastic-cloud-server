:original_name: en-us_topic_0027157850.html

.. _en-us_topic_0027157850:

Enabling Internet Connectivity for an ECS Without an EIP Bound
==============================================================

Scenarios
---------

To ensure platform security and conserve EIPs, EIPs are only assigned to specified ECSs. The ECSs that have not EIPs bound cannot access the Internet directly. If these ECSs need to access the Internet (for example, to perform a software upgrade or install a patch), you can select an ECS that has an EIP bound to function as a proxy ECS to provide an access channel for these ECSs.

.. note::

   NAT Gateway is recommended, which provides both the SNAT and DNAT functions for your ECSs in a VPC and allows the ECSs to access or provide services accessible from the Internet. For details, see `NAT Gateway <https://docs.otc.t-systems.com/usermanual/nat/nat_pro_0000.html>`__.

Prerequisites
-------------

-  A proxy ECS with an EIP bound is available.
-  The IP address of the proxy ECS is in the same network and same security group as the ECSs that need to access the Internet.

Using a Linux Proxy ECS
-----------------------

.. note::

   Prerequisites for this solution:

   -  A proxy ECS with an EIP bound is available.
   -  The IP address of the proxy ECS is in the same network and same security group as the ECSs that need to access the Internet.

The following uses CentOS 7.9 as an example. The operations apply to CentOS 7.9 and earlier versions.

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the search box above the upper right corner of the ECS list, enter the proxy ECS name for search.

#. Click the name of the proxy ECS. The page providing details about the ECS is displayed.

#. On the **Network Interfaces** tab, click |image2|. Then, disable **Source/Destination Check**.


   .. figure:: /_static/images/en-us_image_0000001659671776.png
      :alt: **Figure 1** Disabling source/destination check

      **Figure 1** Disabling source/destination check

   By default, the source/destination check function is enabled. When this function is enabled, the system checks whether source IP addresses contained in the packets sent by ECSs are correct. If the IP addresses are incorrect, the system does not allow the ECSs to send the packets. This mechanism prevents packet spoofing, thereby improving system security. However, this mechanism prevents the packet sender from receiving returned packets. Therefore, disable the source/destination check.

#. Log in to the proxy ECS.

   For more details, see :ref:`Login Overview (Linux) <en-us_topic_0013771089>`.

#. Check whether the proxy ECS can access the Internet.

   **ping www.google.com**

   The proxy ECS can access the Internet if information similar to the following is displayed:

   .. code-block::

      64 bytes from 220.181.111.148: icmp_seq=1 ttl=51 time=9.34 ms
      64 bytes from 220.181.111.148: icmp_seq=2 ttl=51 time=9.11 ms
      64 bytes from 220.181.111.148: icmp_seq=3 ttl=51 time=8.99 ms

#. (Optional) Install the iptables service and set the automatic startup of iptables.

   Perform this step only for ECSs running CentOS 7.x.

   **yum install iptables-services -y**

   **systemctl start** **iptables**

   **systemctl enable iptables**

#. Check whether IP forwarding is enabled on the proxy ECS.

   **cat /proc/sys/net/ipv4/ip_forward**

   -  If **0** (disabled) is displayed, go to :ref:`11 <en-us_topic_0027157850__li51820417113959>`.
   -  If **1** (enabled) is displayed, go to :ref:`16 <en-us_topic_0027157850__li46434272315>`.

#. .. _en-us_topic_0027157850__li51820417113959:

   Open the IP forwarding configuration file in the vi editor.

   **vi /etc/sysctl.conf**

#. Press **i** to enter editing mode.

#. Change the parameter value.

   Set the **net.ipv4.ip_forward** value to **1**.

   .. note::

      If the **sysctl.conf** file does not contain the **net.ipv4.ip_forward** parameter, run the following command to add it:

      **echo net.ipv4.ip_forward=1 >> /etc/sysctl.conf**

#. Press **Esc**, type **:wq**, and press **Enter**.

   The system saves the configurations and exits the vi editor.

#. Apply the change.

   **sysctl -p /etc/sysctl.conf**

#. .. _en-us_topic_0027157850__li46434272315:

   Delete the original iptables rules.

   **iptables -F**

#. .. _en-us_topic_0027157850__li49419571113959:

   Configure source network address translation (SNAT) to enable ECSs in the same network segment to access the Internet through the proxy ECS.

   **iptables -t nat -A POSTROUTING -o eth0 -s** *subnet/netmask-bits* **-j SNAT --to** *nat-instance-ip*

   For example, if the proxy ECS is in network segment 192.168.125.0, the subnet mask has 24 bits, and the private IP address is 192.168.125.4, run the following command:

   **iptables -t nat -A POSTROUTING -o eth0 -s** *192.168.125.0/24* **-j SNAT --to 192.168.125.4**

   .. note::

      To retain the preceding configuration even after the ECS is restarted, run the **vi /etc/rc.local** command to edit the **rc.local** file. Specifically, copy the rule described in step :ref:`17 <en-us_topic_0027157850__li49419571113959>` into **rc.local**, press **Esc** to exit Insert mode, and enter **:wq** to save the settings and exit.

#. Save the iptables configuration and set the automatic startup of iptables.

   **service iptables save**

   **chkconfig iptables on**

#. Check whether SNAT has been configured.

   **iptables -t nat --list**

   SNAT has been configured if information similar to :ref:`Figure 2 <en-us_topic_0027157850__fig27598108113959>` is displayed.

   .. _en-us_topic_0027157850__fig27598108113959:

   .. figure:: /_static/images/en-us_image_0027174005.png
      :alt: **Figure 2** Successful SNAT configuration

      **Figure 2** Successful SNAT configuration

#. Add a route.

   a. Log in to the management console.
   b. Click |image3| in the upper left corner and select your region and project.
   c. Under **Network**, click **Virtual Private Cloud**.
   d. Choose **Route Tables** in the left navigation pane. In the route table list, click a target route table. On the displayed page, click **Add Route**.
   e. Set route information on the displayed page.

      -  **Destination**: indicates the destination network segment. The default value is **0.0.0.0/0**.

      -  **Next Hop**: indicates the private IP address of the proxy ECS.

         You can obtain the private IP address of the ECS on the **Elastic Cloud Server** page.

#. Delete the added iptables rules as needed.

   **iptables -t nat -D POSTROUTING -o eth0 -s** *subnet/netmask-bits* **-j SNAT --to** *nat-instance-ip*

   For example, if the proxy ECS is in network segment 192.168.125.0, the subnet mask has 24 bits, and the private IP address is 192.168.125.4, run the following command:

   **iptables -t nat -D POSTROUTING -o eth0 -s 192.168.125.0/24 -j SNAT --to 192.168.125.4**

.. |image1| image:: /_static/images/en-us_image_0210779229.png
.. |image2| image:: /_static/images/en-us_image_0128851717.png
.. |image3| image:: /_static/images/en-us_image_0210779229.png
