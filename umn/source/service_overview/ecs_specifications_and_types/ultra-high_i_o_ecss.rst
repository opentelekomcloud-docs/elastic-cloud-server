:original_name: en-us_topic_0094118976.html

.. _en-us_topic_0094118976:

Ultra-high I/O ECSs
===================

Overview
--------

Ultra-high I/O ECSs use high-performance local NVMe SSDs to provide high storage input/output operations per second (IOPS) and low read/write latency. You can create such ECSs with high-performance local NVMe SSDs attached on the management console.

Scenarios
---------

-  Ultra-high I/O ECSs are suitable for high-performance relational databases.
-  Ultra-high I/O ECSs are suitable for NoSQL databases (such as Cassandra and MongoDB) and ElasticSearch.

Specifications
--------------

.. table:: **Table 1** I3 ECS specifications

   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------------------+----------------+
   | Flavor        | vCPUs | Memory | Max./Assured Bandwidth | Max. PPS | Max. NIC Queues | Max. NICs | Local Disks        | Virtualization |
   |               |       |        |                        |          |                 |           |                    |                |
   |               |       | (GiB)  | (Gbit/s)               | (10,000) |                 |           | (GiB)              |                |
   +===============+=======+========+========================+==========+=================+===========+====================+================+
   | i3.2xlarge.4  | 8     | 32     | 15/4.5                 | 150      | 4               | 4         | 1 x 3,200 GiB NVMe | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------------------+----------------+
   | i3.4xlarge.4  | 16    | 64     | 20/9                   | 280      | 8               | 8         | 2 x 3,200 GiB NVMe | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------------------+----------------+
   | i3.8xlarge.4  | 32    | 128    | 30/18                  | 550      | 16              | 8         | 4 x 3,200 GiB NVMe | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------------------+----------------+
   | i3.12xlarge.4 | 48    | 192    | 35/27                  | 750      | 16              | 8         | 6 x 3,200 GiB NVMe | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------------------+----------------+
   | i3.16xlarge.4 | 64    | 256    | 40/32                  | 1,000    | 32              | 8         | 8 x 3,200 GiB NVMe | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------------------+----------------+
   | i3.2xlarge.8  | 8     | 64     | 15/4.5                 | 150      | 4               | 4         | 1 x 3,200 GiB NVMe | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------------------+----------------+
   | i3.4xlarge.8  | 16    | 128    | 20/9                   | 280      | 8               | 8         | 2 x 3,200 GiB NVMe | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------------------+----------------+
   | i3.8xlarge.8  | 32    | 256    | 30/18                  | 550      | 16              | 8         | 4 x 3,200 GiB NVMe | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------------------+----------------+
   | i3.12xlarge.8 | 48    | 384    | 35/27                  | 750      | 16              | 8         | 6 x 3,200 GiB NVMe | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------------------+----------------+
   | i3.16xlarge.8 | 64    | 512    | 40/32                  | 1,000    | 32              | 8         | 8 x 3,200 GiB NVMe | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------------------+----------------+

Features
--------

:ref:`Table 2 <en-us_topic_0094118976__table1875314018355>` and :ref:`Table 3 <en-us_topic_0094118976__table9670341181017>` list the IOPS performance of local disks and specifications of a single local disk attached to an I3 ECS.

.. _en-us_topic_0094118976__table1875314018355:

.. table:: **Table 2** IOPS performance of local disks used by I3 ECSs

   ============= =================================
   Flavor        Maximum IOPS for Random 4 KB Read
   ============= =================================
   i3.2xlarge.4  750,000
   i3.4xlarge.4  1,500,000
   i3.8xlarge.4  3,000,000
   i3.12xlarge.4 4,500,000
   i3.16xlarge.4 6,000,000
   i3.2xlarge.8  750,000
   i3.4xlarge.8  1,500,000
   i3.8xlarge.8  3,000,000
   i3.12xlarge.8 4,500,000
   i3.16xlarge.8 6,000,000
   ============= =================================

.. _en-us_topic_0094118976__table9670341181017:

.. table:: **Table 3** Specifications of a single I3 local disk

   ========================== ===================
   Metric                     Performance
   ========================== ===================
   Disk capacity              1.6 TB
   IOPS for random 4 KB read  750,000
   IOPS for random 4 KB write 200,000
   Read throughput            2.9 GiB/s
   Write throughput           1.9 GiB/s
   Access latency             Within microseconds
   ========================== ===================

Notes
-----

