:original_name: en-us_topic_0018078505.html

.. _en-us_topic_0018078505:

Why Can I Remotely Access an ECS But Cannot Ping It?
====================================================

Symptom
-------

You can remotely access an ECS but when you ping the EIP bound to the ECS, the ping operation fails.

Possible Causes
---------------

A desired inbound rule is not added for the security group, and ICMP is not enabled.

Solution
--------

#. Log in to the management console.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the **Elastic Cloud Server** page, click the name of the target ECS.

   The page providing details about the ECS is displayed.

#. Click the **Security Groups** tab, expand the information of the security group, and click the security group ID.

#. On the **Inbound Rules** tab of the **Security Group** page, click **Add Rule**.

#. Add an inbound rule for the security group and enable ICMP.

   -  **Protocol**: **ICMP**
   -  **Source**: **IP address** **0.0.0.0/0**
