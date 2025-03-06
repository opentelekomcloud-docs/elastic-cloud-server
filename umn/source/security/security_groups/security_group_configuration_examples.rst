:original_name: en-us_topic_0140323152.html

.. _en-us_topic_0140323152:

Security Group Configuration Examples
=====================================

When you create instances, such as cloud servers, containers, and databases, in a VPC subnet, you can use the default security group or create a security group. You can add inbound and outbound rules to the default or your security group to control traffic from and to the instances in the security group. Here are some common security group configuration examples:

-  :ref:`Remotely Logging In to an ECS from a Local Server <en-us_topic_0140323152__en-us_topic_0118534011_section14933617154810>`
-  :ref:`Remotely Connecting to an ECS from a Local Server to Upload or Download Files over FTP <en-us_topic_0140323152__en-us_topic_0118534011_section8685162114185>`
-  :ref:`Setting Up a Website on an ECS to Provide Internet-Accessible Services <en-us_topic_0140323152__en-us_topic_0118534011_section316061115481>`
-  :ref:`Using ping Command to Verify Network Connectivity <en-us_topic_0140323152__en-us_topic_0118534011_section29561427142511>`
-  :ref:`Enabling Communications Between Instances in Different Security Groups <en-us_topic_0140323152__en-us_topic_0118534011_section094514632817>`
-  :ref:`Allowing External Instances to Access the Database Deployed on an ECS <en-us_topic_0140323152__en-us_topic_0118534011_section7465183583515>`
-  :ref:`Allowing ECSs to Access Only Specific External Websites <en-us_topic_0140323152__en-us_topic_0118534011_section949023514612>`

Precautions
-----------

Note the following before configuring security group rules:

-  Instances associated with different security groups are isolated from each other by default.

-  Generally, a security group denies all external requests by default, while allowing instances in it to communicate with each other.

   If required, you can add inbound rules to allow specific traffic to access the instances in the security group.

-  By default, outbound security group rules allow all requests from the instances in the security group to access external resources.

   If outbound rules are deleted, the instances in the security group cannot communicate with external resources. To allow outbound traffic, you need to add outbound rules by referring to :ref:`Table 1 <en-us_topic_0140323152__en-us_topic_0118534011_table102261597217>`.

   .. _en-us_topic_0140323152__en-us_topic_0118534011_table102261597217:

   .. table:: **Table 1** Default outbound rules in a security group

      +-----------+------+-----------------+-------------+--------------------------------------------------------------------------------------+
      | Direction | Type | Protocol & Port | Destination | Description                                                                          |
      +===========+======+=================+=============+======================================================================================+
      | Outbound  | IPv4 | All             | 0.0.0.0/0   | Allows the instances in the security group to access any IPv4 address over any port. |
      +-----------+------+-----------------+-------------+--------------------------------------------------------------------------------------+
      | Outbound  | IPv6 | All             | ::/0        | Allows the instances in the security group to access any IPv6 address over any port. |
      +-----------+------+-----------------+-------------+--------------------------------------------------------------------------------------+

.. _en-us_topic_0140323152__en-us_topic_0118534011_section14933617154810:

Remotely Logging In to an ECS from a Local Server
-------------------------------------------------

A security group denies all external requests by default. To remotely log in to an ECS in a security group from a local server, add an inbound rule based on the OS running on the ECS.

-  To remotely log in to a Linux ECS using SSH, enable port 22. For details, see :ref:`Table 2 <en-us_topic_0140323152__en-us_topic_0118534011_table20321112045011>`.

-  To remotely log in to a Windows ECS using RDP, enable port 3389. For details, see :ref:`Table 3 <en-us_topic_0140323152__en-us_topic_0118534011_table1579314381815>`.

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

      If the source is set to 0.0.0.0/0, all external IP addresses are allowed to remotely log in to the ECS. To ensure network security and prevent service interruptions caused by network intrusions, set the source to a trusted IP address. For details, see :ref:`Table 4 <en-us_topic_0140323152__en-us_topic_0118534011_table1919016251434>`.

   .. _en-us_topic_0140323152__en-us_topic_0118534011_table1919016251434:

   .. table:: **Table 4** Remotely logging in to an ECS using a trusted IP address

      =========== ========= ==== =============== ==========================
      ECS Type    Direction Type Protocol & Port Source
      =========== ========= ==== =============== ==========================
      Linux ECS   Inbound   IPv4 TCP: 22         IP address: 192.168.0.0/24
      Windows ECS Inbound   IPv4 TCP: 3389       IP address: 10.10.0.0/24
      =========== ========= ==== =============== ==========================

