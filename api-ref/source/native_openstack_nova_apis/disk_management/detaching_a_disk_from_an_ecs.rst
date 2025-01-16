:original_name: en-us_topic_0065817707.html

.. _en-us_topic_0065817707:

Detaching a Disk from an ECS
============================

Function
--------

This API is used to detach a disk from an ECS.

Constraints
-----------

The system disk, the device name of which is **/dev/sda**, and user disks can be detached from an ECS only when the ECS is stopped. There are no requirements on the OSs and OTC Tools.

When an ECS is in the **active** status, pay attention to the following constraints:

#. Only data disks, the device name of which is not **/dev/sda**, can be detached from an ECS.
#. Make sure that OTC Tools have been installed and enabled on the ECS. Otherwise, the uninstallation will fail.
#. For a Linux ECS, you need to log in to the ECS and run the **umount** command to disassociate the target disk from the file system. In addition, you need to ensure that no data is being written into or being read from the disk. Otherwise, the detachment will fail.
#. For a Windows ECS, you need to ensure that no data is being written into or being read from the disk when a disk is to be detached from the running ECS. Otherwise, data will be lost.
#. OSs supporting EVS disk detachment from a running ECS include two parts:

   -  For the first part, see `External Image File Formats and Supported OSs <https://docs.otc.t-systems.com/en-us/usermanual/ims/en-us_topic_0030713143.html>`__.

   -  :ref:`Table 1 <en-us_topic_0065817707__en-us_topic_0036046828_table9271324195455>` lists the second part of supported OSs.

      .. _en-us_topic_0065817707__en-us_topic_0036046828_table9271324195455:

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

URI
---

DELETE /v2.1/{project_id}/servers/{server_id}/os-volume_attachments/{volume_id}

DELETE /v2/{project_id}/servers/{server_id}/os-volume_attachments/{volume_id}

:ref:`Table 2 <en-us_topic_0065817707__en-us_topic_0057973182_table2814978410562>` describes the parameters in the URI.

.. _en-us_topic_0065817707__en-us_topic_0057973182_table2814978410562:

.. table:: **Table 2** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   volume_id  Yes       Specifies the volume ID.
   ========== ========= =========================

Usage: DELETE /v2/{project_id}/servers/{server_id}/os-volume_attachments/{volume_id}

Request
-------

None

Response
--------

None

Example Request
---------------

Detach the disk whose ID is **54667652-3029-4af8-9222-2d53066fd61c** from a specified ECS.

.. code-block:: text

   DELETE https://{endpoint}/v2/6fbe9263116a4b68818cf1edce16bc4f/servers/ab258e25-e351-47c7-b6e3-0749c5d9ed6a/os-volume_attachments/54667652-3029-4af8-9222-2d53066fd61c
   DELETE https://{endpoint}/v2.1/6fbe9263116a4b68818cf1edce16bc4f/servers/ab258e25-e351-47c7-b6e3-0749c5d9ed6a/os-volume_attachments/54667652-3029-4af8-9222-2d53066fd61c

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
