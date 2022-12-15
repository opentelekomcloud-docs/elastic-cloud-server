:original_name: en-us_topic_0030013188.html

.. _en-us_topic_0030013188:

Can an ECS Without an EIP Bound Access the Internet?
====================================================

Yes.

-  Method 1: Configure a SNAT server.

   You can configure the SNAT server so that the ECS without an EIP bound can access the Internet.

   For details, see `"Configuring an SNAT Server" <https://docs.otc.t-systems.com/en-us/usermanual/vpc/vpc_route_0004.html>`__ in *Virtual Private Cloud User Guide*.

-  Method 2: Create a NAT gateway.

   If a large number of concurrent connections are required, it is a good practice to use the NAT Gateway service provided by the cloud platform.

   The NAT Gateway service offers the NAT function for ECSs in a VPC, allowing these ECSs to access the Internet using an EIP. For more information about NAT Gateway, see *NAT Gateway User Guide*.