-  :ref:`Table 4 <en-us_topic_0094118976__table192771727112217>` lists the OSs supported by ultra-high I/O ECSs.

   .. _en-us_topic_0094118976__table192771727112217:

   .. table:: **Table 4** Supported OS versions

      +-----------------------------------+-----------------------------------------------------+
      | OS                                | Version                                             |
      +===================================+=====================================================+
      | Alma                              | Alma 8 64bit                                        |
      +-----------------------------------+-----------------------------------------------------+
      | CentOS                            | -  CentOS Stream 8.6 64bit                          |
      |                                   | -  CentOS 7.9 64bit                                 |
      |                                   | -  CentOS 7.7 64bit                                 |
      +-----------------------------------+-----------------------------------------------------+
      | Debian                            | -  Debian GNU/Linux 11 64bit                        |
      |                                   | -  Debian GNU/Linux 10 64bit                        |
      +-----------------------------------+-----------------------------------------------------+
      | EulerOS                           | EulerOS 2.5 64bit                                   |
      +-----------------------------------+-----------------------------------------------------+
      | Fedora                            | -  Fedora 35 64bit                                  |
      |                                   | -  Fedora 34 64bit                                  |
      |                                   | -  Fedora 33 64bit                                  |
      +-----------------------------------+-----------------------------------------------------+
      | OpenSUSE                          | OpenSUSE 15.3 64bit                                 |
      +-----------------------------------+-----------------------------------------------------+
      | Oracle Linux                      | -  Oracle Linux Server release 8.4 64bit            |
      |                                   | -  Oracle Linux Server release 7.6 64bit            |
      +-----------------------------------+-----------------------------------------------------+
      | Red Hat                           | -  Red Hat Enterprise Linux 7.9 64bit               |
      |                                   | -  Red Hat Enterprise Linux 6.10 64bit              |
      +-----------------------------------+-----------------------------------------------------+
      | Rocky                             | Rocky 8 64bit                                       |
      +-----------------------------------+-----------------------------------------------------+
      | SUSE                              | -  Novell SUSE Linux Enterprise Server 15 SP3 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 15 SP2 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 15 SP1 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 15 64bit     |
      |                                   | -  Novell SUSE Linux Enterprise Server 12 SP5 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 12 SP4 64bit |
      |                                   | -  Novell SUSE Linux Enterprise Server 12 SP3 64bit |
      +-----------------------------------+-----------------------------------------------------+
      | Ubuntu                            | -  Ubuntu 20.04 server 64bit                        |
      |                                   | -  Ubuntu 18.04 server 64bit                        |
      +-----------------------------------+-----------------------------------------------------+
      | Windows                           | -  Windows Server 2019 Standard 64bit               |
      |                                   | -  Windows Server 2016 Standard 64bit               |
      |                                   | -  Windows Server 2012 R2 Standard 64bit            |
      +-----------------------------------+-----------------------------------------------------+
      | openEuler                         | openEuler 20.03 64bit                               |
      +-----------------------------------+-----------------------------------------------------+

-  If the host where an ultra-high I/O ECS is deployed is faulty, the ECS cannot be restored through live migration.

   -  If the host is faulty or subhealthy, you need to stop the ECS for hardware repair.
   -  In case of system maintenance or hardware faults, the ECS will be redeployed (to ensure HA) and cold migrated to another host. The local disk data of the ECS will not be retained.

-  Ultra-high I/O ECSs do not support specifications change.

-  Ultra-high I/O ECSs do not support local disk snapshots or backups.

-  Ultra-high I/O ECSs can use local disks, and can also have EVS disks attached to provide a larger storage size. Note the following when using the two types of storage media:

   -  Only an EVS disk, not a local disk, can be used as the system disk of an ultra-high I/O ECS.
   -  Both EVS disks and local disks can be used as data disks of an ultra-high I/O ECS.
   -  An ultra-high I/O ECS can have a maximum of 60 attached disks (including VBD, SCSI, and local disks). An ECS can have a maximum of 60 attached disks, including the system disk. For details about constraints, see :ref:`Can I Attach Multiple Disks to an ECS? <en-us_topic_0018073215>`

-  Modify the **fstab** file to set automatic disk mounting at ECS start. For details, see :ref:`Configuring Automatic Mounting at System Start <en-us_topic_0085634798__en-us_topic_0084935709_section15839912195453>`.

-  The local disk data of an ultra-high I/O ECS if an exception occurs, such as physical server breakdown or local disk damage. If your application does not use the data reliability architecture, it is a good practice to use EVS disks to build your ECS.

-  When an ultra-high I/O ECS is deleted, the data on local NVMe SSDs will also be automatically deleted, which can take some time. As a result, an ultra-high I/O ECS takes a longer time than other ECSs to be deleted. Back up the data before deleting such an ECS.

-  The data reliability of local disks depends on the reliability of physical servers and hard disks, which are SPOF-prone. It is a good practice to use data redundancy mechanisms at the application layer to ensure data availability. Use EVS disks to store service data that needs to be stored for a long time.

-  The device name of a local disk attached to an ultra-high I/O ECS is **/dev/nvme0n1** or **/dev/nvme0n2**.

