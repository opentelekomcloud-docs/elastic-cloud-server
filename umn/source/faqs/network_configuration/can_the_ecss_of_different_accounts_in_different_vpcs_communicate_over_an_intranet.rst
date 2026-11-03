:original_name: en-us_topic_0018078501.html

.. _en-us_topic_0018078501:

Can the ECSs of Different Accounts in Different VPCs Communicate over an Intranet?
==================================================================================

No. The ECSs of different accounts in different VPCs cannot communicate with each other over an intranet.

To enable the communication over an intranet, use the methods provided in the following table.

+-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Scenario              | Billing               | Method                                                                                                                                                            |
+=======================+=======================+===================================================================================================================================================================+
| In the same region    | Free of charge        | Use VPC peering to enable the communication over an intranet.                                                                                                     |
|                       |                       |                                                                                                                                                                   |
|                       |                       | -  `VPC Peering Connection Overview <https://docs.otc.t-systems.com/en-us/usermanual/vpc/en-us_topic_0046655036.html>`__                                          |
|                       |                       | -  `Creating a VPC Peering Connection with a VPC in Another Account <https://docs.otc.t-systems.com/en-us/usermanual/vpc/en-us_topic_0046655038.html>`__          |
+-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| In the same region    | Billed                | Use VPC Endpoint to enable the communication over an intranet.                                                                                                    |
|                       |                       |                                                                                                                                                                   |
|                       |                       | -  `What Is VPC Endpoint? <https://docs.otc.t-systems.com/en-us/usermanual/vpcep/en-us_topic_0131645194.html>`__                                                  |
|                       |                       | -  `Configuring a VPC Endpoint for Communications Across VPCs of Different Accounts <https://docs.otc.t-systems.com/en-us/usermanual/vpcep/vpcep_02_0203.html>`__ |
|                       |                       | -  `What Are the Differences Between VPC Endpoints and VPC Peering Connections? <https://docs.otc.t-systems.com/en-us/usermanual/vpcep/vpcep_04_0004.html>`__     |
+-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| In different regions  | Billed                | Use VPN to enable the communication over an intranet.                                                                                                             |
|                       |                       |                                                                                                                                                                   |
|                       |                       | -  `What Is VPN? <https://docs.otc.t-systems.com/en-us/usermanual/vpn/en-us_topic_0035391393.html>`__                                                             |
+-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
