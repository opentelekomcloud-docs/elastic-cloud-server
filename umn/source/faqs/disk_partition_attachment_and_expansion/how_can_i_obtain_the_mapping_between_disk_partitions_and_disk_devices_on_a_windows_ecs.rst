:original_name: en-us_topic_0087680813.html

.. _en-us_topic_0087680813:

How Can I Obtain the Mapping Between Disk Partitions and Disk Devices on a Windows ECS?
=======================================================================================

This section uses an ECS running Windows Server 2008 R2 64bit as an example to describe how to obtain the mapping between disk partitions and disk devices.

#. Log in to the Windows ECS.

#. Click **Start** in the lower left corner of the desktop.

#. Choose **Control Panel** > **Administrative Tools** > **Computer Management**.

#. In the navigation pane on the left, choose **Storage** > **Disk Management**.

   .. _en-us_topic_0087680813__fig63278226101115:

   .. figure:: /_static/images/en-us_image_0087906013.png
      :alt: **Figure 1** Disk Management

      **Figure 1** Disk Management

#. Taking disk 1 marked in :ref:`Figure 1 <en-us_topic_0087680813__fig63278226101115>` as an example, view the disk device for disk 1.

   a. Right-click the gray area where disk 1 is located, as shown in the red box in :ref:`Figure 1 <en-us_topic_0087680813__fig63278226101115>`.

   b. Click **Properties**.

      The **SCSI Disk Device Properties** dialog box is displayed, as shown in :ref:`Figure 2 <en-us_topic_0087680813__fig22437283101545>`.

      .. _en-us_topic_0087680813__fig22437283101545:

      .. figure:: /_static/images/en-us_image_0087906055.png
         :alt: **Figure 2** Disk properties

         **Figure 2** Disk properties

   c. Click the **Details** tab and set **Property** to **Parent**.


      .. figure:: /_static/images/en-us_image_0087906067.png
         :alt: **Figure 3** Disk device details

         **Figure 3** Disk device details

   d. Record the digits following **&** in the parameter value, for example, **51776**, which is the master and slave device number corresponding to the disk partition.

   e. Obtain the disk device according to the information listed in :ref:`Table 1 <en-us_topic_0087680813__table2257401020521>`.

      The disk device corresponding to **51776** is **xvde**. The disk device used by disk 1 is xvde.

      .. _en-us_topic_0087680813__table2257401020521:

      .. table:: **Table 1** Mapping between disk partitions and disk devices

         =================================================== ===========
         Master and Slave Device Number for a Disk Partition Disk Device
         =================================================== ===========
         51712                                               xvda
         51728                                               xvdb
         51744                                               xvdc
         51760                                               xvdd
         51776                                               xvde
         51792                                               xvdf
         51808                                               xvdg
         51824                                               xvdh
         51840                                               xvdi
         51856                                               xvdj
         51872                                               xvdk
         51888                                               xvdl
         51904                                               xvdm
         51920                                               xvdn
         51936                                               xvdo
         51952                                               xvdp
         268439552                                           xvdq
         268439808                                           xvdr
         268440064                                           xvds
         268440320                                           xvdt
         268440576                                           xvdu
         268440832                                           xvdv
         268441088                                           xvdw
         268441344                                           xvdx
         =================================================== ===========
