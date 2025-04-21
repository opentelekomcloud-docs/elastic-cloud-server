:original_name: en-us_topic_0000001194242043.html

.. _en-us_topic_0000001194242043:

Methods for Improving ECS Security
==================================

Scenarios
---------

If ECSs are not protected, they may be attacked by viruses, resulting in data leakage or data loss.

You can use the methods introduced below to protect your ECSs from viruses or attacks.

Protection Types
----------------

ECS can be protected externally and internally.

.. table:: **Table 1** Methods for improving ECS security

   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
   | Type                  | Description                                                                                                                                                                                                                                                                  | Protection Method                                                                                         |
   +=======================+==============================================================================================================================================================================================================================================================================+===========================================================================================================+
   | External security     | Trojan horses or other viruses are common external security issues. To address these issues, you can choose services such as Host Security Service (HSS) based on your service requirements:                                                                                 | -  :ref:`Enabling HSS <en-us_topic_0000001194242043__section47861136153218>`                              |
   |                       |                                                                                                                                                                                                                                                                              | -  :ref:`Monitoring ECSs <en-us_topic_0000001194242043__section980811496326>`                             |
   |                       |                                                                                                                                                                                                                                                                              | -  :ref:`Backing Up Data Periodically <en-us_topic_0000001194242043__section10102957143212>`              |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
   | Internal security     | Incorrect ports opening may cause internal security issues. Improving the internal security is the key to improving the ECS security. If the internal security is not improved, external security solutions cannot effectively intercept and block various external attacks. | -  :ref:`Improving the Port Security <en-us_topic_0000001194242043__section136273234411>`                 |
   |                       |                                                                                                                                                                                                                                                                              | -  :ref:`Periodically Upgrading the Operating System <en-us_topic_0000001194242043__section235552519912>` |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000001194242043__section47861136153218:

Enabling HSS
------------

Host Security Service (HSS) is designed to improve the overall security for ECSs. It helps you identify and manage the assets on your servers, eliminate risks, and defend against intrusions and web page tampering. There are also advanced protection and security operations functions available to help you easily detect and handle threats.

Before using the HSS service, install the HSS agent on your ECSs first and you will be able to check the ECS security status and risks in a region on the HSS console.

We provide different methods for you to install the HSS agent depending on whether your ECSs are to be created or already exist.

-  **Scenario 1: An ECS is to be created.**

   When you use certain public images to create ECSs, you are advised to use HSS to protect your ECSs.

   Select one of the following options:

   -  **Advanced HSS edition (paid)**: You can choose the enterprise edition and you need to pay for it.
   -  **None**: HSS is disabled and servers are not protected.

   After you select an HSS edition, the system automatically installs the HSS agent, enables account cracking prevention, and offers host security functions.

-  **Scenario 2: An ECS is already created and HSS is not configured for it.**

   For an existing ECS without HSS configured, you can manually install an Agent on it.

   For details, see the *Host Security Service User Guide*.

.. _en-us_topic_0000001194242043__section980811496326:

Monitoring ECSs
---------------

Monitoring is key for ensuring ECS performance, reliability, and availability. Using monitored data, you can determine ECS resource utilization. The cloud platform provides Cloud Eye to help you obtain the running statuses of your ECSs. You can use Cloud Eye to automatically monitor ECSs in real time and manage alarms and notifications to keep track of ECS performance metrics.

Server monitoring includes basic monitoring, OS monitoring, and process monitoring for servers.

-  Basic monitoring

   Basic monitoring does not require the agent to be installed and automatically reports ECS metrics to Cloud Eye. Basic monitoring for KVM ECSs is performed every 5 minutes.

-  OS monitoring

   By installing the Agent on an ECS, OS monitoring provides system-wide, active, and fine-grained monitoring. OS monitoring for KVM ECSs is performed every minute.

   **To enable OS monitoring for a created ECS**:

   You need to manually install the agent.

   For instructions about how to install and configure the Agent, see `Agent Installation and Configuration <https://docs.otc.t-systems.com/cloud-eye/umn/server_monitoring/agent_installation_and_configuration.html#ces-01-0027>`__.

