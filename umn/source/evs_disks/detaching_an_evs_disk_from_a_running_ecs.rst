Detaching an EVS Disk from a Running ECS
========================================

Scenarios
---------

An EVS disk attached to an ECS can function as a system disk or data disk.

-  EVS disks mounted to **/dev/sda** or **/dev/vda** function as system disks. You can only detach system disks offline. Before detaching a system disk from an ECS, you must stop the ECS.
-  EVS disks mounted to other locations function as data disks. In addition to offline detachment, data disks can be detached online if the OS running on the ECS supports this feature.

This section describes how to detach a disk from a running ECS.

Constraints
-----------

-  The EVS disk to be detached must be mounted at a location other than **/dev/sda** or **/dev/vda**.

   EVS disks mounted to **/dev/sda** or **/dev/vda** are system disks and cannot be detached from running ECSs.

-  Before detaching an EVS disk from a running Windows ECS, make sure that OTC Tools have been installed on the ECS and that the tools are running properly.

-  Before detaching an EVS disk from a running Windows ECS, ensure that no program is reading data from or writing data to the disk. Otherwise, data will be lost.

-  SCSI EVS disks cannot be detached from running Windows ECSs.

-  Before detaching an EVS disk from a running Linux ECS, you must log in to the ECS and run the **umount** command to cancel the association between the disk and the file system. In addition, ensure that no program is reading data from or writing data to the disk. Otherwise, detaching the disk will fail.

Notes
-----

-  On a Windows ECS, if the disk is in non-offline state, the system forcibly detaches the EVS disk. If this occurs, the system may generate a xenvbd alarm. You can ignore this alarm.\ |image1|

   To view the status of an EVS disk, perform the following operations:

   #. Click **Start** in the task bar. In the displayed **Start** menu, right-click **Computer** and choose **Manage** from the shortcut menu.

      The **Server Manager** page is displayed.

   #. In the navigation pane on the left, choose **Storage** > **Disk Management**.

      The EVS disk list is displayed in the right pane.

   #. View the status of each EVS disk.

-  Do not detach an EVS disk from an ECS that is being started, stopped, or restarted.

-  Do not detach an EVS disk from a running ECS whose OS does not support this feature. OSs supporting EVS disk detachment from a running ECS are listed in `OSs Supporting EVS Disk Detachment from a Running ECS <#EN-US_TOPIC_0036046828__section21417196143518>`__.

-  For a running Linux ECS, the drive letter may be changed after an EVS disk is detached from it and then attached to it again. This is a normal case due to the drive letter allocation mechanism of the Linux system.

-  For a running Linux ECS, the drive letter may be changed after an EVS disk is detached from it and the ECS is restarted. This is a normal case due to the drive letter allocation mechanism of the Linux system.

OSs Supporting EVS Disk Detachment from a Running ECS
-----------------------------------------------------

OSs supporting EVS disk detachment from a running ECS include two parts:

-  For the first part, see `Formats and OSs Supported for External Image Files <https://docs.otc.t-systems.com/en-us/usermanual/ims/en-us_topic_0030713143.html>`__.
-  `Table 1 <#EN-US_TOPIC_0036046828__table9271324195455>`__ lists the second part of supported OSs. 

.. _EN-US_TOPIC_0036046828__table9271324195455:

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

|image2|

Online detachment is not supported by the ECSs running OSs not listed in the preceding table. For such ECSs, stop the ECSs before detaching disks from them to prevent any possible problems from occurring.

Procedure
---------

#. On the **Elastic Cloud Server** page, click the name of the ECS from which the EVS disk is to be detached. The page providing details about the ECS is displayed.
#. Click the **Disks** tab. Locate the row containing the EVS disk to be detached and click **Detach**.



.. |image1| image:: /_static/images/note_3.0-en-us.png
.. |image2| image:: /_static/images/note_3.0-en-us.png
