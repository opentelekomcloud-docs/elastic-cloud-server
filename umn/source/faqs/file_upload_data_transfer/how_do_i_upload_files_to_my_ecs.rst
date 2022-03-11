How Do I Upload Files to My ECS?
================================

Windows
-------

-  File transfer tool

   Install a file transfer tool, such as FileZilla on both the local computer and the Windows ECS and use it to transfer files.

-  (Recommended) Local disk mapping

   Use MSTSC to transfer files. This method does not support resumable transmission. Therefore, do not use this method to transfer large files.

   For details, see `How Can I Transfer Files from a Local Windows Computer to a Windows ECS? <faqs/file_upload_data_transfer/how_can_i_transfer_files_from_a_local_windows_computer_to_a_windows_ecs>`__

-  FTP site

   Transfer files through an FTP site. Before transferring files from a local computer to a Windows ECS, set up an FTP site on the ECS and install FileZilla on the local computer.

   For details, see `How Can I Use FTP to Transfer Files from a Local Windows Computer to a Windows or Linux ECS? <faqs/file_upload_data_transfer/how_can_i_use_ftp_to_transfer_files_from_a_local_windows_computer_to_a_windows_or_linux_ecs>`__

-  From a local Mac

   If your local computer runs Mac, use Microsoft Remote Desktop for Mac to transfer files to the Windows ECS For details, see `How Can I Transfer Files from a Local Mac to a Windows ECS? <faqs/file_upload_data_transfer/how_can_i_transfer_files_from_a_local_mac_to_a_windows_ecs>`__.

Linux
-----

-  From a local Windows computer

   Use WinSCP to transfer the files to the Linux ECS. For details, see `How Can I Use WinSCP to Transfer Files from a Local Windows Computer to a Linux ECS? <faqs/file_upload_data_transfer/how_can_i_use_winscp_to_transfer_files_from_a_local_windows_computer_to_a_linux_ecs>`__

   Before transferring files from a local computer to a Linux ECS, set up an FTP site on the ECS and install FileZilla on the local computer. For details, see `How Can I Use FTP to Transfer Files from a Local Windows Computer to a Windows or Linux ECS? <faqs/file_upload_data_transfer/how_can_i_use_ftp_to_transfer_files_from_a_local_windows_computer_to_a_windows_or_linux_ecs>`__

-  From a local Linux computer

   Use SCP to transfer the files to the Linux ECS. For details, see `How Can I Use SCP to Transfer Files Between a Local Linux Computer and a Linux ECS? <faqs/file_upload_data_transfer/how_can_i_use_scp_to_transfer_files_between_a_local_linux_computer_and_a_linux_ecs>`__

   Use SFTP to transfer the files to the Linux ECS. For details, see `How Can I Use SFTP to Transfer Files Between a Local Linux Computer and a Linux ECS? <faqs/file_upload_data_transfer/how_can_i_use_sftp_to_transfer_files_between_a_local_linux_computer_and_a_linux_ecs>`__

   Use FTP to transfer the files to the Linux ECS. For details, see `How Can I Use FTP to Transfer Files Between a Local Linux Computer and a Linux ECS? <faqs/file_upload_data_transfer/how_can_i_use_ftp_to_transfer_files_between_a_local_linux_computer_and_a_linux_ecs>`__

Does an ECS Support FTP-based File Transferring by Default?
-----------------------------------------------------------

No. You need to install and configure FTP so that the ECS supports FTP-based file transfer.

