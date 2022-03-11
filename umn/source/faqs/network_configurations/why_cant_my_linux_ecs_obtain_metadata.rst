Why Can't My Linux ECS Obtain Metadata?
=======================================

Symptom
-------

The security group of the Linux ECS has been configured based on the prerequisites in `Obtaining Metadata <../../instances/obtaining_metadata_and_passing_user_data/obtaining_metadata.html>`__ in the outbound direction, but the ECS still cannot obtain the metadata through the route with the destination of 169.254.169.254.

Root Cause
----------

Run the following command on the Linux ECS configured with a static IP address:

**#** **ip route\| grep 169.254**

The route with the destination of 169.254.169.254 does not exist, but the route with the destination of 169.254.0.0/16 exists.

| **Figure 1** Route information
| |image1|

After the network is restarted, the original route with the destination of 169.254.169.254 is changed to the route with the destination of 169.254.0.0/16 without a next hop. As a result, the Linux ECS cannot obtain metadata.

Solution
--------

#. Add the route with the destination of 169.254.169.254, and specify the next hop (gateway) and the output device (primary NIC of the Linux ECS). The following is an example:

   **# ip route add 169.254.169.254 via** **192.168.1.1** **dev** **eth0**

   192.168.1.1 is the gateway address of the subnet that the primary NIC resides, and eth0 is the primary NIC.

#. Run the following command to verify that the metadata can be obtained:

   **# curl** **http://169.254.169.254**

   | **Figure 2** Obtaining metadata
   | |image2|

3. Run the following command to create or modify the **/etc/sysconfig/network-scripts/route-eth0** file to prevent the static route from being changed after network restart:

   **# vi /etc/sysconfig/network-scripts/route-eth0**

   Add the following content to the file:

   In this example, the primary NIC is eth0 and gateway address is 192.168.1.1. Replace them based on site requirements.

   **# 169.254.169.254 via 192.168.1.1**



.. |image1| image:: /_static/images/en-us_image_0000001092174258.png

.. |image2| image:: /_static/images/en-us_image_0000001092045958.png
   :class: imgResize

