Default Security Group and Rules
================================

Your account automatically comes with a default security group. The default security group allows all outbound traffic, denies all inbound traffic, and allows all traffic between cloud resources in the group. Your cloud resources in this security group can communicate with each other already without adding additional rules.

`Figure 1 <#EN-US_TOPIC_0140323154__fig11890174421819>`__ shows the default security group.

| **Figure 1** Default security group
| |image1|

`Table 1 <#EN-US_TOPIC_0140323154__table542641118503>`__ describes the rules for the default security group.



.. _EN-US_TOPIC_0140323154__table542641118503:

.. table:: **Table 1** Default security group rules

   +-----------+----------+------------+------------------------------------+--------------------------------------+
   | Direction | Protocol | Port/Range | Source/Destination                 | Description                          |
   +===========+==========+============+====================================+======================================+
   | Outbound  | All      | All        | Destination: 0.0.0.0/0             | Allows all outbound traffic.         |
   +-----------+----------+------------+------------------------------------+--------------------------------------+
   | Inbound   | All      | All        | Source: the current security group | Allows communications among ECSs     |
   |           |          |            | (for example, sg-*xxxxx*)          | within the security group and denies |
   |           |          |            |                                    | all inbound traffic (incoming data   |
   |           |          |            |                                    | packets).                            |
   +-----------+----------+------------+------------------------------------+--------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001230120807.png
   :class: imgResize
