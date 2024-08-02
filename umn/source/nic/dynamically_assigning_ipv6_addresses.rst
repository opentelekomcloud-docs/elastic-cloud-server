:original_name: en-us_topic_0140963099.html

.. _en-us_topic_0140963099:

Dynamically Assigning IPv6 Addresses
====================================

Scenarios
---------

IPv6 addresses are used to deal with IPv4 address exhaustion. If an ECS uses an IPv4 address, the ECS can run in dual-stack mode after IPv6 is enabled for it. Then, the ECS will have two IP addresses to access the intranet and Internet: an IPv4 address and an IPv6 address.

In some cases, an ECS cannot dynamically acquire an IPv6 address even if it meets all the requirements in :ref:`Constraints <en-us_topic_0140963099__en-us_topic_0129883696_section196731247131618>`. You need to configure the ECS to dynamically acquire IPv6 addresses. For public images:

-  By default, dynamic IPv6 address assignment is enabled for Windows public images. You do not need to configure it. The operations in :ref:`Windows Server 2012 <en-us_topic_0140963099__en-us_topic_0129883696_section0206266172>` are for your reference only.
-  Before enabling dynamic IPv6 address assignment for a Linux public image, check whether IPv6 has been enabled and then whether dynamic IPv6 address assignment has been enabled. Currently, IPv6 is enabled for all Linux public images.

.. _en-us_topic_0140963099__en-us_topic_0129883696_section196731247131618:

Constraints
-----------

-  Ensure that IPv6 has been enabled on the subnet where the ECS works.

   For details about how to enable IPv6 on a subnet, see :ref:`Enabling IPv6 on the Subnet Where the ECS Works <en-us_topic_0140963099__en-us_topic_0129883696_section1967161905116>`.

-  Ensure that the ECS flavor supports IPv6. Currently, S3, C4, and M4 ECSs support IPv6.

-  Ensure that **Self-assigned IPv6 address** is selected during ECS creation.

-  After the ECS is started, its hot-swappable NICs cannot automatically acquire IPv6 addresses.
-  Only ECSs can work in dual-stack mode and BMSs cannot.
-  Only one IPv6 address can be bound to a NIC.

Procedure
---------

-  Windows: Windows Server 2012 is used as an example to describe how to enable dynamic assignment of IPv6 addresses in Windows.

-  Linux: Dynamic assignment of IPv6 addresses can be enabled automatically (recommended) or manually.

   If a private image created from a CentOS 6.x or Debian ECS with automatic IPv6 address assignment enabled is used to create an ECS in an environment that does not support IPv6, the ECS may start slow because of IPv6 address assignment timeout. You can set the timeout duration for assigning IPv6 addresses by referring to :ref:`Setting the Timeout Duration for IPv6 Address Assignment <en-us_topic_0140963099__en-us_topic_0129883696_section814912855814>`.

.. table:: **Table 1** Enabling dynamic assignment of IPv6 addresses for different OSs

   +---------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS                  | Automatically/Manually Enabling | Reference                                                                                                                                       |
   +=====================+=================================+=================================================================================================================================================+
   | Windows Server 2012 | Automatically                   | :ref:`Windows Server 2012 <en-us_topic_0140963099__en-us_topic_0129883696_section0206266172>`                                                   |
   +---------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Linux               | Automatically (recommended)     | :ref:`Linux (Automatically Enabling Dynamic Assignment of IPv6 Addresses) <en-us_topic_0140963099__en-us_topic_0129883696_section106971627556>` |
   +---------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Linux               | Manually                        | :ref:`Linux (Manually Enabling Dynamic Assignment of IPv6 Addresses) <en-us_topic_0140963099__en-us_topic_0129883696_section7426172116710>`     |
   +---------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0140963099__en-us_topic_0129883696_section1967161905116:

Enabling IPv6 on the Subnet Where the ECS Works
-----------------------------------------------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Under **Computing**, click **Elastic Cloud Server**.