-  The basic resources, including vCPUs, memory, and image of an ultra-high I/O ECS will continue to be billed after the ECS is stopped. To stop the ECS from being billed, delete it and its associated resources.

Handling Damaged Local Disks Attached to an ECS of I Series
-----------------------------------------------------------

If a local disk attached to an ECS is damaged, perform the following operations to handle this issue:

**For a Linux ECS:**

#. Detach the faulty local disk.

   a. Run the following command to query the mount point of the faulty disk:

      **df -Th**

      .. _en-us_topic_0094118976__fig17394172431814:

      .. figure:: /_static/images/en-us_image_0000001347858206.png
         :alt: **Figure 1** Querying the mount point

         **Figure 1** Querying the mount point

   b. Run the following command to detach the faulty local disk:

      **umount Mount point**

      In the example shown in :ref:`Figure 1 <en-us_topic_0094118976__fig17394172431814>`, the mount point of **/dev/nvme0n1** is **/mnt/nvme0**. Run the following command:

      **umount /mnt/nvme0**

#. Check whether the mount point of the faulty disk is configured in **/etc/fstab** of the ECS. If yes, comment out the mount point to prevent the ECS from entering the maintenance mode upon ECS startup after the faulty disk is replaced.

   a. .. _en-us_topic_0094118976__li7673171202112:

      Run the following command to obtain the partition UUID:

      **blkid** **Disk partition**

      In this example, run the following command to obtain the UUID of the **/dev/nvme0n1** partition:

      **blkid /dev/nvme0n1**

      Information similar to the following is displayed:

      .. code-block::

         /dev/nvme0n1: UUID="b9a07b7b-9322-4e05-ab9b-14b8050cd8cc" TYPE="ext4"

   b. Run the following command to check whether **/etc/fstab** contains the automatic mounting information about the disk partition:

      **cat /etc/fstab**

      Information similar to the following is displayed:

      .. code-block::

         UUID=b9a07b7b-9322-4e05-ab9b-14b8050cd8cc    /mnt   ext4    defaults        0 0

   c. If the mounting information exists, perform the following steps to delete it.

      #. Run the following command to edit **/etc/fstab**:

         **vi /etc/fstab**

         Use the UUID obtained in :ref:`2.a <en-us_topic_0094118976__li7673171202112>` to check whether the mounting information of the local disk is contained in **/etc/fstab**. If yes, comment out the information. This prevents the ECS from entering the maintenance mode upon ECS startup after the local disk is replaced.

      #. Press **i** to enter editing mode.

      #. Delete or comment out the automatic mounting information of the disk partition.

         For example, add a pound sign (#) at the beginning of the following command line to comment out the automatic mounting information:

         .. code-block::

            # UUID=b9a07b7b-9322-4e05-ab9b-14b8050cd8cc    /mnt   ext4    defaults        0 0

      #. Press **Esc** to exit editing mode. Enter **:wq** and press **Enter** to save the settings and exit.

#. Run the following command to obtain the SN of the local disk:

   For example, if the nvme0n1 disk is faulty, obtain the serial number of the nvme0n1 disk.

   **ll /dev/disk/by-id/**


   .. figure:: /_static/images/en-us_image_0000001347546258.png
      :alt: **Figure 2** Querying the serial number of the faulty local disk

      **Figure 2** Querying the serial number of the faulty local disk

#. Stop the ECS and provide the serial number of the faulty disk to technical support personnel to replace the local disk.

   After the local disk is replaced, restart the ECS to synchronize the new local disk information to the virtualization layer.

**For a Windows ECS:**

#. Open **Computer Management**, choose **Computer Management (Local)** > **Storage** > **Disk Management**, and view the disk ID, for example, Disk 1.

#. Open Windows PowerShell as an administrator and run the following command to query the disk on which the logical disk is created:

   **Get-CimInstance -ClassName Win32_LogicalDiskToPartition \|select Antecedent, Dependent \| fl**


   .. figure:: /_static/images/en-us_image_0000001346942780.png
      :alt: **Figure 3** Querying the disk on which the logical disk is created

      **Figure 3** Querying the disk on which the logical disk is created

#. Run the following command to obtain the serial number of the faulty disk according to the mapping between the disk ID and serial number:

   **Get-Disk \| select Number, SerialNumber**


   .. figure:: /_static/images/en-us_image_0000001346921122.png
      :alt: **Figure 4** Querying the mapping between the disk ID and serial number

      **Figure 4** Querying the mapping between the disk ID and serial number

   .. note::

      If the serial number cannot be obtained by running the preceding command, see :ref:`Using a Serial Number to Obtain the Disk Name (Windows) <en-us_topic_0103285575__section1549713815243>`.

#. Stop the ECS and provide the serial number of the faulty disk to technical support personnel to replace the local disk.

   After the local disk is replaced, restart the ECS to synchronize the new local disk information to the virtualization layer.
