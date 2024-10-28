:original_name: en-us_topic_0036046828.html

.. _en-us_topic_0036046828:

Detaching an EVS Disk from a Running ECS
========================================

Scenarios
---------

You can detach EVS disks from an ECS.

-  System disks (mounted to **/dev/sda** or **/dev/vda**) can only be detached offline. They must be stopped before being detached.
-  Data disks (mounted to points other than **dev/sda**) can be detached online if the attached ECS is running certain OSs. You can detach these data disks without stopping the ECS.

This section describes how to detach a disk from a running ECS.

Constraints
-----------

-  The EVS disk to be detached must be mounted to a point other than **/dev/sda** or **/dev/vda**.

   EVS disks mounted to **/dev/sda** or **/dev/vda** are system disks and cannot be detached from running ECSs.

-  Before detaching an EVS disk from a running Windows ECS, make sure that OTC Tools have been installed on the ECS and that the tools are running properly.

-  Before detaching an EVS disk from a running Windows ECS, ensure that no programs are reading data from or writing data to the disk. Otherwise, data will be lost.

-  SCSI EVS disks cannot be detached from running Windows ECSs.

-  Before detaching an EVS disk from a running Linux ECS, you must log in to the ECS and run the **umount** command to cancel the association between the disk and the file system. In addition, ensure that no programs are reading data from or writing data to the disk. Otherwise, detaching the disk will fail.

Notes
-----

-  On a Windows ECS, if the disk is in non-offline state, the system forcibly detaches the EVS disk. If this occurs, the system may generate a xenvbd alarm. You can ignore this alarm.

   .. note::

      To view the status of an EVS disk, perform the following operations:

      #. Click **Start** in the task bar. In the displayed **Start** menu, right-click **Computer** and choose **Manage** from the shortcut menu.

         The **Server Manager** page is displayed.

      #. In the navigation pane on the left, choose **Storage** > **Disk Management**.

         The EVS disk list is displayed in the right pane.

      #. View the status of each EVS disk.

-  Do not detach an EVS disk from an ECS that is being started, stopped, or restarted.
-  Do not detach an EVS disk from a running ECS whose OS does not support this feature. OSs supporting EVS disk detachment from a running ECS are listed in :ref:`OSs Supporting EVS Disk Detachment from a Running ECS <en-us_topic_0036046828__section21417196143518>`.
-  For a running Linux ECS, the drive letter may be changed after an EVS disk is detached from it and then attached to it again. This is a normal case due to the drive letter allocation mechanism of the Linux system.
-  For a running Linux ECS, the drive letter may be changed after an EVS disk is detached from it and the ECS is restarted. This is a normal case due to the drive letter allocation mechanism of the Linux system.

.. _en-us_topic_0036046828__section21417196143518:

OSs Supporting EVS Disk Detachment from a Running ECS
-----------------------------------------------------

OSs supporting EVS disk detachment from a running ECS include two parts:

-  For the first part, see `External Image File Formats and Supported OSs <https://docs.otc.t-systems.com/en-us/usermanual/ims/en-us_topic_0030713143.html>`__.

-  :ref:`Table 1 <en-us_topic_0036046828__table9271324195455>` lists the second part of supported OSs.

   .. _en-us_topic_0036046828__table9271324195455:

   .. table:: **Table 1** OSs supporting EVS disk detachment from a running ECS

      +-----------------------------------------------------------------+-------------------------------------------+
      | OS                                                              | Version                                   |
      +=================================================================+===========================================+
      | CentOS                                                          | 7.3 64bit                                 |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | 7.2 64bit                                 |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | 6.8 64bit                                 |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | 6.7 64bit                                 |
      +-----------------------------------------------------------------+-------------------------------------------+
      | Debian                                                          | 8.6.0 64bit                               |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | 8.5.0 64bit                               |
      +-----------------------------------------------------------------+-------------------------------------------+
      | Fedora                                                          | 25 64bit                                  |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | 24 64bit                                  |
      +-----------------------------------------------------------------+-------------------------------------------+
      | SUSE                                                            | SUSE Linux Enterprise Server 12 SP2 64bit |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | SUSE Linux Enterprise Server 12 SP1 64bit |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | SUSE Linux Enterprise Server 11 SP4 64bit |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | SUSE Linux Enterprise Server 12 64bit     |
      +-----------------------------------------------------------------+-------------------------------------------+
      | OpenSUSE                                                        | 42.2 64bit                                |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | 42.1 64bit                                |
      +-----------------------------------------------------------------+-------------------------------------------+
      | Oracle Linux Server release                                     | 7.3 64bit                                 |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | 7.2 64bit                                 |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | 6.8 64bit                                 |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | 6.7 64bit                                 |
      +-----------------------------------------------------------------+-------------------------------------------+
      | Ubuntu Server                                                   | 16.04 64bit                               |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | 14.04 64bit                               |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | 14.04.4 64bit                             |
      +-----------------------------------------------------------------+-------------------------------------------+
      | Windows (SCSI EVS disks cannot be detached from a running ECS.) | Windows Server 2008 R2 Enterprise 64bit   |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | Windows Server 2012 R2 Standard 64bit     |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | Windows Server 2016 R2 Standard 64bit     |
      +-----------------------------------------------------------------+-------------------------------------------+
      | Red Hat Linux Enterprise                                        | 7.3 64bit                                 |
      +-----------------------------------------------------------------+-------------------------------------------+
      |                                                                 | 6.8 64bit                                 |
      +-----------------------------------------------------------------+-------------------------------------------+

.. note::

   Online detachment is not supported by the ECSs running OSs not listed in the preceding table. For such ECSs, stop the ECSs before detaching disks from them to prevent any possible problems from occurring.

Procedure
---------

#. On the **Elastic Cloud Server** page, click the name of the ECS from which the EVS disk is to be detached. The page providing details about the ECS is displayed.
#. Click the **Disks** tab. Locate the row containing the EVS disk to be detached and click **Detach**.
