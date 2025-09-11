:original_name: en-us_topic_0140323154.html

.. _en-us_topic_0140323154:

Default Security Groups and Rules
=================================

Note the following when using default security group rules:

-  **Inbound rules** control incoming traffic to instances in the default security group. The instances can communicate with each other but cannot be accessed from external networks.
-  **Outbound rules** allow all traffic from the instances in the default security group to external networks.

:ref:`Figure 1 <en-us_topic_0140323154__fig11890174421819>` shows the default security group.

.. _en-us_topic_0140323154__fig11890174421819:

.. figure:: /_static/images/en-us_image_0000001230120807.png
   :alt: **Figure 1** Default security group

   **Figure 1** Default security group

:ref:`Table 1 <en-us_topic_0140323154__table542641118503>` describes the default security group rules.

.. _en-us_topic_0140323154__table542641118503:

.. table:: **Table 1** Default security group rules

   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Direction | Protocol | Port/Range | Source/Destination                                           | Description                                                                                                        |
   +===========+==========+============+==============================================================+====================================================================================================================+
   | Outbound  | All      | All        | Destination: 0.0.0.0/0                                       | Allows all outbound traffic.                                                                                       |
   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Inbound   | All      | All        | Source: the current security group (for example, sg-*xxxxx*) | Allows communications among ECSs within the security group and denies all inbound traffic (incoming data packets). |
   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
