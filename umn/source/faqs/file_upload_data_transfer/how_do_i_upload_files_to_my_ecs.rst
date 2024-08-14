:original_name: en-us_topic_0236302789.html

.. _en-us_topic_0236302789:

How Do I Upload Files to My ECS?
================================

Windows
-------

-  File transfer tool

   Install a file transfer tool, such as FileZilla on both the local computer and the Windows ECS and use it to transfer files.

-  (Recommended) Local disk mapping

   Use MSTSC to transfer files. This method does not support resumable transmission. Therefore, do not use this method to transfer large files.

   For details, see :ref:`How Can I Transfer Files from a Local Windows Computer to a Windows ECS? <en-us_topic_0166284970>`

-  FTP site

   Transfer files through an FTP site. Before transferring files from a local computer to a Windows ECS, set up an FTP site on the ECS and install FileZilla on the local computer.

   For details, see :ref:`How Can I Use FTP to Transfer Files from a Local Windows Computer to a Windows or Linux ECS? <en-us_topic_0263806053>`

-  From a local Mac

   If your local computer runs macOS, use Microsoft Remote Desktop for Mac to transfer files to the Windows ECS. For details, see :ref:`How Can I Transfer Files from a Local Mac to a Windows ECS? <en-us_topic_0295091738>`.

Linux
-----

-  From a local Windows computer

   Use WinSCP to transfer the files to the Linux ECS. For details, see :ref:`How Can I Use WinSCP to Transfer Files from a Local Windows Computer to a Linux ECS? <en-us_topic_0166284971>`

   Before transferring files from a local computer to a Linux ECS, set up an FTP site on the ECS and install FileZilla on the local computer. For details, see :ref:`How Can I Use FTP to Transfer Files from a Local Windows Computer to a Windows or Linux ECS? <en-us_topic_0263806053>`

-  From a local Linux computer

   Use SCP to transfer the files to the Linux ECS. For details, see :ref:`How Can I Use SCP to Transfer Files Between a Local Linux Computer and a Linux ECS? <en-us_topic_0263796591>`

   Use SFTP to transfer the files to the Linux ECS. For details, see :ref:`How Can I Use SFTP to Transfer Files Between a Local Linux Computer and a Linux ECS? <en-us_topic_0170139796>`

   Use FTP to transfer the files to the Linux ECS. For details, see :ref:`How Can I Use FTP to Transfer Files Between a Local Linux Computer and a Linux ECS? <en-us_topic_0263806054>`

Does an ECS Support FTP-based File Transferring by Default?
-----------------------------------------------------------

No. You need to install and configure FTP so that the ECS supports FTP-based file transfer.
