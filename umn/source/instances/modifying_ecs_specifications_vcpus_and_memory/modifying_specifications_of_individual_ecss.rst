:original_name: en-us_topic_0013771092.html

.. _en-us_topic_0013771092:

Modifying Specifications of Individual ECSs
===========================================

Scenarios
---------

If the ECS specifications do not meet service requirements, you can modify the specifications, including vCPUs and memory. Certain ECSs allow you to change their types when you modify their specifications.

Background
----------

To obtain the virtualization type of an ECS, perform the following operations:

#. On the ECS details page, view the ECS specifications.


   .. figure:: /_static/images/en-us_image_0000002351464146.png
      :alt: **Figure 1** Viewing ECS specifications

      **Figure 1** Viewing ECS specifications

#. Check the specifications tables in :ref:`ECS Types <en-us_topic_0035470096>` for the virtualization type.

Notes
-----

-  The ECS needs to be stopped during the specification modification, so you are advised to perform this operation during off-peak hours.
-  During the specification modification, do not perform any operation on the ECS, such as stopping or restarting the ECS. Otherwise, the modification will fail.
-  Downgrading ECS specifications (vCPUs or memory) will reduce performance.
-  Certain ECS types do not support specification modification. For details about ECS types and functions, see :ref:`ECS Specifications <en-us_topic_0132345719>`. For details about constraints on using different types of ECSs, see their notes.
-  When the disk status is **Expanding**, you are not allowed to modify the specifications of the ECS where the disk is attached.
-  Before modifying the specifications of a Windows ECS, modify the SAN policy to prevent disks from going offline after the specifications are modified. For details, see :ref:`Why Does a Disk Attached to a Windows ECS Go Offline? <en-us_topic_0114225937>`
-  Before modifying specifications, make sure that the ECS has been stopped.

Step 1: Modify Specifications
-----------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the **Elastic Cloud Server** page, view the status of the target ECS.

   If the ECS is not in **Stopped** state, choose **More** > **Stop** in the **Operation** column.

#. Choose **More** > **Modify Specifications** in the **Operation** column.

   The **Modify ECS Specifications** page is displayed.

#. Select a new ECS type, vCPUs, and memory.


   .. figure:: /_static/images/en-us_image_0000001657891362.png
      :alt: **Figure 2** Modifying specifications

      **Figure 2** Modifying specifications

#. (Optional) Set **DeH**.

   If the ECS is created on a DeH, the system allows you to change the DeH.

   To do so, select the target DeH from the drop-down list. If no DeH is available in the drop-down list, it means remaining DeH resources are insufficient and cannot be used to create the ECS with new specifications.

#. Click **Next**.

#. Confirm the new specifications and click **Submit**.

#. Check whether the specifications have been modified.

   a. On the console, check whether **Failures** is displayed by referring to :ref:`Viewing Failed Tasks <en-us_topic_0108255889>`.

      -  If yes, go to step :ref:`10.b <en-us_topic_0013771092__li6253192246>`.
      -  If no, the specifications have been modified.

   b. .. _en-us_topic_0013771092__li6253192246:

      Click **Failures**. Then, in the **Failures** dialog box, click **Operation Failures** and check whether the task is contained in the list by **Name/ID**, **Operated At**, or **Task**.

      -  If yes, the specifications failed to be modified. View the failure causes by referring to :ref:`Follow-up Procedure <en-us_topic_0013771092__section9461027528>`.
      -  If no, the specifications have been modified.

Step 2: Check Disk Attachment
-----------------------------

After specifications are modified, disk attachment may fail. Therefore, check disk attachment after specification modification. If disks are properly attached, the specification modification is successful.

-  Windows ECS

   For details, see :ref:`Why Do the Disks of a Windows ECS Go Offline After I Modify the ECS Specifications? <en-us_topic_0214940105>`

-  Linux ECS

   For details, see :ref:`Why Does the Disk Attachment of a Linux ECS Fail After I Modify the ECS Specifications? <en-us_topic_0214940106>`

.. _en-us_topic_0013771092__section9461027528:

Follow-up Procedure
-------------------

If the specifications fail to be modified, do as follows to view the failure cause:

#. Log in to the management console.

#. Under **Management & Deployment**, click **Cloud Trace Service**.

#. In the navigation pane on the left, choose **Trace List**.

#. In the **Trace Name** column, locate **resizeServer** by resource ID.

   The resource ID is the ID of the ECS whose specifications failed to be modified.

#. Click the target trace name. In the slide-out **Trace Overview** panel, view the trace details and failure cause.

   If the fault cannot be rectified based on logs, contact customer service.

.. |image1| image:: /_static/images/en-us_image_0000002188678994.png
