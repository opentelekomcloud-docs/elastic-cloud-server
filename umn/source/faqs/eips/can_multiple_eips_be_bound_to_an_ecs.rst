:original_name: en-us_topic_0018073216.html

.. _en-us_topic_0018073216:

Can Multiple EIPs Be Bound to an ECS?
=====================================

Scenarios
---------

Multiple EIPs can be bound to an ECS, but this operation is not recommended.

If an ECS has multiple NICs attached and you want to bind multiple EIPs to this ECS, you need to configure policy-based routes for these NICs so that these extension NICs can communicate with external works. For details, see :ref:`Configuration Example <en-us_topic_0018073216__section32091531162222>`.

.. _en-us_topic_0018073216__section32091531162222:

Configuration Example
---------------------

:ref:`Table 1 <en-us_topic_0018073216__table10449199163243>` lists ECS configurations.

.. _en-us_topic_0018073216__table10449199163243:

.. table:: **Table 1** ECS configurations

   ============= ================
   Parameter     Configuration
   ============= ================
   Name          ecs_test
   Image         CentOS 6.5 64bit
   EIP           2
   Primary NIC   eth0
   Secondary NIC eth1
   ============= ================

**Example 1:**

If you intend to access public network 11.11.11.0/24 through standby NIC **eth1**, perform the following operations to configure a route:

#. Log in to the ECS.

#. Run the following command to configure a route:

   **ip route add 11.11.11.0/24 dev eth1 via 192.168.2.1**

   In the preceding command, **192.168.2.1** is the gateway IP address of standby NIC **eth1**.

**Example 2:**

Based on example 1, if you intend to enable routing for default public network traffic through standby NIC **eth1**, perform the following operations to configure a route:

#. Log in to the ECS.

#. Run the following command to delete the default route:

   **ip route delete default**

   .. important::

      Exercise caution when deleting the default route because this operation will interrupt the network and result in SSH login failures.

#. Run the following command to configure a new default route:

   **ip route add 0.0.0.0/0 dev eth1 via 192.168.2.1**

   In the preceding command, **192.168.2.1** is the gateway IP address of standby NIC **eth1**.
