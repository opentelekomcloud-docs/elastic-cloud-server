.. _en-us_topic_0214940105:

Why Do the Disks of a Windows ECS Go Offline After I Modify the ECS Specifications?
===================================================================================

Scenarios
---------

After you modify specifications of a Windows ECS, the disks may go offline. Therefore, you need to check the number of disks after you modify the specifications.

Procedure
---------

#. Check whether the number of disks displayed on the **Computer** page after you modified ECS specifications is the same as the number of disks before you modified ECS specifications.

   -  If the numbers are the same, the status of the disks is properly. No further action is required.
   -  If the numbers are different, the disks are offline. In this case, go to step :ref:`2 <en-us_topic_0214940105__en-us_topic_0100593628_li1476865113179>`.

   For example:

   An ECS running Windows Server 2008 has one system disk and two data disks attached before you modified the specifications.

   .. _en-us_topic_0214940105__en-us_topic_0100593628_fig21898319615:

   .. figure:: /_static/images/en-us_image_0214947577.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 1** Disks before modifying ECS specifications

   After the specifications are modified, check the number of disks.

   .. _en-us_topic_0214940105__en-us_topic_0100593628_fig577522321219:

   .. figure:: /_static/images/en-us_image_0214947578.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 2** Disks after modifying ECS specifications

   Only one system disk is displayed. The data disks are offline after you modify the specifications.

#. .. _en-us_topic_0214940105__en-us_topic_0100593628_li1476865113179:

   Bring the disks online.

   a. Click **Start** in the task bar. In the displayed **Start** menu, right-click **Computer** and choose **Manage** from the shortcut menu.

      The **Server Manager** page is displayed.

   b. In the navigation pane on the left, choose **Storage** > **Disk Management**.

      The **Disk Management** page is displayed.

   c. In the left pane, the disk list is displayed. Right-click the offline disk and choose **Online** from the shortcut menu to bring it online.

      .. _en-us_topic_0214940105__en-us_topic_0100593628_fig2680331163510:

      .. figure:: /_static/images/en-us_image_0214947579.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 3** Bringing the disk online

#. On the **Computer** page, check whether the number of disks after you modified ECS specifications is the same as the number of disks before you modified the ECS specifications.

   -  If the numbers are the same, no further action is required.
   -  If the numbers are different, contact customer service.

   .. _en-us_topic_0214940105__en-us_topic_0100593628_fig746964620392:

   .. figure:: /_static/images/en-us_image_0214947580.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 4** Disks after you bring the disks online
