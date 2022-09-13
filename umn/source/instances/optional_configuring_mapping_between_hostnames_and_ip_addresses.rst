:original_name: en-us_topic_0074752335.html

.. _en-us_topic_0074752335:

(Optional) Configuring Mapping Between Hostnames and IP Addresses
=================================================================

ECSs in the same VPC can communicate with each other using hostnames. In such a case, you are required to configure the mapping between hostnames and IP addresses. The communication using hostnames is more convenient than that using IP addresses.

Constraints
-----------

This method applies only to Linux ECSs.

Procedure
---------

For example, there are two ECSs in a VPC, ecs-01 and ecs-02. Perform the following operations to enable communication using hostnames between ecs-01 and ecs-02:

#. Log in to ecs-01 and ecs-02 and obtain their private IP addresses.

   a. Log in to the management console.

   b. Under **Computing**, click **Elastic Cloud Server**.

   c. On the **Elastic Cloud Server** page, obtain the private IP address in the **IP Address** column.

      For example, the obtained private IP addresses are as follows:

      ecs-01: 192.168.0.1

      ecs-02: 192.168.0.2

#. Obtain the hostnames for the two ECSs.

   a. Log in to an ECS.

   b. Run the following command to view the ECS hostname:

      **sudo hostname**

      For example, the obtained hostnames are as follows:

      ecs-01: hostname01

      ecs-02: hostname02

#. Create a mapping between the hostnames and IP addresses and add information about other ECSs in the same VPC.

   a. Log in to ecs-01.

   b. .. _en-us_topic_0074752335__li6087483710276:

      Run the following command to switch to user **root**:

      **sudo su -**

   c. Run the following command to edit the hosts configuration file:

      **vi /etc/hosts**

   d. Press **i** to enter editing mode.

   e. Add the statement in the following format to set up the mapping:

      *Private IP address hostname*

      For example, add the following statement:

      192.168.0.1 hostname01

      192.168.0.2 hostname02

   f. Press **Esc** to exit editing mode.

   g. .. _en-us_topic_0074752335__li64061240102622:

      Run the following command to save the configuration and exit:

      **:wq**

   h. Log in to ecs-02.

   i. Repeat :ref:`3.b <en-us_topic_0074752335__li6087483710276>` to :ref:`3.g <en-us_topic_0074752335__li64061240102622>`.

#. Check whether the ECSs can communicate with each other using hostnames.

   Log in to an ECS in the same VPC, run the following command to ping the added host, and check whether the operation is successful:

   **ping** *Hostname*
