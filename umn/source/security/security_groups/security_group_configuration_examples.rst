Security Group Configuration Examples
=====================================

Common security group configuration examples are as follows: The following examples allow all outgoing data packets by default and only describe how to configure the inbound rules of a security group.

-  `Enabling ECSs in Different Security Groups to Communicate with Each Other Through an Internal Network <#enabling-ecss-in-different-security-groups-to-communicate-with-each-other-through-an-internal-network>`__
-  `Enabling Specified IP Addresses to Remotely Access ECSs in a Security Group <#enabling-specified-ip-addresses-to-remotely-access-ecss-in-a-security-group>`__
-  `Remotely Connecting to Linux ECSs Using SSH <#remotely-connecting-to-linux-ecss-using-ssh>`__
-  `Remotely Connecting to Windows ECSs Using RDP <#remotely-connecting-to-windows-ecss-using-rdp>`__
-  `Enabling Communication Between ECSs <#enabling-communication-between-ecss>`__
-  `Hosting a Website on ECSs <#hosting-a-website-on-ecss>`__
-  `Enabling an ECS to Function as a DNS Server <#enabling-an-ecs-to-function-as-a-dns-server>`__
-  `Uploading or Downloading Files Using FTP <#uploading-or-downloading-files-using-ftp>`__

Enabling ECSs in Different Security Groups to Communicate with Each Other Through an Internal Network
-----------------------------------------------------------------------------------------------------

-  Example scenario:

   Resources on an ECS in a security group need to be copied to an ECS associated with another security group. The two ECSs are in the same VPC. We recommend that you enable private network communication between the ECSs and then copy the resources.

-  Security group configuration:

   Within a given VPC, ECSs in the same security group can communicate with one another by default. However, ECSs in different security groups cannot communicate with each other by default. To enable these ECSs to communicate with each other, you need to add certain security group rules.

   You can add an inbound rule to the security groups containing the ECSs to allow access from ECSs in the other security group. The required rule is as follows.

   

.. _ENUSTOPIC0140323152enustopic0118534011table854766319358:

   +---------------+----------------------------------------------------+--------------------+------------------------------+
   | **Direction** | **Protocol/Application**                           | **Port**           | **Source**                   |
   +===============+====================================================+====================+==============================+
   | Inbound       | Used for communication through an internal network | Port or port range | ID of another security group |
   +---------------+----------------------------------------------------+--------------------+------------------------------+

Enabling Specified IP Addresses to Remotely Access ECSs in a Security Group
---------------------------------------------------------------------------

-  Example scenario:

   To prevent ECSs from being attacked, you can change the port for remote login and configure security group rules that allow only specified IP addresses to remotely access the ECSs.

-  Security group configuration:

   To allow IP address **192.168.20.2** to remotely access Linux ECSs in a security group over the SSH protocol (port 22), you can configure the following security group rule.

   

.. _ENUSTOPIC0140323152enustopic0118534011table2497622119555:

   +-----------------+-----------------+-----------------+-------------------------------------------------+
   | **Direction**   | **Protocol**    | **Port**        | **Source**                                      |
   +=================+=================+=================+=================================================+
   | Inbound         | SSH             | 22              | IPv4 CIDR block or ID of another security group |
   |                 |                 |                 |                                                 |
   |                 |                 |                 | For example, 192.168.20.2/32                    |
   +-----------------+-----------------+-----------------+-------------------------------------------------+

Remotely Connecting to Linux ECSs Using SSH
-------------------------------------------

-  Example scenario:

   After creating Linux ECSs, you can add a security group rule to enable remote SSH access to the ECSs.

-  Security group rule: 

.. _ENUSTOPIC0140323152enustopic0118534011table16351717123312:

   ============= ============ ======== ==========
   **Direction** **Protocol** **Port** **Source**
   ============= ============ ======== ==========
   Inbound       SSH          22       0.0.0.0/0
   ============= ============ ======== ==========

Remotely Connecting to Windows ECSs Using RDP
---------------------------------------------

-  Example scenario:

   After creating Windows ECSs, you can add a security group rule to enable remote RDP access to the ECSs.

-  Security group rule: 

.. _ENUSTOPIC0140323152enustopic0118534011table129650323711:

   ============= ============ ======== ==========
   **Direction** **Protocol** **Port** **Source**
   ============= ============ ======== ==========
   Inbound       RDP          3389     0.0.0.0/0
   ============= ============ ======== ==========

Enabling Communication Between ECSs
-----------------------------------

-  Example scenario:

   After creating ECSs, you need to add a security group rule so that you can run the **ping** command to test communication between the ECSs.

-  Security group rule: 

.. _ENUSTOPIC0140323152enustopic0118534011table810055173719:

   ============= ============ ======== ==========
   **Direction** **Protocol** **Port** **Source**
   ============= ============ ======== ==========
   Inbound       ICMP         All      0.0.0.0/0
   ============= ============ ======== ==========

Hosting a Website on ECSs
-------------------------

-  Example scenario:

   If you deploy a website on your ECSs and require that your website be accessed over HTTP or HTTPS, you can add rules to the security group used by the ECSs that function as the web servers.

-  Security group rule: 

.. _ENUSTOPIC0140323152enustopic0118534011table30323767195135:

   ============= ============ ======== ==========
   **Direction** **Protocol** **Port** **Source**
   ============= ============ ======== ==========
   Inbound       HTTP         80       0.0.0.0/0
   Inbound       HTTPS        443      0.0.0.0/0
   ============= ============ ======== ==========

Enabling an ECS to Function as a DNS Server
-------------------------------------------

-  Example scenario:

   If you need to use an ECS as a DNS server, you must allow TCP and UDP access from port 53 to the DNS server. You can add the following rules to the security group associated with the ECS.

-  Security group rules: 

.. _ENUSTOPIC0140323152enustopic0118534011table9719143933517:

   ============= ============ ======== ==========
   **Direction** **Protocol** **Port** **Source**
   ============= ============ ======== ==========
   Inbound       TCP          53       0.0.0.0/0
   Inbound       UDP          53       0.0.0.0/0
   ============= ============ ======== ==========

Uploading or Downloading Files Using FTP
----------------------------------------

-  Example scenario:

   If you want to use File Transfer Protocol (FTP) to upload files to or download files from ECSs, you need to add a security group rule.

   .. note::

      You must first install the FTP server program on the ECSs and check whether ports 20 and 21 are working properly.

-  Security group rule: 

.. _ENUSTOPIC0140323152enustopic0118534011table8479153013395:

   ============= ============ ======== ==========
   **Direction** **Protocol** **Port** **Source**
   ============= ============ ======== ==========
   Inbound       TCP          20-21    0.0.0.0/0
   ============= ============ ======== ==========