4. Click the target ECS to go to the detail page.

5. In the **ECS Information** area, click the VPC name.

6. Click the number in the **Subnets** column.

   The **Subnets** page is displayed.

7. In the subnet list, locate the target subnet and click its name.

   The subnet details page is displayed.

8. In the **Subnet Information** area, click **Enable** for **IPv6 CIDR Block**.

9. Click **Yes**.

.. _en-us_topic_0140963099__en-us_topic_0129883696_section0206266172:

Windows Server 2012
-------------------

#. .. _en-us_topic_0140963099__en-us_topic_0129883696_li64771254152011:

   Check whether IPv6 is enabled for the ECS.

   Run the following command in the CMD window to check it:

   **ipconfig**

   -  If an IPv6 address and a link-local IPv6 address are displayed, IPv6 is enabled and dynamic IPv6 assignment is also enabled.

      .. _en-us_topic_0140963099__en-us_topic_0129883696_fig9159201613216:

      .. figure:: /_static/images/en-us_image_0000001723651650.png
         :alt: **Figure 1** Querying the IPv6 address

         **Figure 1** Querying the IPv6 address

   -  If only a link-local IPv6 address is displayed, IPv6 is enabled but dynamic IPv6 assignment is not enabled. Go to :ref:`2 <en-us_topic_0140963099__en-us_topic_0129883696_li2024825592115>`.


      .. figure:: /_static/images/en-us_image_0000001723492302.png
         :alt: **Figure 2** Link-local IPv6 address

         **Figure 2** Link-local IPv6 address

   -  If neither an IPv6 address nor link-local IPv6 address is displayed, IPv6 is disabled. Go to :ref:`3 <en-us_topic_0140963099__en-us_topic_0129883696_li35521349132511>`.


      .. figure:: /_static/images/en-us_image_0000001771211453.png
         :alt: **Figure 3** IPv6 disabled

         **Figure 3** IPv6 disabled

      .. note::

         By default, dynamic IPv6 address assignment is enabled for Windows public images, as shown in :ref:`Figure 1 <en-us_topic_0140963099__en-us_topic_0129883696_fig9159201613216>`. No additional configuration is required.

#. .. _en-us_topic_0140963099__en-us_topic_0129883696_li2024825592115:

   Enable dynamic IPv6 address assignment.

   a. Choose **Start** > **Control Panel**.

   b. Click **Network and Sharing Center**.

   c. Click the Ethernet connection.


      .. figure:: /_static/images/en-us_image_0000001771292121.png
         :alt: **Figure 4** Ethernet connection

         **Figure 4** Ethernet connection

   d. In the **Ethernet Status** dialog box, click **Properties** in the lower left corner.

   e. Select **Internet Protocol Version 6 (TCP/IPv6)** and click **OK**.


      .. figure:: /_static/images/en-us_image_0000001723651658.png
         :alt: **Figure 5** Configuring dynamic IPv6 address assignment

         **Figure 5** Configuring dynamic IPv6 address assignment

   f. Perform :ref:`1 <en-us_topic_0140963099__en-us_topic_0129883696_li64771254152011>` to check whether dynamic IPv6 address assignment is enabled.

#. .. _en-us_topic_0140963099__en-us_topic_0129883696_li35521349132511:

   Enable and configure IPv6.

   a. In the **Internet Protocol Version 6 (TCP/IPv6) Properties** dialog box, configure an IPv6 address and a DNS server address.

      -  **IPv6 address**: IPv6 address allocated during ECS creation. Obtain the value from the ECS list on the console.
      -  **Subnet prefix length**: **64**
      -  **Preferred DNS server**: **240c::6666** (recommended)


      .. figure:: /_static/images/en-us_image_0000001723492306.png
         :alt: **Figure 6** Configuring an IPv6 address and a DNS server address

         **Figure 6** Configuring an IPv6 address and a DNS server address

   b. (Optional) Run the following command depending on your ECS OS.

      For Windows Server 2012, run the following command in PowerShell or CMD:

      **Set-NetIPv6Protocol -RandomizeIdentifiers disabled**

   c. Perform :ref:`1 <en-us_topic_0140963099__en-us_topic_0129883696_li64771254152011>` to check whether dynamic IPv6 address assignment is enabled.

