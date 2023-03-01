:original_name: en-us_topic_0140323154.html

.. _en-us_topic_0140323154:

Default Security Group and Rules
================================

The system creates a default security group for each account. By default, the default security group rules:

-  Allow all outbound packets: Instances in the default security group can send requests to and receive responses from instances in other security groups.
-  Deny all inbound packets: Requests from instances in other security groups will be denied by the default security group.

:ref:`Figure 1 <en-us_topic_0140323154__fig11890174421819>` shows the default security group.

.. _en-us_topic_0140323154__fig11890174421819:

.. figure:: /_static/images/en-us_image_0000001230120807.png
   :alt: **Figure 1** Default security group

   **Figure 1** Default security group

:ref:`Table 1 <en-us_topic_0140323154__table542641118503>` describes the rules for the default security group.

.. _en-us_topic_0140323154__table542641118503:

.. table:: **Table 1** Default security group rules

   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Direction | Protocol | Port/Range | Source/Destination                                           | Description                                                                                                        |
   +===========+==========+============+==============================================================+====================================================================================================================+
   | Outbound  | All      | All        | Destination: 0.0.0.0/0                                       | Allows all outbound traffic.                                                                                       |
   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Inbound   | All      | All        | Source: the current security group (for example, sg-*xxxxx*) | Allows communications among ECSs within the security group and denies all inbound traffic (incoming data packets). |
   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
