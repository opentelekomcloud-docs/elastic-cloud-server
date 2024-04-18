:original_name: en-us_topic_0013771092.html

.. _en-us_topic_0013771092:

General Operations
==================

Scenarios
---------

If ECS specifications do not meet service requirements, you can modify the ECS specifications, including vCPUs and memory. Certain ECSs allow you to change their types when you modify their specifications.

Background
----------

To obtain the virtualization type of an ECS, perform the following operations:

#. On the page providing details about the ECS, view the ECS specifications.


   .. figure:: /_static/images/en-us_image_0121090576.png
      :alt: **Figure 1** Viewing ECS specifications

      **Figure 1** Viewing ECS specifications

#. Check the specifications tables in :ref:`ECS Types <en-us_topic_0035470096>` for the virtualization type.

Notes
-----

-  Downgrading ECS specifications (vCPU or memory) will reduce performance.
-  Certain ECS types do not support specifications modification currently. For details about available ECS types as well as their functions and usage, see "Notes" in :ref:`ECS Types <en-us_topic_0035470096>`.
-  When the disk status is **Expanding**, you are not allowed to modify the specifications of the ECS where the disk is attached.
-  Before modifying the specifications of a Windows ECS, modify the SAN policy by following the instructions provided in :ref:`Why Does a Disk Attached to a Windows ECS Go Offline? <en-us_topic_0114225937>` to prevent disks from going offline after the specifications are modified.
-  Before modifying specifications, make sure that the ECS has been stopped.

Step 1: Modify Specifications
-----------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the **Elastic Cloud Server** page, view the status of the target ECS.

   If the ECS is not in **Stopped** state, click **More** in the **Operation** column and select **Stop**.

#. Click **More** in the **Operation** column and select **Modify Specifications**.

   The **Modify ECS Specifications** page is displayed.

#. Select the new ECS type, vCPUs, and memory as prompted.


   .. figure:: /_static/images/en-us_image_0000001657891362.png
      :alt: **Figure 2** Modifying specifications

      **Figure 2** Modifying specifications

#. (Optional) Set **DeH**.

   If the ECS is created on a DeH, the system allows you to change the DeH.

   To do so, select the target DeH from the drop-down list. If no DeH is available in the drop-down list, remaining DeH resources are insufficient and cannot be used to create the ECS with specifications modified.

#. Click **Next**.

#. Confirm the settings and click **Submit**.

#. Check whether the specifications have been modified.

   After modifying the specifications, you can check whether the specifications have been modified in **Failures**.

   a. Check whether **Failures** is displayed on the management console. For details, see :ref:`Viewing Failed Tasks <en-us_topic_0108255889>`.

      -  If yes, go to step :ref:`10.b <en-us_topic_0013771092__li6253192246>`.
      -  If no, the specifications have been modified.

   b. .. _en-us_topic_0013771092__li6253192246:

      Click **Failures**. Then, in the **Failures** dialog box, click **Operation Failures** and check whether the task is contained in the list by **Name/ID**, **Operated At**, or **Task**.

      -  If yes, the specifications modification failed. See :ref:`Follow-up Procedure <en-us_topic_0013771092__section9461027528>` for failure causes.
      -  If no, the specifications have been modified.

Step 2: Check Disk Attachment
-----------------------------

After specifications are modified, disk attachment may fail. Therefore, check disk attachment after specifications modification. If disks are properly attached, the specifications modification is successful.

-  Windows ECS

   For details, see :ref:`Why Do the Disks of a Windows ECS Go Offline After I Modify the ECS Specifications? <en-us_topic_0214940105>`

-  Linux ECS

   For details, see :ref:`Why Does the Disk Attachment of a Linux ECS Fail After I Modify the ECS Specifications? <en-us_topic_0214940106>`

.. _en-us_topic_0013771092__section9461027528:

Follow-up Procedure
-------------------

Perform the following operations in the event of a specifications modification failure:

#. Log in to the management console.

#. Under **Management & Deployment**, choose **Cloud Trace Service**.

#. In the navigation pane on the left, choose **Trace List**.

#. In the **Trace Name** column, locate the **resizeServer** event by resource ID.

   The resource ID is the ID of the ECS on which the specifications modification failed.

#. Click **View Trace** in the **Operation** column to view the failure cause.

   If the fault cannot be rectified based on logs, contact customer service.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
