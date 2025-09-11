:original_name: en-us_topic_0042400609.html

.. _en-us_topic_0042400609:

Obtaining ECS Details Using Metadata
====================================

Scenarios
---------

ECS metadata is a special API that can be locally accessed in the ECS OS. It contains basic ECS details, such as the cloud server ID, hostname, and network details. With ECS metadata, you can exchange basic information in an ECS and configure and manage the ECS OS and applications more conveniently and securely. Metadata allows you to configure information in the OS during initialization and obtain ECS information during service running.

ECS metadata supports OpenStack and EC2 compatible types, as shown in :ref:`Table 1 <en-us_topic_0042400609__table273552371680>`.

The following describes the URI and methods of using the supported ECS metadata.

Notes
-----

If the metadata contains sensitive data, take appropriate measures to protect the sensitive data, for example, controlling access permissions and encrypting the data.

Example configurations on the firewall are listed below:

-  Windows

   To only allow the administrator to access custom data, enable the firewall as the administrator and run the following commands in PowerShell:

   **PS C:\\>$RejectPrincipal = New-Object -TypeName System.Security.Principal.NTAccount ("Everyone")**

   **PS C:\\>$RejectPrincipalSID = $RejectPrincipal.Translate([System.Security.Principal.SecurityIdentifier]).Value**

   **PS C:\\>$ExceptPrincipal = New-Object -TypeName System.Security.Principal.NTAccount ("Administrator")**

   **PS C:\\>$ExceptPrincipalSID = $ExceptPrincipal.Translate([System.Security.Principal.SecurityIdentifier]).Value**

   **PS C:\\>$PrincipalSDDL = "O:LSD:(D;;CC;;;$ExceptPrincipalSID)(A;;CC;;;$RejectPrincipalSID)"**

   **PS C:\\>New-NetFirewallRule -DisplayName "Reject metadata service for $($RejectPrincipal.Value), exception: $($ExceptPrincipal.Value)" -Action block -Direction out -Protocol TCP -RemoteAddress 169.254.169.254 -LocalUser $PrincipalSDDL**

-  Linux

   To only allow user **root** to access custom data, run the following command as user **root**:

   **iptables --append OUTPUT --proto tcp --destination 169.254.169.254 --match owner ! --uid-owner root --jump REJECT**

ECS Metadata Types
------------------

:ref:`Table 1 <en-us_topic_0042400609__table273552371680>` does not contain the following EC2-compatible metadata items: ami-id, ami-launch-index, ami-manifest-path, block-device-mapping, instance-action, instance-id, reservation-id, ramdisk-id, and kernel-id. These metadata items are meaningless and not recommended.

.. _en-us_topic_0042400609__table273552371680:

