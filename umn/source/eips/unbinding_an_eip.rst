:original_name: en-us_topic_0240543420.html

.. _en-us_topic_0240543420:

Unbinding an EIP
================

Scenarios
---------

This section describes how to unbind an EIP from an ECS.

.. caution::

   After an EIP is unbound from an ECS, the ECS can no longer access the public network. Before unbinding an EIP, ensure that the ECS does not need to access the public network or an alternative network connection is available.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the ECS list on the **Elastic Cloud Server** page, click the name of the target ECS.

   The ECS details page is displayed.

#. On the **EIPs** tab, locate the row containing the EIP to be unbound and click **Unbind**.


   .. figure:: /_static/images/en-us_image_0000002351518800.png
      :alt: **Figure 1** Unbinding an EIP

      **Figure 1** Unbinding an EIP

#. Confirm the EIP to be unbound and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000002188678994.png