.. _en-us_topic_0140323152__en-us_topic_0118534011_section8685162114185:

Remotely Connecting to an ECS from a Local Server to Upload or Download Files over FTP
--------------------------------------------------------------------------------------

By default, a security group denies all external requests. If you need to remotely connect to an ECS from a local server to upload or download files over FTP, you need to enable FTP ports 20 and 21.

.. table:: **Table 5** Remotely connecting to an ECS from any server to upload or download files over FTP

   ========= ==== =============== =====================
   Direction Type Protocol & Port Source
   ========= ==== =============== =====================
   Inbound   IPv4 TCP: 20-21      IP address: 0.0.0.0/0
   ========= ==== =============== =====================

.. important::

   -  If the source is set to 0.0.0.0/0, all external IP addresses are allowed to remotely log in to the ECS to upload or download files. To ensure network security and prevent service interruptions caused by network intrusions, set the source to a trusted IP address. For details, see :ref:`Table 6 <en-us_topic_0140323152__en-us_topic_0118534011_table127653483419>`.
   -  You must first install the FTP server program on the ECSs and then check whether ports 20 and 21 are working properly.

.. _en-us_topic_0140323152__en-us_topic_0118534011_table127653483419:

.. table:: **Table 6** Remotely connecting to an ECS from a trusted server to upload or download files

   ========= ==== =============== ==========================
   Direction Type Protocol & Port Source
   ========= ==== =============== ==========================
   Inbound   IPv4 TCP: 20-21      IP address: 192.168.0.0/24
   ========= ==== =============== ==========================

.. _en-us_topic_0140323152__en-us_topic_0118534011_section316061115481:

Setting Up a Website on an ECS to Provide Internet-Accessible Services
----------------------------------------------------------------------

A security group denies all external requests by default. If you set up a website on an ECS to allow access from the Internet, you need to add an inbound rule to the ECS security group to allow access over specific ports, such as HTTP (80) and HTTPS (443).

.. table:: **Table 7** Setting up a website on an ECS to provide services internet-accessible services

   ========= ==== =============== =====================
   Direction Type Protocol & Port Source
   ========= ==== =============== =====================
   Inbound   IPv4 TCP: 80         IP address: 0.0.0.0/0
   Inbound   IPv4 TCP: 443        IP address: 0.0.0.0/0
   ========= ==== =============== =====================

.. _en-us_topic_0140323152__en-us_topic_0118534011_section29561427142511:

Using **ping** Command to Verify Network Connectivity
-----------------------------------------------------

Ping works by sending an Internet Control Message Protocol (ICMP) Echo Request. To ping an ECS from your PC to verify the network connectivity, you need to add an inbound rule to the security group of the ECS to allow ICMP traffic.

.. table:: **Table 8** Using **ping** command to verify network connectivity

   ========= ==== =============== =====================
   Direction Type Protocol & Port Source
   ========= ==== =============== =====================
   Inbound   IPv4 ICMP: All       IP address: 0.0.0.0/0
   Inbound   IPv6 ICMP: All       IP address: ::/0
   ========= ==== =============== =====================

.. _en-us_topic_0140323152__en-us_topic_0118534011_section094514632817:

Enabling Communications Between Instances in Different Security Groups
----------------------------------------------------------------------

Instances in the same VPC but in different security groups cannot communicate with each other. If you want ECSs in security group **sg-A** to access MySQL databases in security group **sg-B**, you need to add an inbound rule to security group **sg-B** to allow access from ECSs in security group **sg-A**.

