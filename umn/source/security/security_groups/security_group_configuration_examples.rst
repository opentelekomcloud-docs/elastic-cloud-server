.. _en-us_topic_0140323152:

Security Group Configuration Examples
=====================================

Common security group configuration examples are as follows: The following examples allow all outgoing data packets by default and only describe how to configure the inbound rules of a security group.

-  :ref:`Enabling ECSs in Different Security Groups to Communicate with Each Other Through an Internal Network <en-us_topic_0140323152__en-us_topic_0118534011_section14197522283>`
-  :ref:`Enabling Specified IP Addresses to Remotely Access ECSs in a Security Group <en-us_topic_0140323152__en-us_topic_0118534011_section17693183118306>`
-  :ref:`Remotely Connecting to Linux ECSs Using SSH <en-us_topic_0140323152__en-us_topic_0118534011_section115069253338>`
-  :ref:`Remotely Connecting to Windows ECSs Using RDP <en-us_topic_0140323152__en-us_topic_0118534011_section168046312349>`
-  :ref:`Enabling Communication Between ECSs <en-us_topic_0140323152__en-us_topic_0118534011_section34721049193411>`
-  :ref:`Hosting a Website on ECSs <en-us_topic_0140323152__en-us_topic_0118534011_section1517991516357>`
-  :ref:`Enabling an ECS to Function as a DNS Server <en-us_topic_0140323152__en-us_topic_0118534011_section2910346123520>`
-  :ref:`Uploading or Downloading Files Using FTP <en-us_topic_0140323152__en-us_topic_0118534011_section5964121693610>`



.. _en-us_topic_0140323152__en-us_topic_0118534011_section14197522283:

Enabling ECSs in Different Security Groups to Communicate with Each Other Through an Internal Network
-----------------------------------------------------------------------------------------------------

-  Example scenario:

   Resources on an ECS in a security group need to be copied to an ECS associated with another security group. The two ECSs are in the same VPC. We recommend that you enable private network communication between the ECSs and then copy the resources.

-  Security group configuration:

   Within a given VPC, ECSs in the same security group can communicate with one another by default. However, ECSs in different security groups cannot communicate with each other by default. To enable these ECSs to communicate with each other, you need to add certain security group rules.

   You can add an inbound rule to the security groups containing the ECSs to allow access from ECSs in the other security group. The required rule is as follows.

   

.. _en-us_topic_0140323152__en-us_topic_0118534011_table854766319358:

   +---------------+----------------------------------------------------+--------------------+------------------------------+
   | **Direction** | **Protocol/Application**                           | **Port**           | **Source**                   |
   +===============+====================================================+====================+==============================+
   | Inbound       | Used for communication through an internal network | Port or port range | ID of another security group |
   +---------------+----------------------------------------------------+--------------------+------------------------------+



.. _en-us_topic_0140323152__en-us_topic_0118534011_section17693183118306:

Enabling Specified IP Addresses to Remotely Access ECSs in a Security Group
---------------------------------------------------------------------------

-  Example scenario:

   To prevent ECSs from being attacked, you can change the port for remote login and configure security group rules that allow only specified IP addresses to remotely access the ECSs.

-  Security group configuration:

   To allow IP address **192.168.20.2** to remotely access Linux ECSs in a security group over the SSH protocol (port 22), you can configure the following security group rule.

   

.. _en-us_topic_0140323152__en-us_topic_0118534011_table2497622119555:

   +-----------------+-----------------+-----------------+-------------------------------------------------+
   | **Direction**   | **Protocol**    | **Port**        | **Source**                                      |
   +=================+=================+=================+=================================================+
   | Inbound         | SSH             | 22              | IPv4 CIDR block or ID of another security group |
   |                 |                 |                 |                                                 |
   |                 |                 |                 | For example, 192.168.20.2/32                    |
   +-----------------+-----------------+-----------------+-------------------------------------------------+



.. _en-us_topic_0140323152__en-us_topic_0118534011_section115069253338:

