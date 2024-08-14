:original_name: en-us_topic_0085634796.html

.. _en-us_topic_0085634796:

Initializing a Windows Data Disk (Windows Server 2008)
======================================================

Scenarios
---------

This section uses Windows Server 2008 R2 Enterprise 64bit to describe how to initialize a data disk attached to a server running Windows.

The maximum disk capacity supported by MBR is 2 TiB, and that supported by GPT is 18 EiB. Therefore, use the GPT partition style if your disk capacity is larger than 2 TiB. To learn more about disk partition styles, see :ref:`Scenarios and Disk Partitions <en-us_topic_0030831623>`.

The method for initializing a disk varies slightly depending on the OS running on the server. This document is used for reference only. For the detailed operations and differences, see the product documents of the corresponding OS.

.. important::

   When using a disk for the first time, if you have not initialized it, including creating partitions and file systems, the additional space added to this disk in an expansion later may not be normally used.

Prerequisites
-------------

-  A data disk has been attached to a server and has not been initialized.
-  You have logged in to the server.

   -  For how to log in to an ECS, see the *Elastic Cloud Server User Guide*.
   -  For how to log in to a BMS, see the *Bare Metal Server User Guide*.

Procedure
---------

#. On the desktop of the server, right-click **Computer** and choose **Manage** from the shortcut menu.

   The **Server Manager** window is displayed.

#. In the navigation tree, choose **Storage** > **Disk Management**.

   The **Disk Management** window is displayed.

   -  If :ref:`Figure 1 <en-us_topic_0085634796__en-us_topic_0044524740_fig40496387105554>` is displayed, the new disk is offline. Go to :ref:`3 <en-us_topic_0085634796__en-us_topic_0044524740_li33296033102625>`.
   -  If :ref:`Figure 4 <en-us_topic_0085634796__en-us_topic_0044524740_fig68332918241>` is displayed, the **Initialize Disk** window is prompted. Go to :ref:`5 <en-us_topic_0085634796__en-us_topic_0044524740_li34991214122212>`.

   .. _en-us_topic_0085634796__en-us_topic_0044524740_fig40496387105554:

   .. figure:: /_static/images/en-us_image_0095024494.png
      :alt: **Figure 1** Disk Management

      **Figure 1** Disk Management

#. .. _en-us_topic_0085634796__en-us_topic_0044524740_li33296033102625:

   Disks are displayed in the right pane. In the **Disk 1** area, right-click **Offline** and choose **Online** from the shortcut menu to online the disk.


   .. figure:: /_static/images/en-us_image_0132359404.png
      :alt: **Figure 2** Online the disk

      **Figure 2** Online the disk

   .. note::

      If the disk is offline, you need to online the disk before initializing it.

#. After making the disk online, the disk status changes from **Offline** to **Not Initialized**. Right-click the disk status and choose **Initialize Disk** from the shortcut menu, as shown in :ref:`Figure 3 <en-us_topic_0085634796__en-us_topic_0044524740_fig409808111224>`.

   .. _en-us_topic_0085634796__en-us_topic_0044524740_fig409808111224:

   .. figure:: /_static/images/en-us_image_0132360430.png
      :alt: **Figure 3** Initialize Disk

      **Figure 3** Initialize Disk

#. .. _en-us_topic_0085634796__en-us_topic_0044524740_li34991214122212:

   In the **Initialize Disk** dialog box, select the target disk, click **MBR (Master Boot Record)** or **GPT (GUID Partition Table)**, and click **OK**, as shown in :ref:`Figure 4 <en-us_topic_0085634796__en-us_topic_0044524740_fig68332918241>`.

   .. _en-us_topic_0085634796__en-us_topic_0044524740_fig68332918241:

   .. figure:: /_static/images/en-us_image_0097597141.png
      :alt: **Figure 4** Unallocated space

      **Figure 4** Unallocated space

   .. important::

      The maximum disk size supported by MBR is 2 TiB, and that supported by GPT is 18 EiB. Because an EVS data disk currently supports up to 32 TiB, use GPT if your disk size is larger than 2 TiB.

      If the partition style is changed after the disk has been used, all data on the disk will be lost, so take care to select an appropriate partition style when initializing the disk. If you must change the partition style to GPT after a disk has been used, it is recommended that you back up the disk data before the change.

#. Right-click at the unallocated space and choose **New Simple Volume** from the shortcut menu, as shown in :ref:`Figure 5 <en-us_topic_0085634796__en-us_topic_0044524740_fig1945583522619>`.

   .. _en-us_topic_0085634796__en-us_topic_0044524740_fig1945583522619:

   .. figure:: /_static/images/en-us_image_0097597143.png
      :alt: **Figure 5** New Simple Volume

      **Figure 5** New Simple Volume

#. On the displayed **New Simple Volume Wizard** window, click **Next**.


   .. figure:: /_static/images/en-us_image_0097597145.png
      :alt: **Figure 6** New Simple Volume Wizard

      **Figure 6** New Simple Volume Wizard

#. Specify the volume size and click **Next**. The default value is the maximum size.


   .. figure:: /_static/images/en-us_image_0097597147.png
      :alt: **Figure 7** Specify Volume Size

      **Figure 7** Specify Volume Size

#. Assign the driver letter and click **Next**.


   .. figure:: /_static/images/en-us_image_0097597149.png
      :alt: **Figure 8** Assign Driver Letter or Path

      **Figure 8** Assign Driver Letter or Path

#. On the displayed **Format Partition** page, click **Format this volume with the following settings**, set parameters based on the requirements, and select **Perform a quick format**. Then, click **Next**.


   .. figure:: /_static/images/en-us_image_0097597151.png
      :alt: **Figure 9** Format Partition

      **Figure 9** Format Partition


   .. figure:: /_static/images/en-us_image_0097597153.png
      :alt: **Figure 10** Completing the partition creation

      **Figure 10** Completing the partition creation

   .. important::

      The partition sizes supported by file systems vary. Therefore, you are advised to choose an appropriate file system based on your service requirements.

#. Click **Finish**. Wait for the initialization to complete. When the volume status changes to **Healthy**, the initialization has finished successfully, as shown in :ref:`Figure 11 <en-us_topic_0085634796__en-us_topic_0044524740_fig14464150329>`.

   .. _en-us_topic_0085634796__en-us_topic_0044524740_fig14464150329:

   .. figure:: /_static/images/en-us_image_0097597155.png
      :alt: **Figure 11** Disk initialization succeeded

      **Figure 11** Disk initialization succeeded
