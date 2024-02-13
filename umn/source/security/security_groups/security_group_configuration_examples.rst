:original_name: en-us_topic_0140323152.html

.. _en-us_topic_0140323152:

Security Group Configuration Examples
=====================================

Here are some common security group configuration examples for different scenarios, including remote login to ECSs, website access, and internal communication between instances in different security groups.

Generally, a security group denies all external requests by default. You need to add inbound rules to a security group based on the whitelist principle to allow specific external requests to access instances in the security group.

-  :ref:`Remotely Logging In to an ECS from a Local Server <en-us_topic_0140323152__en-us_topic_0118534011_section14933617154810>`
-  :ref:`Remotely Connecting to an ECS from a Local Server to Upload or Download Files <en-us_topic_0140323152__en-us_topic_0118534011_section8685162114185>`
-  :ref:`Setting Up a Website on an ECS to Provide Services Externally <en-us_topic_0140323152__en-us_topic_0118534011_section316061115481>`
-  :ref:`Using ping Command to Verify Network Connectivity <en-us_topic_0140323152__en-us_topic_0118534011_section29561427142511>`
-  :ref:`Enabling ECSs In Different Security Groups to Communicate Through an Internal Network <en-us_topic_0140323152__en-us_topic_0118534011_section094514632817>`
-  :ref:`ECS Providing Database Access Service <en-us_topic_0140323152__en-us_topic_0118534011_section7465183583515>`
-  :ref:`Allowing ECSs to Access Only Specific External Websites <en-us_topic_0140323152__en-us_topic_0118534011_section949023514612>`

By default, all outbound rules of a security group allow all requests from instances in the security group to access external networks. :ref:`Table 1 <en-us_topic_0140323152__en-us_topic_0118534011_table102261597217>` lists the rules.

.. _en-us_topic_0140323152__en-us_topic_0118534011_table102261597217:

.. table:: **Table 1** Default outbound rules in a security group

   +-----------+------+-----------------+-------------+-------------------------------------------------------------------------------------------------+
   | Direction | Type | Protocol & Port | Destination | Description                                                                                     |
   +===========+======+=================+=============+=================================================================================================+
   | Outbound  | IPv4 | All             | 0.0.0.0/0   | This rule allows access from instances in the security group to any IPv4 address over any port. |
   +-----------+------+-----------------+-------------+-------------------------------------------------------------------------------------------------+
   | Outbound  | IPv6 | All             | ::/0        | This rule allows access from instances in the security group to any IPv6 address over any port. |
   +-----------+------+-----------------+-------------+-------------------------------------------------------------------------------------------------+

.. _en-us_topic_0140323152__en-us_topic_0118534011_section14933617154810:

Remotely Logging In to an ECS from a Local Server
-------------------------------------------------

A security group denies all external requests by default. To remotely log in to an ECS from a local server, add an inbound security group rule based on the OS running on the ECS.

-  To remotely log in to a Linux ECS using SSH, enable the SSH (22) port. For details, see :ref:`Table 2 <en-us_topic_0140323152__en-us_topic_0118534011_table20321112045011>`.

-  To remotely log in to a Windows ECS using RDP, enable the RDP (3389) port. For details, see :ref:`Table 3 <en-us_topic_0140323152__en-us_topic_0118534011_table1579314381815>`.

   .. _en-us_topic_0140323152__en-us_topic_0118534011_table20321112045011:

   .. table:: **Table 2** Remotely logging in to a Linux ECS using SSH

      ========= ==== =============== =====================
      Direction Type Protocol & Port Source
      ========= ==== =============== =====================
      Inbound   IPv4 TCP: 22         IP address: 0.0.0.0/0
      ========= ==== =============== =====================

   .. _en-us_topic_0140323152__en-us_topic_0118534011_table1579314381815:

   .. table:: **Table 3** Remotely logging in to a Windows ECS using RDP

      ========= ==== =============== =====================
      Direction Type Protocol & Port Source
      ========= ==== =============== =====================
      Inbound   IPv4 TCP: 3389       IP address: 0.0.0.0/0
      ========= ==== =============== =====================

   .. important::

      If the source is set to 0.0.0.0/0, remotely logging in to the ECS through any IP address is allowed. To ensure security, set the source to a specific IP address based on service requirements. For details about the configuration example, see :ref:`Table 4 <en-us_topic_0140323152__en-us_topic_0118534011_table1919016251434>`.

   .. _en-us_topic_0140323152__en-us_topic_0118534011_table1919016251434:

   .. table:: **Table 4** Remotely logging in to an ECS using a specified IP address

      =========== ========= ==== =============== ==========================
      ECS Type    Direction Type Protocol & Port Source
      =========== ========= ==== =============== ==========================
      Linux ECS   Inbound   IPv4 TCP: 22         IP address: 192.168.0.0/24
      Windows ECS Inbound   IPv4 TCP: 3389       IP address: 10.10.0.0/24
      =========== ========= ==== =============== ==========================

.. _en-us_topic_0140323152__en-us_topic_0118534011_section8685162114185:

Remotely Connecting to an ECS from a Local Server to Upload or Download Files
-----------------------------------------------------------------------------

By default, a security group denies all external requests. If you need to remotely connect to an ECS from a local server to upload or download files, you need to enable FTP ports 20 and 21.

.. table:: **Table 5** Remotely connecting to an ECS from a local server to upload or download files

   ========= ==== =============== =====================
   Direction Type Protocol & Port Source
   ========= ==== =============== =====================
   Inbound   IPv4 TCP: 20-21      IP address: 0.0.0.0/0
   ========= ==== =============== =====================

.. important::

   You must first install the FTP server program on the ECSs and check whether ports 20 and 21 are working properly.