.. table:: **Table 1** ECS metadata types

   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Metadata Type         | Metadata Item                                 | Description                                                                                                                                                                                                                                      |
   +=======================+===============================================+==================================================================================================================================================================================================================================================+
   | OpenStack             | /openstack/latest/meta_data.json              | Displays ECS metadata.                                                                                                                                                                                                                           |
   |                       |                                               |                                                                                                                                                                                                                                                  |
   |                       |                                               | For the key fields in the ECS metadata, see :ref:`Table 2 <en-us_topic_0042400609__table2373623012315>`.                                                                                                                                         |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OpenStack             | /openstack/latest/password                    | Displays the password for logging in to an ECS.                                                                                                                                                                                                  |
   |                       |                                               |                                                                                                                                                                                                                                                  |
   |                       |                                               | This metadata is used by Cloudbase-Init to store ciphertext passwords during initialization of key-pair-authenticated Windows ECSs.                                                                                                              |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OpenStack             | /openstack/latest/user_data                   | Displays ECS user data.                                                                                                                                                                                                                          |
   |                       |                                               |                                                                                                                                                                                                                                                  |
   |                       |                                               | You can specify scripts and configuration files for ECS initialization as required. User-defined data is read and parsed by software such as Cloud-Init or Cloudbase-Init. For details, see :ref:`Injecting User Data <en-us_topic_0032380449>`. |
   |                       |                                               |                                                                                                                                                                                                                                                  |
   |                       |                                               | For password-authenticated Linux ECSs, this metadata is used to save password injection scripts.                                                                                                                                                 |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OpenStack             | /openstack/latest/network_data.json           | Displays ECS network information.                                                                                                                                                                                                                |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OpenStack             | /openstack/latest/securitykey                 | Obtains temporary AKs and SKs.                                                                                                                                                                                                                   |
   |                       |                                               |                                                                                                                                                                                                                                                  |
   |                       |                                               | Before enabling an ECS to obtain a temporary AK and SK, authorize agency permissions to the **op_svc_ecs** account and ECSs in IAM.                                                                                                              |
   |                       |                                               |                                                                                                                                                                                                                                                  |
   |                       |                                               | .. note::                                                                                                                                                                                                                                        |
   |                       |                                               |                                                                                                                                                                                                                                                  |
   |                       |                                               |    You can determine what permissions are granted to the agency based on the principal of least privilege (PoLP).                                                                                                                                |
   |                       |                                               |                                                                                                                                                                                                                                                  |
   |                       |                                               |    ECSs will not use agencies to perform operations on resources.                                                                                                                                                                                |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EC2 compatible        | /latest/meta-data/hostname                    | Displays the name of the host accommodating an ECS.                                                                                                                                                                                              |
   |                       |                                               |                                                                                                                                                                                                                                                  |
   |                       |                                               | To remove the suffix **.novalocal** from an ECS, see:                                                                                                                                                                                            |
   |                       |                                               |                                                                                                                                                                                                                                                  |
   |                       |                                               | :ref:`Is an ECS Hostname with Suffix .novalocal Normal? <en-us_topic_0094874138>`                                                                                                                                                                |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EC2 compatible        | /latest/meta-data/local-hostname              | Has the same meaning as **hostname**.                                                                                                                                                                                                            |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EC2 compatible        | /latest/meta-data/public-hostname             | Has the same meaning as **hostname**.                                                                                                                                                                                                            |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EC2 compatible        | /latest/meta-data/instance-type               | Displays an ECS flavor.                                                                                                                                                                                                                          |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EC2 compatible        | /latest/meta-data/local-ipv4                  | Displays the fixed IP address of an ECS.                                                                                                                                                                                                         |
   |                       |                                               |                                                                                                                                                                                                                                                  |
   |                       |                                               | If there are multiple NICs, only the IP address of the primary NIC is displayed.                                                                                                                                                                 |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EC2 compatible        | /latest/meta-data/placement/availability-zone | Displays the AZ accommodating an ECS.                                                                                                                                                                                                            |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EC2 compatible        | /latest/meta-data/public-ipv4                 | Displays the EIP bound to the ECS.                                                                                                                                                                                                               |
   |                       |                                               |                                                                                                                                                                                                                                                  |
   |                       |                                               | If there are multiple NICs, only the EIP of the primary NIC is displayed.                                                                                                                                                                        |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EC2 compatible        | /latest/meta-data/public-keys/0/openssh-key   | Displays the public key of an ECS.                                                                                                                                                                                                               |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EC2 compatible        | /latest/user-data                             | Displays ECS user data. It is used the same way as user-data in the OpenStack metadata type.                                                                                                                                                     |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EC2 compatible        | /latest/meta-data/security-groups             | Displays the security group of an ECS.                                                                                                                                                                                                           |
   +-----------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0042400609__table2373623012315:

.. table:: **Table 2** metadata key fields

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                         |
   +=======================+=======================+=====================================================================================+
   | uuid                  | String                | Specifies an ECS ID.                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------+
   | availability_zone     | String                | Specifies the AZ where an ECS locates.                                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------+
   | meta                  | Dict                  | Specifies the metadata information, including the image name, image ID, and VPC ID. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------+
   | hostname              | String                | Specifies the name of the host accommodating an ECS.                                |
   |                       |                       |                                                                                     |
   |                       |                       | To remove the suffix **.novalocal** from an ECS, see:                               |
   |                       |                       |                                                                                     |
   |                       |                       | :ref:`Is an ECS Hostname with Suffix .novalocal Normal? <en-us_topic_0094874138>`   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------+

Prerequisites
-------------

-  The target ECS has been logged in.
-  Security group rules in the outbound direction meet the following requirements:

   -  Protocol: TCP
   -  Port: 80
   -  Destination: 169.254.0.0/16

   .. note::

      If you use the default security group rules for the outbound direction, the metadata can be accessed because the default rules meet the preceding requirements. For details about the default security group rules for the outbound direction, see :ref:`Default Security Groups and Rules <en-us_topic_0140323154>`.

Metadata (OpenStack Metadata API)
---------------------------------

This API is used to query ECS metadata.

-  URI

   /169.254.169.254/openstack/latest/meta_data.json

-  Usage method

   GET request

-  Example

   To use cURL to view Linux ECS metadata, run the following command:

   **curl http://169.254.169.254/openstack/latest/meta_data.json**

   To use Invoke-RestMethod to view Windows ECS metadata, run the following command:

   **Invoke-RestMethod http://169.254.169.254/openstack/latest/meta_data.json \| ConvertTo-Json**

   .. code-block::

      {
          "random_seed": "rEocCViRS+dNwlYdGIxJHUp+00poeUsAdBFkbPbYQTmpNwpoEb43k9z+96TyrekNKS+iLYDdRNy4kKGoNPEVBCc05Hg1TcDblAPfJwgJS1okqEtlcofUhKmL3K0fto+5KXEDU3GNuGwyZXjdVb9HQWU+E1jztAJjjqsahnU+g/tawABTVySLBKlAT8fMGax1mTGgArucn/WzDcy19DGioKPE7F8ILtSQ4Ww3VClK5VYB/h0x+4r7IVHrPmYX/bi1Yhm3Dc4rRYNaTjdOV5gUOsbO3oAeQkmKwQ/NO0N8qw5Ya4l8ZUW4tMav4mOsRySOOB35v0bvaJc6p+50DTbWNeX5A2MLiEhTP3vsPrmvk4LRF7CLz2J2TGIM14OoVBw7LARwmv9cz532zHki/c8tlhRzLmOTXh/wL36zFW10DeuReUGmxth7IGNmRMQKV6+miI78jm/KMPpgAdK3vwYF/GcelOFJD2HghMUUCeMbwYnvijLTejuBpwhJMNiHA/NvlEsxJDxqBCoss/Jfe+yCmUFyxovJ+L8oNkTzkmtCNzw3Ra0hiKchGhqK3BIeToV/kVx5DdF081xrEA+qyoM6CVyfJtEoz1zlRRyoo9bJ65Eg6JJd8dj1UCVsDqRY1pIjgzE/Mzsw6AaaCVhaMJL7u7YMVdyKzA6z65Xtvujz0Vo=",
          "uuid": "ca9e8b7c-f2be-4b6d-a639-f10b4d994d04",
          "availability_zone": "lt-test-1c",
          "hostname": "ecs-ddd4.novalocal",
          "launch_index": 0,
          "meta": {
              "metering.image_id": "3a64bd37-955e-40cd-ab9e-129db56bc05d",
              "metering.imagetype": "gold",
              "metering.resourcespeccode": "s3.medium.2.linux",
              "image_name": "CentOS 7.6 64bit",
              "metering.resourcetype": "1",
              "vpc_id": "3b6c201f-aeb3-4bce-b841-64756e66cb49",
              "os_bit": "64",
              "cascaded.instance_extrainfo": "pcibridge:1",
              "os_type": "Linux",
              "charging_mode": "0"
          },
          "project_id": "6e8b0c94265645f39c5abbe63c4113c6",
          "name": "ecs-ddd4"
      }

