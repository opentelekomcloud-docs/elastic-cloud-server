.. _en-us_topic_0122307169:

Enabling Advanced Disk
======================



.. _en-us_topic_0122307169__section3591191571:

Scenarios
---------

-  Disk functions have been upgraded on the platform. Newly created ECSs can have up to 60 attached disks. However, an existing ECS can still have a maximum of 24 attached disks (40 for certain ECSs). To allow such ECSs to have up to 60 attached disks, enable advanced disk.
-  After advanced disk is enabled, you can view the mapping between device names and disks. For details, see :ref:`How Do I Obtain My Disk Name in the ECS OS Using the Device Identifier Provided on the Console? <en-us_topic_0103285575>`

This section describes how to enable advanced disk on an ECS.



.. _en-us_topic_0122307169__section12913133110717:

Procedure
---------

#. Log in to management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. Click the name of the target ECS. The page providing details about the ECS is displayed.

#. Click the **Disks** tab.

#. View the current number of disks that can be attached to the ECS and enable advanced disk as prompted.

   The **Enable Advanced Disk** dialog box is displayed.

#. Click **OK**.

#. Stop and then start the target ECS.

   This operation allows advanced disk to take effect.

#. Switch to the page providing details about the ECS again, click the **Disks** tab, and check whether the number of disks that can be attached to the ECS has been changed.

   -  If yes, advanced disk has been enabled.
   -  If no, enabling advanced disk failed. In such a case, try again later or contact customer service.

.. |image1| image:: /_static/images/en-us_image_0210779229.png