.. _en-us_topic_0140323152__en-us_topic_0118534011_section316061115481:

Setting Up a Website on an ECS to Provide Services Externally
-------------------------------------------------------------

A security group denies all external requests by default. If you have set up a website on an ECS that can be accessed externally, you need to add an inbound rule to the ECS security group to allow access over specific ports, such as HTTP (80) and HTTPS (443).

.. table:: **Table 6** Setting up a website on an ECS to provide services externally

   ========= ==== =============== =====================
   Direction Type Protocol & Port Source
   ========= ==== =============== =====================
   Inbound   IPv4 TCP: 80         IP address: 0.0.0.0/0
   Inbound   IPv4 TCP: 443        IP address: 0.0.0.0/0
   ========= ==== =============== =====================

.. _en-us_topic_0140323152__en-us_topic_0118534011_section29561427142511:

Using **ping** Command to Verify Network Connectivity
-----------------------------------------------------

By default, a security group denies all external requests. If you need to run the **ping** command on an ECS to verify network connectivity, add an inbound rule to the ECS security group to allow access over the ICMP port.

.. table:: **Table 7** Using **ping** command to verify network connectivity

   ========= ==== =============== =====================
   Direction Type Protocol & Port Source
   ========= ==== =============== =====================
   Inbound   IPv4 ICMP: All       IP address: 0.0.0.0/0
   Inbound   IPv6 ICMP: All       IP address: ::/0
   ========= ==== =============== =====================

.. _en-us_topic_0140323152__en-us_topic_0118534011_section094514632817:

Enabling ECSs In Different Security Groups to Communicate Through an Internal Network
-------------------------------------------------------------------------------------

ECSs in the same VPC but associated with different security groups cannot communicate with each other. If you want to share data between ECSs in a VPC, for example, ECSs in security group sg-A need to access MySQL databases in security group sg-B, you need to add an inbound rule to security group sg-B to allow access from ECSs in security group sg-A over MySQL port 3306.

.. table:: **Table 8** Enabling instances in different security groups to communicate through an internal network

   ========= ==== =============== ====================
   Direction Type Protocol & Port Source
   ========= ==== =============== ====================
   Inbound   IPv4 TCP: 3306       Security group: sg-A
   ========= ==== =============== ====================

.. _en-us_topic_0140323152__en-us_topic_0118534011_section7465183583515:

ECS Providing Database Access Service
-------------------------------------

A security group denies all external requests by default. If you have deployed the database service on an ECS and need to allow other ECSs to access the database service through an internal network, you need to add an inbound rule to the security group of the ECS with the database service deployed to allow access over ports, for example, MySQL (3306), Oracle (1521), MS SQL (1433), PostgreSQL (5432) and Redis (6379).

.. table:: **Table 9** ECS providing database access service

   +-----------+------+-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Direction | Type | Protocol & Port | Source                     | Description                                                                                                                   |
   +===========+======+=================+============================+===============================================================================================================================+
   | Inbound   | IPv4 | TCP: 3306       | Security group: sg-A       | This rule allows ECSs in security group sg-A to access the MySQL database service.                                            |
   +-----------+------+-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv4 | TCP: 1521       | Security group: sg-B       | This rule allows ECSs in security group sg-B to access the Oracle database service.                                           |
   +-----------+------+-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv4 | TCP: 1433       | IP address: 172.16.3.21/32 | This rule allows the ECS whose private IP address is 172.16.3.21 to access the MS SQL database service.                       |
   +-----------+------+-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv4 | TCP: 5432       | IP address: 192.168.0.0/24 | This rule allows ECSs whose private IP addresses are in the 192.168.0.0/24 network to access the PostgreSQL database service. |
   +-----------+------+-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+

.. important::

   In this example, the source is for reference only. Set the source address based on actual requirements.

.. _en-us_topic_0140323152__en-us_topic_0118534011_section949023514612:

Allowing ECSs to Access Only Specific External Websites
-------------------------------------------------------

By default, a security group allows all outbound traffic. :ref:`Table 11 <en-us_topic_0140323152__en-us_topic_0118534011_table5759161135518>` lists the default rules. If you want to allow ECSs to access only specific websites, configure the security groups of the ECSs as follows:

#. First, add outbound rules to allow traffic over specific ports and to specific IP addresses.

   .. table:: **Table 10** Enabling instances in different security groups to communicate through an internal network

      ========= ==== =============== =========================
      Direction Type Protocol & Port Source
      ========= ==== =============== =========================
      Outbound  IPv4 TCP: 80         IP address: 132.15.XX.XX
      Outbound  IPv4 TCP: 443        IP address: 145.117.XX.XX
      ========= ==== =============== =========================

#. Then, delete the original outbound rules that allow all traffic shown in :ref:`Table 11 <en-us_topic_0140323152__en-us_topic_0118534011_table5759161135518>`.

   .. _en-us_topic_0140323152__en-us_topic_0118534011_table5759161135518:

   .. table:: **Table 11** Default outbound rules in a security group

      +-----------+------+-----------------+-------------+-------------------------------------------------------------------------------------------------+
      | Direction | Type | Protocol & Port | Destination | Description                                                                                     |
      +===========+======+=================+=============+=================================================================================================+
      | Outbound  | IPv4 | All             | 0.0.0.0/0   | This rule allows access from instances in the security group to any IPv4 address over any port. |
      +-----------+------+-----------------+-------------+-------------------------------------------------------------------------------------------------+
      | Outbound  | IPv6 | All             | ::/0        | This rule allows access from instances in the security group to any IPv6 address over any port. |
      +-----------+------+-----------------+-------------+-------------------------------------------------------------------------------------------------+
