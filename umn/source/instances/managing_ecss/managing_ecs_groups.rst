.. _en-us_topic_0032980085:

Managing ECS Groups
===================

Scenarios
---------

An ECS group allows you to create ECSs on different physical servers, thereby improving service reliability. This function does not apply to existing ECSs. You cannot add existing ECSs to an ECS group.

Notes
-----

An existing ECS cannot be added to an ECS group.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the navigation pane on the left, choose **ECS Group**.

#. On the **ECS Group** page, click **Create ECS Group**.

#. Enter the name of the target ECS group.

   The **Anti-affinity** policy is used by default.

#. Click **OK**.

Follow-up Procedure
-------------------

Add an ECS to an ECS group only when creating the ECS.

To do so, expand **Advanced Options** and select the target ECS group.

.. |image1| image:: /_static/images/en-us_image_0210779229.png

