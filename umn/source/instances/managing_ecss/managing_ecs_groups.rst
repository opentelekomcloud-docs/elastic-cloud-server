:original_name: en-us_topic_0032980085.html

.. _en-us_topic_0032980085:

Managing ECS Groups
===================

Scenarios
---------

An ECS group logically groups ECSs. ECSs in an ECS group comply with the same policy associated with the ECS group.

Currently, only the anti-affinity policy is supported.

You can perform the following operations on an ECS group:

-  :ref:`Creating an ECS Group <en-us_topic_0032980085__section1464061364114>`
-  :ref:`Adding an ECS to an ECS Group <en-us_topic_0032980085__section1447818554481>`

   -  Add an ECS to an ECS group during ECS creation.

      For details, see :ref:`Step 3: Configure Advanced Settings <en-us_topic_0163572591>`.

   -  Add an existing ECS to an ECS group.

-  :ref:`Removing an ECS from an ECS Group <en-us_topic_0032980085__section12553172594918>`
-  :ref:`Deleting an ECS Group <en-us_topic_0032980085__section95601058404>`

.. _en-us_topic_0032980085__section1464061364114:

Creating an ECS Group
---------------------

Create an ECS group and associate the same policy to all group members. ECS groups are independent from each other.

#. Log in to the management console.
#. Click |image1| in the upper left corner and select your region and project.
#. Under **Computing**, choose **Elastic Cloud Server**.
#. In the navigation pane on the left, choose **ECS Group**.
#. On the **ECS Group** page, click **Create ECS Group**.
#. Enter the name of an ECS group.
#. Select a policy for the ECS group.
#. Click **OK**.

.. _en-us_topic_0032980085__section1447818554481:

Adding an ECS to an ECS Group
-----------------------------

To improve service reliability, you can add ECSs to an ECS group so that these ECSs in this group can run on different hosts.

.. note::

   -  After an ECS is added to an ECS group, the system reallocates a host to run this ECS to ensure that ECSs in this group are running on different hosts. When the ECS is being restarted, the startup may fail due to insufficient resources. In such a case, remove the ECS from the ECS group and try to restart the ECS again.
   -  ECSs that have local disks attached can be added to an ECS group only during the creation process. Once created, they can no longer be added to any ECS groups.
   -  ECSs that have local disks, GPU cards, or FPGA cards attached can be added to an ECS group only during the creation process. Once created, they can no longer be added to any ECS groups.

#. Log in to the management console.
#. Click |image2| in the upper left corner and select your region and project.
#. Under **Computing**, choose **Elastic Cloud Server**.
#. In the navigation pane on the left, choose **ECS Group**.
#. Locate the row that contains the target ECS group and click **Add ECS** in the **Operation** column.
#. On the **Add ECS** page, select an ECS to be added.
#. Click **OK**. The ECS is added to the ECS group.

.. _en-us_topic_0032980085__section12553172594918:

Removing an ECS from an ECS Group
---------------------------------

After an ECS is removed from an ECS group, the ECS does not comply with the anti-affinity policy anymore.

#. Log in to the management console.

#. Click |image3| in the upper left corner and select your region and project.

#. Under **Computing**, choose **Elastic Cloud Server**.

#. In the navigation pane on the left, choose **ECS Group**.

#. Expand the ECS group information and view the ECSs in the ECS group.

#. Locate the ECS to be removed and click **Remove** in the **Operation** column.

#. In the displayed dialog box, click **Yes**.

   The ECS is removed from the ECS group.

.. _en-us_topic_0032980085__section95601058404:

Deleting an ECS Group
---------------------

After an ECS group is deleted, the policy does not apply to the ECSs in the ECS group anymore.

#. Log in to the management console.
#. Click |image4| in the upper left corner and select your region and project.
#. Under **Computing**, choose **Elastic Cloud Server**.
#. In the navigation pane on the left, choose **ECS Group**.
#. Locate the ECS group to be deleted and click **Delete** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
.. |image2| image:: /_static/images/en-us_image_0210779229.png
.. |image3| image:: /_static/images/en-us_image_0210779229.png
.. |image4| image:: /_static/images/en-us_image_0210779229.png