Remotely Connecting to Linux ECSs Using SSH
-------------------------------------------

-  Example scenario:

   After creating Linux ECSs, you can add a security group rule to enable remote SSH access to the ECSs.

-  Security group rule:

   

.. _en-us_topic_0140323152__en-us_topic_0118534011_table16351717123312:

   ============= ============ ======== ==========
   **Direction** **Protocol** **Port** **Source**
   ============= ============ ======== ==========
   Inbound       SSH          22       0.0.0.0/0
   ============= ============ ======== ==========



.. _en-us_topic_0140323152__en-us_topic_0118534011_section168046312349:

Remotely Connecting to Windows ECSs Using RDP
---------------------------------------------

-  Example scenario:

   After creating Windows ECSs, you can add a security group rule to enable remote RDP access to the ECSs.

-  Security group rule:

   

.. _en-us_topic_0140323152__en-us_topic_0118534011_table129650323711:

   ============= ============ ======== ==========
   **Direction** **Protocol** **Port** **Source**
   ============= ============ ======== ==========
   Inbound       RDP          3389     0.0.0.0/0
   ============= ============ ======== ==========



.. _en-us_topic_0140323152__en-us_topic_0118534011_section34721049193411:

Enabling Communication Between ECSs
-----------------------------------

-  Example scenario:

   After creating ECSs, you need to add a security group rule so that you can run the **ping** command to test communication between the ECSs.

-  Security group rule:

   

.. _en-us_topic_0140323152__en-us_topic_0118534011_table810055173719:

   ============= ============ ======== ==========
   **Direction** **Protocol** **Port** **Source**
   ============= ============ ======== ==========
   Inbound       ICMP         All      0.0.0.0/0
   ============= ============ ======== ==========



.. _en-us_topic_0140323152__en-us_topic_0118534011_section1517991516357:

Hosting a Website on ECSs
-------------------------

-  Example scenario:

   If you deploy a website on your ECSs and require that your website be accessed over HTTP or HTTPS, you can add rules to the security group used by the ECSs that function as the web servers.

-  Security group rule:

   

.. _en-us_topic_0140323152__en-us_topic_0118534011_table30323767195135:

   ============= ============ ======== ==========
   **Direction** **Protocol** **Port** **Source**
   ============= ============ ======== ==========
   Inbound       HTTP         80       0.0.0.0/0
   Inbound       HTTPS        443      0.0.0.0/0
   ============= ============ ======== ==========



.. _en-us_topic_0140323152__en-us_topic_0118534011_section2910346123520:

Enabling an ECS to Function as a DNS Server
-------------------------------------------

-  Example scenario:

   If you need to use an ECS as a DNS server, you must allow TCP and UDP access from port 53 to the DNS server. You can add the following rules to the security group associated with the ECS.

-  Security group rules:

   

.. _en-us_topic_0140323152__en-us_topic_0118534011_table9719143933517:

   ============= ============ ======== ==========
   **Direction** **Protocol** **Port** **Source**
   ============= ============ ======== ==========
   Inbound       TCP          53       0.0.0.0/0
   Inbound       UDP          53       0.0.0.0/0
   ============= ============ ======== ==========



.. _en-us_topic_0140323152__en-us_topic_0118534011_section5964121693610:

Uploading or Downloading Files Using FTP
----------------------------------------

-  Example scenario:

   If you want to use File Transfer Protocol (FTP) to upload files to or download files from ECSs, you need to add a security group rule.

   .. note::

      You must first install the FTP server program on the ECSs and check whether ports 20 and 21 are working properly.

-  Security group rule:

   

.. _en-us_topic_0140323152__en-us_topic_0118534011_table8479153013395:

   ============= ============ ======== ==========
   **Direction** **Protocol** **Port** **Source**
   ============= ============ ======== ==========
   Inbound       TCP          20-21    0.0.0.0/0
   ============= ============ ======== ==========
