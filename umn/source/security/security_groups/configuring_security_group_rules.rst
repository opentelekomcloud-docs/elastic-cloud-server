Configuring Security Group Rules
================================

Scenarios
---------

Similar to firewall, a security group is a logical group used to control network access. You can define access rules for a security group to protect the ECSs that are added to this security group.

-  Inbound: Inbound rules allow external network traffic to be sent to the ECSs in the security group.
-  Outbound: Outbound rules allow network traffic from the ECSs in the security group to be sent out of the security group.

For details about the default security group rules, see *Virtual Private Cloud User Guide*. For details about configuration examples for security group rules, see `Security Group Configuration Examples <../../security/security_groups/security_group_configuration_examples.html>`__.

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

#. On the **Inbound Rules** tab, click **Add Rule**. In the displayed dialog box, set required parameters to add an inbound rule.

   You can click **+** to add more inbound rules.

   .. figure:: /_static/images/en-us_image_0284920908.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 1** Add Inbound Rule

   

.. _ENUSTOPIC0030878383enustopic0118534005table111445216564:

   .. table:: **Table 1** Inbound rule parameter description

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | **Parameter**         | **Description**                                                                                                                                                                      | **Example Value**     |
      +=======================+======================================================================================================================================================================================+=======================+
      | Protocol & Port       | **Protocol**: The network protocol. Currently, the value can be **All**, **TCP**, **UDP**, **ICMP**, **GRE**, or others.                                                             | TCP                   |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      |                       | **Port**: The port or port range over which the traffic can reach your ECS. The value ranges from 1 to 65535.                                                                        | 22, or 22-30          |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source                | The source of the security group rule. The value can be a single IP address or a security group to allow access from the IP address or instances in the security group. For example: | 0.0.0.0/0             |
      |                       |                                                                                                                                                                                      |                       |
      |                       | -  xxx.xxx.xxx.xxx/32 (IPv4 address)                                                                                                                                                 |                       |
      |                       | -  xxx.xxx.xxx.0/24 (IP address range)                                                                                                                                               |                       |
      |                       | -  0.0.0.0/0 (all IP addresses)                                                                                                                                                      |                       |
      |                       | -  sg-abc (security group)                                                                                                                                                           |                       |
      |                       |                                                                                                                                                                                      |                       |
      |                       | If the source is a security group, this rule will apply to all instances associated with the selected security group.                                                                |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the security group rule. This parameter is optional.                                                                                                 | N/A                   |
      |                       |                                                                                                                                                                                      |                       |
      |                       | The security group rule description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                              |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. On the **Outbound Rules** tab, click **Add Rule**. In the displayed dialog box, set required parameters to add an outbound rule.

   You can click **+** to add more outbound rules.

   .. figure:: /_static/images/en-us_image_0284993717.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 2** Add Outbound Rule

   

.. _ENUSTOPIC0030878383enustopic0118534005table0614192319232:

   .. table:: **Table 2** Outbound rule parameter description

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | **Parameter**         | **Description**                                                                                                                                                                         | **Example Value**     |
      +=======================+=========================================================================================================================================================================================+=======================+
      | Protocol & Port       | **Protocol**: The network protocol. Currently, the value can be **All**, **TCP**, **UDP**, **ICMP**, **GRE**, or others.                                                                | TCP                   |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      |                       | **Port**: The port or port range over which the traffic can leave your ECS. The value ranges from 1 to 65535.                                                                           | 22, or 22-30          |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Destination           | The destination of the security group rule. The value can be a single IP address or a security group to allow access to the IP address or instances in the security group. For example: | 0.0.0.0/0             |
      |                       |                                                                                                                                                                                         |                       |
      |                       | -  xxx.xxx.xxx.xxx/32 (IPv4 address)                                                                                                                                                    |                       |
      |                       | -  xxx.xxx.xxx.0/24 (IP address range)                                                                                                                                                  |                       |
      |                       | -  0.0.0.0/0 (all IP addresses)                                                                                                                                                         |                       |
      |                       | -  sg-abc (security group)                                                                                                                                                              |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the security group rule. This parameter is optional.                                                                                                    | N/A                   |
      |                       |                                                                                                                                                                                         |                       |
      |                       | The security group rule description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                 |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK** to complete the security rule configuration.



.. |image1| image:: /_static/images/en-us_image_0210779229.png

