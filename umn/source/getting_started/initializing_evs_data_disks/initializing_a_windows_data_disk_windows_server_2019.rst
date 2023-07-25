:original_name: en-us_topic_0117490178.html

.. _en-us_topic_0117490178:

Initializing a Windows Data Disk (Windows Server 2019)
======================================================

Scenarios
---------

This section uses Windows Server 2019 Standard 64bit to describe how to initialize a data disk attached to a server running Windows.

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

#. On the desktop of the server, click the start icon in the lower left corner.

   The **Windows Server** window is displayed.

#. Click **Server Manager**.

   The **Server Manager** window is displayed.


   .. figure:: /_static/images/en-us_image_0132368216.png
      :alt: **Figure 1** Server Manager

      **Figure 1** Server Manager

#. In the upper right corner, choose **Tools** > **Computer Management**.

   The **Computer Management** window is displayed.


   .. figure:: /_static/images/en-us_image_0175083503.png
      :alt: **Figure 2** Computer Management

      **Figure 2** Computer Management

#. Choose **Storage** > **Disk Management**.

   Disks are displayed in the right pane. If there is a disk that is not initialized, the system will prompt you with the **Initialize Disk** dialog box.


   .. figure:: /_static/images/en-us_image_0175083504.png
      :alt: **Figure 3** Disk list

      **Figure 3** Disk list

#. In the **Initialize Disk** dialog box, the to-be-initialized disk is selected. Select a disk partition style and click **OK**. In this example, **GPT (GUID Partition Table)** is selected.

   The **Computer Management** window is displayed.


   .. figure:: /_static/images/en-us_image_0175083507.png
      :alt: **Figure 4** Computer Management

      **Figure 4** Computer Management

   .. important::

      The maximum disk size supported by MBR is 2 TiB, and that supported by GPT is 18 EiB. Because an EVS data disk currently supports up to 32 TiB, use GPT if your disk size is larger than 2 TiB.

      If the partition style is changed after the disk has been used, all data on the disk will be lost, so take care to select an appropriate partition style when initializing the disk. If you must change the partition style to GPT after a disk has been used, it is recommended that you back up the disk data before the change.

#. Right-click at the unallocated disk space and choose **New Simple Volume** from the shortcut menu.

   The **New Simple Volume Wizard** window is displayed.


   .. figure:: /_static/images/en-us_image_0175083508.png
      :alt: **Figure 5** New Simple Volume Wizard

      **Figure 5** New Simple Volume Wizard

#. Follow the prompts and click **Next**.

   The **Specify Volume Size** page is displayed.


   .. figure:: /_static/images/en-us_image_0175083509.png
      :alt: **Figure 6** Specify Volume Size

      **Figure 6** Specify Volume Size

#. Specify the volume size and click **Next**. The system selects the maximum volume size by default. You can specify the volume size as required. In this example, the default setting is used.

   The **Assign Drive Letter or Path** page is displayed.


   .. figure:: /_static/images/en-us_image_0175083510.png
      :alt: **Figure 7** Assign Driver Letter or Path

      **Figure 7** Assign Driver Letter or Path

#. Assign a drive letter or path to your partition and click **Next**. The system assigns drive letter D by default. In this example, the default setting is used.

   The **Format Partition** page is displayed.


   .. figure:: /_static/images/en-us_image_0175083511.png
      :alt: **Figure 8** Format Partition

      **Figure 8** Format Partition

#. Specify format settings and click **Next**. The system selects the NTFS file system by default. You can specify the file system type as required. In this example, the default setting is used.

   The **Completing the New Simple Volume Wizard** page is displayed.


   .. figure:: /_static/images/en-us_image_0175083512.png
      :alt: **Figure 9** Completing the New Simple Volume Wizard

      **Figure 9** Completing the New Simple Volume Wizard

   .. important::

      The partition sizes supported by file systems vary. Therefore, you are advised to choose an appropriate file system based on your service requirements.

#. Click **Finish**.

   Wait for the initialization to complete. When the volume status changes to **Healthy**, the initialization has finished successfully, as shown in :ref:`Figure 10 <en-us_topic_0117490178__en-us_topic_0115255433_fig14464150329>`.

   .. _en-us_topic_0117490178__en-us_topic_0115255433_fig14464150329:

   .. figure:: /_static/images/en-us_image_0175083513.png
      :alt: **Figure 10** Disk initialized

      **Figure 10** Disk initialized

#. After the volume is created, click |image1| on the task bar and check whether a new volume appears in **This PC**. In this example, New Volume (D:) is the new volume.

   If New Volume (D:) appears, the disk is successfully initialized and no further action is required.


   .. figure:: /_static/images/en-us_image_0175083515.png
      :alt: **Figure 11** This PC

      **Figure 11** This PC

.. |image1| image:: /_static/images/en-us_image_0238263336.png