.. _en-us_topic_0140963099__en-us_topic_0129883696_section106971627556:

Linux (Automatically Enabling Dynamic Assignment of IPv6 Addresses)
-------------------------------------------------------------------

The **ipv6-setup-**\ *xxx* tool can be used to enable Linux OSs to automatically acquire IPv6 addresses. *xxx* indicates a tool, which can be rhel or debian.

You can also enable dynamic IPv6 address assignment by following the instructions in :ref:`Linux (Manually Enabling Dynamic Assignment of IPv6 Addresses) <en-us_topic_0140963099__en-us_topic_0129883696_section7426172116710>`.

.. caution::

   -  When you run **ipv6-setup-**\ *xxx*, the network service will be automatically restarted. As a result, the network is temporarily disconnected.
   -  If a private image created from a CentOS 6.x or Debian ECS with automatic IPv6 address assignment enabled is used to create an ECS in an environment that does not support IPv6, the ECS may start slow because of IPv6 address assignment timeout. Set the timeout duration for assigning IPv6 addresses to 30s by referring to :ref:`Setting the Timeout Duration for IPv6 Address Assignment <en-us_topic_0140963099__en-us_topic_0129883696_section814912855814>` and try to create a new private image again.

#. Run the following command to check whether IPv6 is enabled for the ECS:

   **ip addr**

   -  If only an IPv4 address is displayed, IPv6 is disabled. Enable it by referring to :ref:`Setting the Timeout Duration for IPv6 Address Assignment <en-us_topic_0140963099__en-us_topic_0129883696_section814912855814>`.


      .. figure:: /_static/images/en-us_image_0000001723492314.png
         :alt: **Figure 7** IPv6 disabled

         **Figure 7** IPv6 disabled

   -  If a link-local address (starting with fe80) is displayed, IPv6 is enabled but dynamic assignment of IPv6 addresses is not enabled.

      .. _en-us_topic_0140963099__en-us_topic_0129883696_en-us_topic_0129883696_fig1176932510308:

      .. figure:: /_static/images/en-us_image_0000001771211465.png
         :alt: **Figure 8** IPv6 enabled

         **Figure 8** IPv6 enabled

   -  If the following address is displayed, IPv6 is enabled and an IPv6 address has been assigned:


      .. figure:: /_static/images/en-us_image_0000001771292133.png
         :alt: **Figure 9** IPv6 enabled and an IPv6 address assigned

         **Figure 9** IPv6 enabled and an IPv6 address assigned

   .. note::

      IPv6 is enabled for Linux public images by default, as shown in :ref:`Figure 8 <en-us_topic_0140963099__en-us_topic_0129883696_en-us_topic_0129883696_fig1176932510308>`.

#. Enable IPv6 for the ECS.

   a. Run the following command to check whether IPv6 is enabled for the kernel:

      **sysctl -a \| grep ipv6**

      -  If a command output is displayed, IPv6 is enabled.
      -  If no information is displayed, IPv6 is disabled. Go to :ref:`2.b <en-us_topic_0140963099__en-us_topic_0129883696_li193875248395>` to load the IPv6 module.

   b. Run the following command to load the IPv6 module:

      **modprobe ipv6**

   c. Add the following content to the **/etc/sysctl.conf** file:

      **net.ipv6.conf.all.disable_ipv6=0**

   d. Save the configuration and exit. Then, run the following command to load the configuration:

      **sysctl -p**