.. table:: **Table 9** Enabling communications between instances in different security groups

   ========= ==== =============== ====================
   Direction Type Protocol & Port Source
   ========= ==== =============== ====================
   Inbound   IPv4 TCP: 3306       Security group: sg-A
   ========= ==== =============== ====================

.. _en-us_topic_0140323152__en-us_topic_0118534011_section7465183583515:

Allowing External Instances to Access the Database Deployed on an ECS
---------------------------------------------------------------------

A security group denies all external requests by default. If you have deployed a database on an ECS and want the database to be accessed from external instances on a private network, you need to add an inbound rule to the security group of the ECS to allow access over corresponding ports. Here are some common ports for databases:

-  MySQL: port 3306
-  Oracle: port 1521
-  MS SQL: port 1433
-  PostgreSQL: port 5432
-  Redis: port 6379

.. table:: **Table 10** Allowing external instances to access the database deployed on an ECS

   +-----------+------+-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------+
   | Direction | Type | Protocol & Port | Source                     | Description                                                                                                 |
   +===========+======+=================+============================+=============================================================================================================+
   | Inbound   | IPv4 | TCP: 3306       | Security group: sg-A       | Allows the ECSs in security group **sg-A** to access the MySQL database.                                    |
   +-----------+------+-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv4 | TCP: 1521       | Security group: sg-B       | Allows the ECSs in security group **sg-B** to access the Oracle database.                                   |
   +-----------+------+-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv4 | TCP: 1433       | IP address: 172.16.3.21/32 | Allows the ECS whose private IP address is 172.16.3.21 to access the MS SQL database.                       |
   +-----------+------+-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv4 | TCP: 5432       | IP address: 192.168.0.0/24 | Allows ECSs whose private IP addresses are in the 192.168.0.0/24 network to access the PostgreSQL database. |
   +-----------+------+-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------+

.. important::

   In this example, the source IP addresses are for reference only. Replace them with actual IP addresses.

.. _en-us_topic_0140323152__en-us_topic_0118534011_section949023514612:

Allowing ECSs to Access Only Specific External Websites
-------------------------------------------------------

By default, a security group allows all outbound traffic. :ref:`Table 12 <en-us_topic_0140323152__en-us_topic_0118534011_table5759161135518>` lists the default outbound rules. If you want to allow ECSs to access only specific websites, configure the security group as follows:

#. Add outbound rules to only allow traffic over specific ports to specific IP addresses.

   .. table:: **Table 11** Allowing ECSs to access only specific external websites

      +-----------+------+-----------------+---------------------------+------------------------------------------------------------------------------------------------+
      | Direction | Type | Protocol & Port | Destination               | Description                                                                                    |
      +===========+======+=================+===========================+================================================================================================+
      | Outbound  | IPv4 | TCP: 80         | IP address: 132.15.XX.XX  | Allows ECSs in the security group to access the external website at http://132.15.XX.XX:80.    |
      +-----------+------+-----------------+---------------------------+------------------------------------------------------------------------------------------------+
      | Outbound  | IPv4 | TCP: 443        | IP address: 145.117.XX.XX | Allows ECSs in the security group to access the external website at https://145.117.XX.XX:443. |
      +-----------+------+-----------------+---------------------------+------------------------------------------------------------------------------------------------+

#. Delete the default outbound rules that allow all traffic.

   .. _en-us_topic_0140323152__en-us_topic_0118534011_table5759161135518:

   .. table:: **Table 12** Default outbound rules in a security group

      +-----------+------+-----------------+-------------+--------------------------------------------------------------------------------------+
      | Direction | Type | Protocol & Port | Destination | Description                                                                          |
      +===========+======+=================+=============+======================================================================================+
      | Outbound  | IPv4 | All             | 0.0.0.0/0   | Allows the instances in the security group to access any IPv4 address over any port. |
      +-----------+------+-----------------+-------------+--------------------------------------------------------------------------------------+
      | Outbound  | IPv6 | All             | ::/0        | Allows the instances in the security group to access any IPv6 address over any port. |
      +-----------+------+-----------------+-------------+--------------------------------------------------------------------------------------+
