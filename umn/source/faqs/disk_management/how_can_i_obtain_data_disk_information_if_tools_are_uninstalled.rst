:original_name: en-us_topic_0029806525.html

.. _en-us_topic_0029806525:

How Can I Obtain Data Disk Information If Tools Are Uninstalled?
================================================================

If you uninstall Tools from a Linux ECS in a non-PVOPS system, data disks cannot be identified. In such a case, you can create a new ECS and attach the data disks of the original ECS to the new ECS and view information about the data disks. The procedure is as follows:

#. Log in to the management console and create a new ECS.

   .. note::

      Ensure that the new ECS is located in the same AZ and has the same parameter settings as the original ECS.

#. (Optional) On the **Elastic Cloud Server** page, locate the row containing the original ECS, click **More** in the **Operation** column, and select **Stop**. On the **Stop ECS** page, select **Forcibly stop the preceding ECSs** and click **Yes** to forcibly stop the original ECS.

   Manually refresh the **Elastic Cloud Server** page. The original ECS is stopped once the **Status** changes to **Stopped**.

   .. note::

      The ECSs running certain OSs support online data disk detaching. If your OS supports this feature, you can detach data disks from the running ECS.

#. View information about the data disks attached to the original ECS.

   .. note::

      If the original ECS has multiple data disks attached, repeat steps :ref:`4 <en-us_topic_0029806525__li3454282161441>` to :ref:`6 <en-us_topic_0029806525__li3628995162045>` to attach each data disk to the new ECS.

#. .. _en-us_topic_0029806525__li3454282161441:

   Click a data disk. The **Elastic Volume Service** page is displayed.

#. Select the data disk to be detached and click **Detach** in the **Operation** column. On the **Detach Disk** page, select the original ECS and click **OK** to detach the data disk from the original ECS.

   Manually refresh the **Elastic Volume Service** page. The data disk is detached from the original ECS once the **Status** changes to **Available**.

#. .. _en-us_topic_0029806525__li3628995162045:

   Select the detached data disk and click **Attach** in the **Operation** column. On the **Attach Disk** page, click the new ECS, select a device name, and click **OK** to attach the data disk to the new ECS.

   Manually refresh the EVS list. The data disk is attached to the new ECS once the **Status** value changes to **In-use**. You can then log in to the management console and view information about the data disk of the new ECS.