#. Enable dynamic IPv6 address assignment for the ECS.

   a. Download **ipv6-setup-rhel** or **ipv6-setup-debian** with a required version and upload it to the target ECS.

      **ipv6-setup-**\ *xxx* modifies the configuration file of a NIC to enable dynamic IPv6 address assignment or adds such a configuration file for a NIC, and then restarts the NIC or network service.

      Contact the administrator to obtain the download paths of **ipv6-setup-rhel** and **ipv6-setup-debian**.

   b. Run the following command to make **ipv6-setup-**\ *xxx* executable:

      **chmod** **+x** **ipv6-setup-**\ *xxx*

   c. Run the following command to enable dynamic IPv6 address assignment for a NIC:

      **./ipv6-setup-**\ *xxx* **--dev** [*dev*]

      Example:

      **./ipv6-setup-**\ *xxx* **--dev eth0**

      .. note::

         -  To enable dynamic IPv6 address assignment for all NICs, run the **./ipv6-setup-**\ *xxx* command.
         -  To learn how to use **ipv6-setup-**\ *xxx*, run the **./ipv6-setup-**\ *xxx* **--help** command.

.. _en-us_topic_0140963099__en-us_topic_0129883696_section7426172116710:

Linux (Manually Enabling Dynamic Assignment of IPv6 Addresses)
--------------------------------------------------------------

.. caution::

   If a private image created from a CentOS 6.x or Debian ECS with automatic IPv6 address assignment enabled is used to create an ECS in an environment that does not support IPv6, the ECS may start slow because of IPv6 address assignment timeout. Set the timeout duration for assigning IPv6 addresses to 30s by referring to :ref:`Setting the Timeout Duration for IPv6 Address Assignment <en-us_topic_0140963099__en-us_topic_0129883696_section814912855814>` and try to create a new private image again.

#. .. _en-us_topic_0140963099__en-us_topic_0129883696_li967053013012:

   Run the following command to check whether IPv6 is enabled for the ECS:

   **ip addr**

   -  If only an IPv4 address is displayed, IPv6 is disabled. Enable it by referring to :ref:`2 <en-us_topic_0140963099__en-us_topic_0129883696_li615511220439>`.


      .. figure:: /_static/images/en-us_image_0000001723651670.png
         :alt: **Figure 10** IPv6 disabled

         **Figure 10** IPv6 disabled

   -  If a link-local address (starting with fe80) is displayed, IPv6 is enabled but dynamic assignment of IPv6 addresses is not enabled.

      .. _en-us_topic_0140963099__en-us_topic_0129883696_fig1176932510308:

      .. figure:: /_static/images/en-us_image_0000001723492318.png
         :alt: **Figure 11** IPv6 enabled

         **Figure 11** IPv6 enabled

   -  If the following address is displayed, IPv6 is enabled and an IPv6 address has been assigned:


      .. figure:: /_static/images/en-us_image_0000001771211469.png
         :alt: **Figure 12** IPv6 enabled and an IPv6 address assigned

         **Figure 12** IPv6 enabled and an IPv6 address assigned

   .. note::

      IPv6 is enabled for Linux public images by default, as shown in :ref:`Figure 11 <en-us_topic_0140963099__en-us_topic_0129883696_fig1176932510308>`.

#. .. _en-us_topic_0140963099__en-us_topic_0129883696_li615511220439:

   Enable IPv6 for the ECS.

   a. Run the following command to check whether IPv6 is enabled for the kernel:

      **sysctl -a \| grep ipv6**

      -  If a command output is displayed, IPv6 is enabled.
      -  If no information is displayed, IPv6 is disabled. Go to :ref:`2.b <en-us_topic_0140963099__en-us_topic_0129883696_li193875248395>` to load the IPv6 module.

   b. .. _en-us_topic_0140963099__en-us_topic_0129883696_li193875248395:

      Run the following command to load the IPv6 module:

      **modprobe ipv6**

   c. Add the following content to the **/etc/sysctl.conf** file:

      **net.ipv6.conf.all.disable_ipv6=0**

   d. Save the configuration and exit. Then, run the following command to load the configuration:

      **sysctl -p**

