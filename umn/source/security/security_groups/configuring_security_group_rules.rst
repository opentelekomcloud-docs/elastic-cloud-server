:original_name: en-us_topic_0030878383.html

.. _en-us_topic_0030878383:

Configuring Security Group Rules
================================

Scenarios
---------

Similar to firewall, a security group is a logical group used to control network access. You can define access rules for a security group to protect the ECSs that are added to this security group.

-  Inbound: Inbound rules allow external network traffic to be sent to the ECSs in the security group.
-  Outbound: Outbound rules allow network traffic from the ECSs in the security group to be sent out of the security group.

For details about the default security group rules, see *Virtual Private Cloud User Guide*. For details about configuration examples for security group rules, see :ref:`Security Group Configuration Examples <en-us_topic_0140323152>`.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the **Elastic Cloud Server** page, click the name of the target ECS.

   The page providing details about the ECS is displayed.

#. Click the **Security Groups** tab, expand the information of the security group, and view security group rules.

#. Click the security group ID.

   The system automatically switches to the security group details page.

#. On the **Inbound Rules** tab, click **Add Rule**.

   The **Add Inbound Rule** dialog box is displayed.

#. Configure required parameters.

   You can click **+** to add more inbound rules.


   .. figure:: /_static/images/en-us_image_0000002076474708.png
      :alt: **Figure 1** Adding inbound rules

      **Figure 1** Adding inbound rules

   .. table:: **Table 1** Inbound rule parameter description

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                   | Example Value         |
      +=======================+===============================================================================================================================================================================================================================================================================================================================================================+=======================+
      | Protocol              | The network protocol used to match traffic in a security group rule.                                                                                                                                                                                                                                                                                          | TCP                   |
      |                       |                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | Currently, the value can be **All**, **TCP**, **UDP**, **GRE**, **ICMP**, or more.                                                                                                                                                                                                                                                                            |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Port                  | The port or port range over which traffic can reach your ECS. The value can be from 1 to 65535.                                                                                                                                                                                                                                                               | 22, or 22-30          |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Type                  | Source IP address version. You can select:                                                                                                                                                                                                                                                                                                                    | IPv4                  |
      |                       |                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | -  IPv4                                                                                                                                                                                                                                                                                                                                                       |                       |
      |                       | -  IPv6                                                                                                                                                                                                                                                                                                                                                       |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source                | Source of the security group rule. The value can be an IP address or a security group to allow access from IP addresses or instances in the security group.                                                                                                                                                                                                   | 0.0.0.0/0             |
      |                       |                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | -  IP address:                                                                                                                                                                                                                                                                                                                                                |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       |    -  Single IP address: 192.168.10.10/32                                                                                                                                                                                                                                                                                                                     |                       |
      |                       |    -  All IP addresses: 0.0.0.0/0                                                                                                                                                                                                                                                                                                                             |                       |
      |                       |    -  IP address range: 192.168.1.0/24                                                                                                                                                                                                                                                                                                                        |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | -  **Security group**: The source is from another security group. You can select a security group in the same region from the drop-down list. If there is instance A in security group A and instance B in security group B, and the inbound rule of security group A allows traffic from security group B, traffic is allowed from instance B to instance A. |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | If the source is a security group, this rule will apply to all instances associated with the selected security group.                                                                                                                                                                                                                                         |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the security group rule. This parameter is optional.                                                                                                                                                                                                                                                                          | ``-``                 |
      |                       |                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                                                                                                                                                                                                           |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

   The inbound rule list is displayed.

#. On the **Outbound Rules** tab, click **Add Rule**.

   The **Add Outbound Rule** dialog box is displayed.

#. Configure required parameters.

   You can click **+** to add more outbound rules.


   .. figure:: /_static/images/en-us_image_0000002076320880.png
      :alt: **Figure 2** Adding outbound rules

      **Figure 2** Adding outbound rules

   .. table:: **Table 2** Outbound rule parameter description

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                   | Example Value         |
      +=======================+===============================================================================================================================================================================================================================================================================================================================================================+=======================+
      | Protocol              | The network protocol used to match traffic in a security group rule.                                                                                                                                                                                                                                                                                          | TCP                   |
      |                       |                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | Currently, the value can be **All**, **TCP**, **UDP**, **GRE**, **ICMP**, or more.                                                                                                                                                                                                                                                                            |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Port                  | The port or port range over which traffic can leave your ECS. The value can be from 1 to 65535.                                                                                                                                                                                                                                                               | 22, or 22-30          |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Type                  | Source IP address version. You can select:                                                                                                                                                                                                                                                                                                                    | IPv4                  |
      |                       |                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | -  IPv4                                                                                                                                                                                                                                                                                                                                                       |                       |
      |                       | -  IPv6                                                                                                                                                                                                                                                                                                                                                       |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Destination           | Destination of the security group rule. The value can be an IP address or a security group to allow access to IP addresses or instances in the security group.                                                                                                                                                                                                | 0.0.0.0/0             |
      |                       |                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | -  IP address:                                                                                                                                                                                                                                                                                                                                                |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       |    -  Single IP address: 192.168.10.10/32                                                                                                                                                                                                                                                                                                                     |                       |
      |                       |    -  All IP addresses: 0.0.0.0/0                                                                                                                                                                                                                                                                                                                             |                       |
      |                       |    -  IP address range: 192.168.1.0/24                                                                                                                                                                                                                                                                                                                        |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | -  **Security group**: The source is from another security group. You can select a security group in the same region from the drop-down list. If there is instance A in security group A and instance B in security group B, and the inbound rule of security group A allows traffic from security group B, traffic is allowed from instance B to instance A. |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the security group rule. This parameter is optional.                                                                                                                                                                                                                                                                          | ``-``                 |
      |                       |                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                                                                                                                                                                                                           |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK** to complete the security rule configuration.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