User Data (OpenStack Metadata API)
----------------------------------

This API is used to query ECS user data. The value is configured only when you create an ECS. It cannot be changed after the configuration.

-  URI

   /169.254.169.254/openstack/latest/user_data

-  Usage method

   GET request

-  Example

   Linux:

   **curl http://169.254.169.254/openstack/latest/user_data**

   Windows:

   **Invoke-RestMethod** **http://169.254.169.254/openstack/latest/user_data**

   .. code-block::

      #!/bin/bash
      echo "Hello, the time is now $(date -R)" | tee /root/output.txt

   .. note::

      If user data was not passed to the ECS during ECS creation, the query result is 404.


      .. figure:: /_static/images/en-us_image_0166755236.png
         :alt: **Figure 1** 404 Not Found

         **Figure 1** 404 Not Found

Network Data (OpenStack Metadata API)
-------------------------------------

This API is used to query information about all NICs attached to an ECS, including their DNS server addresses, network bandwidth, IDs, private IP addresses, EIPs, and MAC addresses.

-  URI

   /openstack/latest/network_data.json

-  Usage method

   Supports GET requests.

-  Example

   .. note::

      **instance_max_bandwidth** and **instance_min_bandwidth** are in the unit of Mbit/s. If the value is **-1**, the bandwidth is not limited.

   Linux:

   **curl http://169.254.169.254/openstack/latest/network_data.json**

   Windows:

   **Invoke-RestMethod http://169.254.169.254/openstack/latest/network_data.json \| ConvertTo-Json**

   .. code-block::

      {
          "services": [{
              "type": "dns",
              "address": "xxx.xx.x.x"
          },
          {
              "type": "dns",
              "address": "100.125.21.250"
          }],
          "qos":{
              "instance_min_bandwidth": 100,
              "instance_max_bandwidth": 500
          },
          "networks": [{
              "network_id": "67dc10ce-441f-4592-9a80-cc709f6436e7",
              "type": "ipv4_dhcp",
              "link": "tap68a9272d-71",
              "id": "network0"
          }],
          "links": [{
              "vif_id": "68a9272d-7152-4ae7-a138-3ef53af669e7",
              "ethernet_mac_address": "fa:16:3e:f7:c1:47",
              "mtu": null,
              "type": "cascading",
              "id": "tap68a9272d-71"
          }]
      }

Security Key (OpenStack Metadata API)
-------------------------------------

This API is used to obtain a temporary AK/SK.

.. note::

   -  If an ECS needs to obtain a temporary AK/SK, you need to create and authorize an agency on the IAM console and then go to the ECS details page to configure **Agency** for the ECS in the **Management Information** area.
   -  The validity period of a temporary AK and SK is one hour. The temporary AK and SK are updated 10 minutes ahead of the expiration time. During the 10 minutes, both the new and old temporary AKs and SKs can be used.
   -  When using temporary AKs and SKs, add **'X-Security-Token':{securitytoken}** in the message header. **securitytoken** is the value returned when a call is made to the API.

-  URI

   /openstack/latest/securitykey

-  Usage method

   Supports GET requests.

-  Examples

   Linux:

   **curl http://169.254.169.254/openstack/latest/securitykey**

   Windows:

   **Invoke-RestMethod http://169.254.169.254/openstack/latest/securitykey**

User Data (EC2 Compatible API)
------------------------------

This API is used to query ECS user data. The value is configured only when you create an ECS. It cannot be changed after the configuration.

-  URI

   /169.254.169.254/latest/user-data

-  Usage method

   GET request

-  Example

   Linux:

   **curl http://169.254.169.254/latest/user-data**

   Windows:

   **Invoke-RestMethod http://169.254.169.254/latest/user-data**

   .. code-block::

      #!/bin/bash
      echo "Hello, the time is now $(date -R)" | tee /root/output.txt

Hostname (EC2 Compatible API)
-----------------------------