#. Enable dynamic IPv6 address assignment for the ECS.

   -  Ubuntu 18.04/20.04

      a. Run the following command to access **/etc/netpaln/**:

         **cd /etc/netplan**

      b. Run the following command to list the configuration file:

         **ls**


         .. figure:: /_static/images/en-us_image_0000001771292137.png
            :alt: **Figure 13** Configuration file name

            **Figure 13** Configuration file name

      c. Run the following command to edit the configuration file:

         **vi 01-network-manager-all.yaml**

      d. Append the following content to the configuration file (pay attention to the yaml syntax and text indentation):

         .. code-block::

            ethernets:
             eth0:
              dhcp6: true


         .. figure:: /_static/images/en-us_image_0000001723651674.png
            :alt: **Figure 14** Edited configuration file

            **Figure 14** Edited configuration file

         Save the changes and exit.

      e. Run the following command to make the changes take effect:

         **sudo netplan apply**

   -  Ubuntu 22.04

      a. Run the following command to access **/etc/netpaln/**:

         **cd /etc/netplan**

      b. Run the following command to list the configuration file:

         **ls**


         .. figure:: /_static/images/en-us_image_0000001723492322.png
            :alt: **Figure 15** Configuration file name

            **Figure 15** Configuration file name

      c. Run the following command to edit the configuration file:

         **vi 01-netcfg.yaml**

      d. Append the following content to the configuration file (pay attention to the yaml syntax and text indentation):

         .. code-block::

            ethernets:
             eth0:
              dhcp6: true


         .. figure:: /_static/images/en-us_image_0000001771211473.png
            :alt: **Figure 16** Edited configuration file

            **Figure 16** Edited configuration file

         Save the changes and exit.

      e. Run the following command to make the changes take effect:

         **sudo netplan apply**

   -  Debian

      a. Add the following content to the **/etc/network/interfaces** file:

         .. code-block::

            auto lo
            iface lo inet loopback
            auto eth0
            iface eth0 inet dhcp
            iface eth0 inet6 dhcp
                 pre-up sleep 3

      b. Add configurations for each NIC to the **/etc/network/interfaces** file. The following uses eth1 as an example:

         .. code-block::

            auto eth1
            iface eth1 inet dhcp
            iface eth1 inet6 dhcp
                 pre-up sleep 3

      c. Run the following command to restart the network service:

         **service networking restart**

         .. note::

            If no IPv6 address is assigned after the NICs are brought down and up, you can run this command to restart the network.

      d. Perform :ref:`1 <en-us_topic_0140963099__en-us_topic_0129883696_li967053013012>` to check whether dynamic IPv6 address assignment is enabled.

   -  CentOS, EulerOS, or Fedora

      a. Open the configuration file **/etc/sysconfig/network-scripts/ifcfg-eth0** of the primary NIC.

         Add the following configuration items to the file:

         .. code-block::

            IPV6INIT=yes
            DHCPV6C=yes

      b. Edit the **/etc/sysconfig/network** file to add or modify the following line:

         .. code-block::

            NETWORKING_IPV6=yes

      c. For an ECS running CentOS 6, you need to edit the configuration files of its extension NICs. For example, if the extension NIC is eth1, you need to edit **/etc/sysconfig/network-scripts/ifcfg-eth1**.

         Add the following configuration items to the file:

         .. code-block::

            IPV6INIT=yes
            DHCPV6C=yes

         In CentOS 6.3, dhcpv6-client requests are filtered by **ip6tables** by default. So, you also need to add a rule allowing the dhcpv6-client request to the **ip6tables** file.

         #. Run the following command to add the rule to **ip6tables**:

            **ip6tables -A INPUT -m state --state NEW -m udp -p udp --dport 546 -d fe80::/64 -j ACCEPT**

         #. Run the following command to save the rule in **ip6tables**:

            **service ip6tables save**


            .. figure:: /_static/images/en-us_image_0000001771292141.png
               :alt: **Figure 17** Example command

               **Figure 17** Example command

      d. (Optional) For CentOS 7/CentOS 8, change the IPv6 link-local address mode of extension NICs to EUI64.

         #. Run the following command to query the NIC information:

            **nmcli con**


            .. figure:: /_static/images/en-us_image_0000001723651678.png
               :alt: **Figure 18** Querying NIC information

               **Figure 18** Querying NIC information

         #. Run the following command to change the IPv6 link-local address mode of eth1 to EUI64:

            **nmcli con modify "**\ *Wired connection 1*\ **" ipv6.addr-gen-mode eui64**

            .. note::

               The NIC information varies depending on the CentOS series. In the command, *Wired connection 1* needs to be replaced with the value in the **NAME** column of the queried NIC information.

         #. Run the following commands to bring eth1 down and up:

            **ifdown eth1**

            **ifup eth1**

      e. Restart the network service.

         #. For CentOS 6, run the following command to restart the network service:

            **service network restart**

         #. For CentOS 7/EulerOS/Fedora, run the following command to restart the network service:

            **systemctl restart NetworkManager**

      f. Perform :ref:`1 <en-us_topic_0140963099__en-us_topic_0129883696_li967053013012>` to check whether dynamic IPv6 address assignment is enabled.

   -  SUSE, openSUSE, or CoreOS

      SUSE 11 SP4 does not support dynamic IPv6 address assignment.

      No additional configuration is required for SUSE 12 SP1 or SUSE 12 SP2.

      No additional configuration is required for openSUSE 13.2 or openSUSE 42.2.

      No additional configuration is required for CoreOS 10.10.5.

