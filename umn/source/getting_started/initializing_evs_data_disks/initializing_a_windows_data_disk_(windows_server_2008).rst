Initializing a Windows Data Disk (Windows Server 2008)
======================================================

Scenarios
---------

This section uses Windows Server 2008 R2 Enterprise 64bit to describe how to initialize a data disk attached to a server running Windows.

The maximum disk capacity supported by MBR is 2 TB, and that supported by GPT is 18 EB. Therefore, use the GPT partition style if your disk capacity is larger than 2 TB. For details about disk partition styles, see `Scenarios and Disk Partitions <en-us_topic_0030831623.html>`__.

The method for initializing a disk varies depending on the OS running on the server. This document is used for reference only. For the detailed operations and differences, see the product documents of the corresponding OS.

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

   -  If `Figure 1 <#EN-US_TOPIC_0085634796__en-us_topic_0044524740_fig40496387105554>`__ is displayed, the new disk is offline. Go to `3 <#EN-US_TOPIC_0085634796__en-us_topic_0044524740_li33296033102625>`__.
   -  If `Figure 4 <#EN-US_TOPIC_0085634796__en-us_topic_0044524740_fig68332918241>`__ is displayed, the **Initialize Disk** window is prompted. Go to `5 <#EN-US_TOPIC_0085634796__en-us_topic_0044524740_li34991214122212>`__.

   | **Figure 1** Disk Management
   | |image1|

#. Disks are displayed in the right pane. In the **Disk 1** area, right-click **Offline** and choose **Online** from the shortcut menu to online the disk.

   | **Figure 2** Online the disk
   | |image2|
     |image3|

   If the disk is offline, you need to online the disk before initializing it.

#. After making the disk online, the disk status changes from **Offline** to **Not Initialized**. Right-click the disk status and choose **Initialize Disk** from the shortcut menu, as shown in `Figure 3 <#EN-US_TOPIC_0085634796__en-us_topic_0044524740_fig409808111224>`__.

   | **Figure 3** Initialize Disk
   | |image4|

#. In the **Initialize Disk** dialog box, select the target disk, click **MBR (Master Boot Record)** or **GPT (GUID Partition Table)**, and click **OK**, as shown in `Figure 4 <#EN-US_TOPIC_0085634796__en-us_topic_0044524740_fig68332918241>`__.

   | **Figure 4** Unallocated space
   | |image5|
     |image6|

   The maximum disk capacity supported by MBR is 2 TB, and that supported by GPT is 18 EB. Because a data disk currently supports up to 32 TB, use the GPT partition style if your disk capacity is larger than 2 TB.

   If you change the disk partition style after the disk has been used, the data on the disk will be cleared. Therefore, select a proper disk partition style when initializing the disk.

#. Right-click at the unallocated space and choose **New Simple Volume** from the shortcut menu, as shown in `Figure 5 <#EN-US_TOPIC_0085634796__en-us_topic_0044524740_fig1945583522619>`__.

   | **Figure 5** New Simple Volume
   | |image7|

#. On the displayed **New Simple Volume Wizard** window, click **Next**.

   | **Figure 6** New Simple Volume Wizard
   | |image8|

#. Specify the volume size and click **Next**. The default value is the maximum size.

   | **Figure 7** Specify Volume Size
   | |image9|

#. Assign the driver letter and click **Next**.

   | **Figure 8** Assign Driver Letter or Path
   | |image10|

#. Select **Format this volume with the following settings**, set parameters based on the actual requirements, and select **Perform a quick format**. Then, click **Next**.

   | **Figure 9** Format Partition
   | |image11|
     **Figure 10** Completing the partition creation
   | |image12|
     |image13|

   The partition sizes supported by file systems vary. Therefore, you are advised to choose an appropriate file system based on your service requirements.

#. Click **Finish**. Wait for the initialization to complete. When the volume status changes to **Healthy**, the initialization has finished successfully, as shown in `Figure 11 <#EN-US_TOPIC_0085634796__en-us_topic_0044524740_fig14464150329>`__.

   | **Figure 11** Disk initialization succeeded
   | |image14|


.. |image1| image:: /_static/images/en-us_image_0095024494.png
   :class: imgResize

.. |image2| image:: /_static/images/en-us_image_0132359404.png
   :class: imgResize

.. |image3| image:: /_static/images/note_3.0-en-us.png
.. |image4| image:: /_static/images/en-us_image_0132360430.png
   :class: imgResize

.. |image5| image:: /_static/images/en-us_image_0097597141.png
   :class: imgResize

.. |image6| image:: /_static/images/notice_3.0-en-us.png
.. |image7| image:: /_static/images/en-us_image_0097597143.png
   :class: imgResize

.. |image8| image:: /_static/images/en-us_image_0097597145.png
   :class: imgResize

.. |image9| image:: /_static/images/en-us_image_0097597147.png
   :class: imgResize

.. |image10| image:: /_static/images/en-us_image_0097597149.png
   :class: imgResize

.. |image11| image:: /_static/images/en-us_image_0097597151.png
   :class: imgResize

.. |image12| image:: /_static/images/en-us_image_0097597153.png
   :class: imgResize

.. |image13| image:: /_static/images/notice_3.0-en-us.png
.. |image14| image:: /_static/images/en-us_image_0097597155.png
   :class: imgResize

