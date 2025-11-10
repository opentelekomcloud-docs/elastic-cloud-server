:original_name: en-us_topic_0163572590.html

.. _en-us_topic_0163572590:

Step 2: Configure Network Settings
==================================

Network Settings
----------------

#. Set **Network** by selecting an available VPC and subnet from the drop-down list and specifying a private IP address assignment mode.

   VPC provides a dedicated network for your ECS. A VPC can contain subnets for further isolation. You can configure security groups per subnet to control access to cloud resources.

   You can select an existing VPC or create a new one.

   For more information about VPC, see *Virtual Private Cloud User Guide*.

   .. note::

      -  Ensure that DHCP is enabled in the VPC which the ECS belongs to.
      -  When you use VPC for the first time, the system automatically creates a VPC for you, including the security group and NIC.

#. (Optional) Set **Extension NIC**. You can add multiple extension NICs to an ECS and specify IP addresses for them (including primary NICs).

   .. note::

      If you specify an IP address for a NIC when creating multiple ECSs in a batch:

      -  This IP address serves as the start IP address.
      -  Ensure that the IP addresses required by the NICs are within the subnet, consecutive, and available.
      -  The subnet with the specified IP address cannot overlap with other subnets.

#. Set **Security Group** by selecting an available security group from the drop-down list or creating a new one.

   A security group controls ECS access within or between security groups by defining access rules. This enhances ECS security.

   When creating an ECS, you can select multiple (recommended not more than five) security groups. In such a case, the access rules of all the selected security groups apply on the ECS.

   .. note::

      Before initializing an ECS, ensure that the security group rules for the outbound direction meet the following requirements:

      -  Protocol & Port: TCP
      -  Port: 80
      -  Destination: 169.254.0.0/16

      If you use the default security group rules for the outbound direction, the preceding requirements are met, and the ECS can be initialized. The default security group rules for the outbound direction are as follows:

      -  Protocol & Port: All
      -  Port range: All ports
      -  Destination: 0.0.0.0/0

#. Set **EIP**.

   An EIP is a static public IP address bound to an ECS in a VPC. Using the EIP, the ECS can provide services externally.

   The following options are provided:

   -  Auto assign

      The system automatically assigns an EIP with exclusive bandwidth for each ECS. You can set the bandwidth as required.

   -  Use existing

      An existing EIP is assigned for the ECS. When using an existing EIP, you are not allowed to create ECSs in a batch.

   -  Do not use

      Without an EIP, the ECS cannot access the Internet and is used in the private network or cluster only.

#. Set **Bandwidth Size**.

   Select the bandwidth based on service requirements. The unit is Mbit/s.

#. Click **Next: Configure Advanced Settings**.