-  Process monitoring

   Process monitoring provides monitoring of active processes on ECSs and it requires the Agent to be installed on the ECSs to be monitored. Processes are monitored at an interval of 1 minute (for KVM ECSs).

After server monitoring is enabled, you can set ECS alarm rules to customize the monitored objects and notification policies and learn about the ECS running status at any time.

.. _en-us_topic_0000001194242043__section10102957143212:

Backing Up Data Periodically
----------------------------

Data backup is a process of storing all or part of data in different ways to prevent data loss. The following uses Cloud Backup and Recovery (CBR) as an example. For more backup methods, see :ref:`Overview <en-us_topic_0000001128445638>`.

CBR enables you to back up ECSs and disks with ease. In case of a virus attack, accidental deletion, or software or hardware fault, you can restore data to any point in the past when the data was backed up. CBR protects your services by ensuring the security and consistency of your data.

**To enable CBR when purchasing an ECS**:

Set CBR when purchasing an ECS. The system will associate the ECS with a cloud backup vault and the selected backup policy to periodically back up the ECS.

-  Create new

   #. Enter the name of the cloud backup vault. The name consists of 1 to 64 characters. Only letters, digits, underscores (_), and hyphens (-) are allowed. For example, **vault-f61e**. The default naming rule is **vault\_**\ *xxxx*.
   #. Enter the vault capacity, which is required for backing up the ECS. The vault capacity cannot be smaller than that of the ECS to be backed up. Its value ranges from the total capacity of the ECS to 10,485,760 in the unit of GB.
   #. Select a backup policy from the drop-down list, or log in to the CBR console and configure a desired one.

-  Use existing

   #. Select an existing cloud backup vault from the drop-down list.
   #. Select a backup policy from the drop-down list, or log in to the CBR console and configure a desired one.

-  Do not use

   Skip this configuration if CBR is not required. If you need to enable CBR after creating an ECS, log in to the CBR console, locate the target vault, and associate it with the ECS.

**To back up data for a created ECS**:

You can use the cloud server backup and cloud disk backup to :ref:`back up your ECS data <en-us_topic_0000001128445638>`.

-  Cloud server backup (recommended): Use this backup method if you want to back up the data of all EVS disks (system and data disks) attached to an ECS. This prevents data inconsistency caused by the time difference in creating a backup.
-  Cloud disk backup: Use this backup method if you want to back up the data of one or more EVS disks (system or data disk) attached to an ECS. This minimizes backup costs on the basis of data security.

.. _en-us_topic_0000001194242043__section136273234411:

Improving the Port Security
---------------------------

You can use security groups to protect the network security of your ECSs. A security group controls inbound and outbound traffic for your ECSs. Inbound traffic originates from the outside to the ECS, while outbound traffic originates from the ECS to the outside.

You can configure security group rules to grant access to or from specific ports. You are advised to disable high-risk ports and only enable necessary ports.

:ref:`Table 2 <en-us_topic_0000001194242043__table34831117171>` lists common high-risk ports. You are advised to change these ports to non-high-risk ports.

.. _en-us_topic_0000001194242043__table34831117171:

.. table:: **Table 2** Common high-risk ports

   +----------+-------------------------------------------------------------------------------------------------------------------------+
   | Protocol | Port                                                                                                                    |
   +==========+=========================================================================================================================+
   | TCP      | 42, 135, 137, 138, 139, 444, 445, 593, 1025, 1068, 1434, 3127, 3128, 3129, 3130, 4444, 4789, 5554, 5800, 5900, and 9996 |
   +----------+-------------------------------------------------------------------------------------------------------------------------+
   | UDP      | 135 to 139, 1026, 1027, 1028, 1068, 1433, 1434, 4789, 5554, and 9996                                                    |
   +----------+-------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000001194242043__section235552519912:

Periodically Upgrading the Operating System
-------------------------------------------

After ECSs are created, you need to maintain and periodically upgrade the operating system.
