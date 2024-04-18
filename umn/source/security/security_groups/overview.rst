:original_name: en-us_topic_0140323157.html

.. _en-us_topic_0140323157:

Overview
========

Security Group
--------------

A security group is a collection of access control rules for ECSs that have the same security protection requirements and that are mutually trusted. After a security group is created, you can create various access rules for the security group, these rules will apply to all ECSs added to this security group.

You can also customize a security group or use the default one. The system provides a default security group for you, which permits all outbound traffic and denies inbound traffic. ECSs in a security group are accessible to each other. For details about the default security group, see :ref:`Default Security Group and Rules <en-us_topic_0140323154>`.

.. note::

   If two ECSs are in the same security group but in different VPCs, the security group does not take effect. You can use a VPC peering connection to connect the two VPCs first.

Security Group Rules
--------------------

After a security group is created, you can add rules to the security group. A rule applies either to inbound traffic (ingress) or outbound traffic (egress). After ECSs are added to the security group, they are protected by the rules of that group.

Each security group has default rules. For details, see :ref:`Default Security Group and Rules <en-us_topic_0140323154>`. You can also customize security group rules. For details, see :ref:`Configuring Security Group Rules <en-us_topic_0030878383>`.

Security Group Constraints
--------------------------

-  By default, you can create a maximum of 100 security groups in your cloud account.
-  By default, you can add up to 50 security group rules to a security group.
