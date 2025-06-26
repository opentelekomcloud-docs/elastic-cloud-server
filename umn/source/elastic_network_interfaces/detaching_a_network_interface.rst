:original_name: en-us_topic_0093492519.html

.. _en-us_topic_0093492519:

Detaching a Network Interface
=============================

Scenarios
---------

An ECS can have a maximum of 12 network interfaces, including a primary network interface that cannot be detached. This section describes how to detach an extension network interface.

.. caution::

   Detaching a networking interface may cause network interruptions. Evaluate the impact in advance and exercise caution when performing this operation.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the ECS list, click the name of the ECS from which you want to detach a network interface

   The page providing details about the ECS is displayed.

#. On the **Network Interfaces** tab, locate the target network interface and click **Detach**.

   .. note::

      You are not allowed to detach the primary network interface (the first one displayed in the network interface list).

#. In the displayed dialog box, click **OK**.

   .. note::

      Certain ECSs do not support network interface detachment when they are running. For details, see the GUI display. To detach a network interface from such an ECS, stop the ECS first.

.. |image1| image:: /_static/images/en-us_image_0093507592.png
