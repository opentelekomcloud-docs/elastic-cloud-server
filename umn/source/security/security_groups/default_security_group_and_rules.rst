Default Security Group and Rules
================================

Your account automatically comes with a default security group. The default security group allows all outbound traffic, denies all inbound traffic, and allows all traffic between cloud resources in the group. Your cloud resources in this security group can communicate with each other already without adding additional rules.

Figure 1 shows the default security group.

.. figure:: /_static/images/en-us_image_0000001230120807.png
   :alt: Click to enlarge
   :figclass: imgResize


   **Figure 1** Default security group

`Table 1 <#enustopic0140323154table542641118503>`__ describes the rules for the default security group.



.. _ENUSTOPIC0140323154table542641118503:

.. table:: **Table 1** Default security group rules

   +-----------+----------+--------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Direction | Protocol | Port / Range | Source / Destination                                         | Description                                                                                                        |
   +===========+==========+==============+==============================================================+====================================================================================================================+
   | Outbound  | All      | All          | Destination: 0.0.0.0/0                                       | Allows all outbound traffic.                                                                                       |
   +-----------+----------+--------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Inbound   | All      | All          | Source: the current security group (for example, sg-*xxxxx*) | Allows communications among ECSs within the security group and denies all inbound traffic (incoming data packets). |
   +-----------+----------+--------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+


