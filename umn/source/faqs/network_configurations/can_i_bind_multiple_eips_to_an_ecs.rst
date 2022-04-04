Can I Bind Multiple EIPs to an ECS?
===================================

Scenarios
---------

You can bind multiple EIPs to an ECS. However, this configuration is not recommended.

To bind multiple EIPs to an ECS, you must manually configure routes.

Configuration Example
---------------------

`Table 1 <#enustopic0018073216table10449199163243>`__ lists ECS configurations.



.. _ENUSTOPIC0018073216table10449199163243:

.. container:: table-responsive

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

If you are required to access public network 11.11.11.0/24 through standby NIC **eth1**, perform the following operations to configure a route:

#. Log in to the ECS.

#. Run the following command to configure a route:

   **ip route add 11.11.11.0/24 dev eth1 via 192.168.2.1**

   In the preceding command, **192.168.2.1** is the gateway IP address of standby NIC **eth1**.

**Example 2:**

Based on example 1, if you are required to enable routing for default public network traffic through standby NIC **eth1**, perform the following operations to configure a route:

#. Log in to the ECS.

#. Run the following command to delete the default route:

   **ip route delete default**

#. Run the following command to configure a new default route:

   **ip route add 0.0.0.0/0 dev eth1 via 192.168.2.1**

   In the preceding command, **192.168.2.1** is the gateway IP address of standby NIC **eth1**.


