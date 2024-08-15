:original_name: en-us_topic_0140323154.html

.. _en-us_topic_0140323154:

Default Security Groups and Rules
=================================

Note the following when using default security group rules:

-  Inbound rules control incoming traffic to instances in the default security group. The instances can only communicate with each other but cannot be accessed from external networks.
-  Outbound rules allow all traffic from the instances in the default security group to external networks.

:ref:`Figure 1 <en-us_topic_0140323154__fig11890174421819>` shows the default security group.

.. _en-us_topic_0140323154__fig11890174421819:

.. figure:: /_static/images/en-us_image_0000001230120807.png
   :alt: **Figure 1** Default security group

   **Figure 1** Default security group

.. note::

   -  You cannot delete the default security group, but you can modify existing rules or add rules to the group.
   -  The default security group is automatically created to simplify the process of creating an instance for the first time. The default security group denies all external requests. To log in to an instance, add a security group rule by referring to :ref:`Remotely Logging In to an ECS from a Local Server <en-us_topic_0140323152__en-us_topic_0118534011_section14933617154810>`.

:ref:`Table 1 <en-us_topic_0140323154__table542641118503>` describes the rules in the default security group.

.. _en-us_topic_0140323154__table542641118503:

.. table:: **Table 1** Default security group rules

   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Direction | Protocol | Port/Range | Source/Destination                                           | Description                                                                                                        |
   +===========+==========+============+==============================================================+====================================================================================================================+
   | Outbound  | All      | All        | Destination: 0.0.0.0/0                                       | Allows all outbound traffic.                                                                                       |
   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Inbound   | All      | All        | Source: the current security group (for example, sg-*xxxxx*) | Allows communications among ECSs within the security group and denies all inbound traffic (incoming data packets). |
   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