.. _en-us_topic_0140963099__en-us_topic_0129883696_section814912855814:

Setting the Timeout Duration for IPv6 Address Assignment
--------------------------------------------------------

After automatic IPv6 address assignment is configured on an ECS running CentOS 6.x or Debian, the ECS will be created as a private image. When this image is used to create an ECS in an environment that IPv6 is unavailable, the ECS may start slow because acquiring an IPv6 address times out. Before creating the private image, you can set the timeout duration for acquiring IPv6 addresses to 30s as follows:

-  CentOS 6.\ *x*:

   #. Run the following command to edit the **dhclient.conf** file:

      **vi /etc/dhcp/dhclient.conf**

   #. Press **i** to enter editing mode and add the timeout attribute to the file.

      .. code-block::

         timeout  30;

   #. Enter **:wq** to save the settings and exit.

-  Debian 7.5:

   #. Run the following command to edit the **networking** file:

      **vi /etc/init.d/networking**

   2. Press **i** to enter editing mode and add the timeout attribute.


      .. figure:: /_static/images/en-us_image_0000001723492326.png
         :alt: **Figure 19** Modification 1

         **Figure 19** Modification 1


      .. figure:: /_static/images/en-us_image_0000001771211517.png
         :alt: **Figure 20** Modification 2

         **Figure 20** Modification 2

-  Debian 8.2.0/8.8.0

   #. Run the following command to edit the **network-pre.conf** file:

      **vi /lib/systemd/system/networking.service.d/network-pre.conf**

   #. Press *i* to enter editing mode and add the timeout attribute to the file.

      .. code-block::

         [Service]
         TimeoutStartSec=30

-  Debian 9.0

   #. Run the following command to edit the **networking.service** file:

      **vi /etc/system/system/network-online.target.wants/networking.service**

   #. Press **i** to enter editing mode and change **TimeoutStartSec=5min** to **TimeoutStartSec=30**.

.. |image1| image:: /_static/images/en-us_image_0000001771211441.png