This API is used to query the name of the host accommodating an ECS. The **.novalocal** suffix will be added later.

-  URI

   /169.254.169.254/latest/meta-data/hostname

-  Usage method

   GET request

-  Example

   Linux:

   **curl http://169.254.169.254/latest/meta-data/hostname**

   Windows:

   **Invoke-RestMethod http://169.254.169.254/latest/meta-data/hostname**

   .. code-block::

      vm-test.novalocal

Instance Type (EC2 Compatible API)
----------------------------------

This API is used to query an ECS flavor.

-  URI

   /169.254.169.254/latest/meta-data/instance-type

-  Usage method

   GET request

-  Example

   Linux:

   **curl http://169.254.169.254/latest/meta-data/instance-type**

   Windows:

   **Invoke-RestMethod http://169.254.169.254/latest/meta-data/instance-type**

   .. code-block::

      s3.medium.2

Local IPv4 (EC2 Compatible API)
-------------------------------

This API is used to query the fixed IP address of an ECS. If there are multiple NICs, only the IP address of the primary NIC is displayed.

-  URI

   /169.254.169.254/latest/meta-data/local-ipv4

-  Usage method

   GET request

-  Example

   Linux:

   **curl http://169.254.169.254/latest/meta-data/local-ipv4**

   Windows:

   **Invoke-RestMethod http://169.254.169.254/latest/meta-data/local-ipv4**

   .. code-block::

      192.1.1.2

Availability Zone (EC2 Compatible API)
--------------------------------------

This API is used to query the AZ accommodating an ECS.

-  URI

   /169.254.169.254/latest/meta-data/placement/availability-zone

-  Usage method

   GET request

-  Example

   Linux:

   **curl http://169.254.169.254/latest/meta-data/placement/availability-zone**

   Windows:

   **Invoke-RestMethod http://169.254.169.254/latest/meta-data/placement/availability-zone**

   .. code-block::

      az1.dc1

Public IPv4 (EC2 Compatible API)
--------------------------------

This API is used to query the EIP bound to an ECS. If there are multiple NICs, only the EIP of the primary NIC is displayed.

-  URI

   /169.254.169.254/latest/meta-data/public-ipv4

-  Usage method

   GET request

-  Example

   Linux:

   **curl http://169.254.169.254/latest/meta-data/public-ipv4**

   Windows:

   **Invoke-RestMethod http://169.254.169.254/latest/meta-data/public-ipv4**

   .. code-block::

      46.1.1.2

Public Keys (EC2 Compatible API)
--------------------------------

This API is used to query the public key of an ECS.

-  URI

   /169.254.169.254/latest/meta-data/public-keys/0/openssh-key

-  Usage method

   GET request

-  Example

   Linux:

   **curl http://169.254.169.254/latest/meta-data/public-keys/0/openssh-key**

   Windows:

   **Invoke-RestMethod http://169.254.169.254/latest/meta-data/public-keys/0/openssh-key**

   .. code-block::

      ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDI5Fw5k8Fgzajn1zJwLoV3+wMP+6CyvsSiIc/hioggSnYu/AD0Yqm8vVO0kWlun1rFbdO+QUZKyVr/OPUjQSw4SRh4qsTKf/+eFoWTjplFvd1WCBZzS/WRenxIwR00KkczHSJro763+wYcwKieb4eKRxaQoQvoFgVjLBULXAjH4eKoKTVNtMXAvPP9aMy2SLgsJNtMb9ArfziAiblQynq7UIfLnN3VclzPeiWrqtzjyOp6CPUXnL0lVPTvbLe8sUteBsJZwlL6K4i+Y0lf3ryqnmQgC21yW4Dzu+kwk8FVT2MgWkCwiZd8gQ/+uJzrJFyMfUOBIklOBfuUENIJUhAB Generated-by-Nova

Helpful Links
-------------

:ref:`Why Can't My Linux ECS Obtain Metadata? <en-us_topic_0000001138811177>`
