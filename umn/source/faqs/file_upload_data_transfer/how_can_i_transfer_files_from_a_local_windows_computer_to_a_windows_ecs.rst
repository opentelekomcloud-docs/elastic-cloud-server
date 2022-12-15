:original_name: en-us_topic_0166284970.html

.. _en-us_topic_0166284970:

How Can I Transfer Files from a Local Windows Computer to a Windows ECS?
========================================================================

Scenarios
---------

You want to transfer files from a local Windows computer to a Windows ECS through an MSTSC-based remote desktop connection.

Prerequisites
-------------

-  The target ECS is running.
-  An EIP has been bound to the ECS. For details, see :ref:`Binding an EIP <en-us_topic_0174917535>`.

-  Access to port 3389 is allowed in the inbound direction of the security group to which the ECS belongs. For details, see :ref:`Configuring Security Group Rules <en-us_topic_0030878383>`.

Solution
--------

#. On the local Windows computer, click **Start**. In the **Search programs and files** text box, enter **mstsc**.

   The **Remote Desktop Connection** window is displayed.

#. Click **Options**.

   |image1|

#. On the **General** tab, enter the EIP bound to the ECS and username **Administrator** for logging in to the ECS.

   |image2|

#. Click the **Local Resources** tab and verify that **Clipboard** is selected in the **Local devices and resources** pane.

   |image3|

#. Click **More**.

#. In the **Drives** pane, select the local disk where the file to be transferred to the Windows ECS is located.

   |image4|

#. Click **OK** and log in to the Windows ECS.

#. Choose **Start** > **Computer**.

   The local disk is displayed on the Windows ECS.

#. Double-click the local disk to access it and copy the file to be transferred to the Windows ECS.

.. |image1| image:: /_static/images/en-us_image_0166287347.png
.. |image2| image:: /_static/images/en-us_image_0166287348.png
.. |image3| image:: /_static/images/en-us_image_0166287349.png
.. |image4| image:: /_static/images/en-us_image_0166287351.png
