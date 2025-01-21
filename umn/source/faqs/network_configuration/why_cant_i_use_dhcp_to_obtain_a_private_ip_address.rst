:original_name: en-us_topic_0105130173.html

.. _en-us_topic_0105130173:

Why Can't I Use DHCP to Obtain a Private IP Address?
====================================================

Symptom
-------

You attempt to use DHCP to obtain a private IP address, but you cannot obtain the IP address.

-  For Linux, a private IP address cannot be assigned.
-  For Windows, a private IP address is changed to an IP address in the 169.254 network segment, which is different from the private IP address displayed on the ECS console.

.. note::

   You are advised to use a public image to create an ECS. All public images support DHCP continuous discovery mode.

Solution (Linux)
----------------

The following uses CentOS 7.2 as an example. For solutions about other OSs, see the corresponding help documentation.

#. Log in to the ECS and run the following command:

   **ps -ef \| grep dhclient**

#. If the dhclient process does not exist, restart the NIC or run any of the following commands to initiate a DHCP request:

   **dhclient eth0**, **ifdown eth0 + ifup eth0**, or **dhcpcd eth0**

#. If the DHCP client does not send any requests for a long time, for example, the issue recurs after the NIC is restarted, do the following:

   a. Run the following command to configure a static IP:

      **vi /etc/sysconfig/network-scripts/ifcfg-eth0**

      .. code-block::

         BOOTPROTO=static
         IPADDR=192.168.1.100 #IP address (modified)
         NETMASK=255.255.255.0 #Mask (modified)
         GATEWAY=192.168.1.1 #Gateway IP address (modified)

   b. Restart the ECS to make the network settings take effect.

   c. Select an image in which DHCP runs stably.

#. If the fault persists, obtain the messages in **/var/log/messages** on the affected ECS, use the MAC address of the affected NIC to filter the desired log, and check whether there is any process that prevents DHCP from obtaining an IP address.

#. If the fault persists, contact technical support.

Solution (Windows)
------------------

The following uses Windows 2012 as an example. For solutions about other OSs, see the corresponding help documentation.

#. Right-click a local area connection and choose **Disable** from the shortcut menu. Then, choose **Enable**.

   |image1|

#. If the DHCP client does not send any requests for a long time, for example, the issue recurs after the NIC is restarted, do the following:

   a. Right-click **Local Area Connection** and choose **Properties** from the shortcut menu.

   b. In the displayed dialog box, select **Internet Protocol Version 4 (TCP/IPv4)**, click **Properties**, and modify parameter settings.

      |image2|

   c. Restart the ECS to make the network settings take effect.

#. If the fault persists, contact technical support.

.. |image1| image:: /_static/images/en-us_image_0000001377299565.png
.. |image2| image:: /_static/images/en-us_image_0000001377418737.png
