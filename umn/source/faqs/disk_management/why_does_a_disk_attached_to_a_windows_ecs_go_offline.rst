:original_name: en-us_topic_0114225937.html

.. _en-us_topic_0114225937:

Why Does a Disk Attached to a Windows ECS Go Offline?
=====================================================

Symptom
-------

A disk attached to a Windows ECS goes offline, and the system displays the message "The disk is offline because of policy set by an administrator."


.. figure:: /_static/images/en-us_image_0114229858.png
   :alt: **Figure 1** Offline disk

   **Figure 1** Offline disk

Possible Causes
---------------

Windows has three types of SAN policies: **OnlineAll**, **OfflineShared**, and **OfflineInternal**.

.. table:: **Table 1** SAN policies

   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | SAN Policy      | Description                                                                                                                                             |
   +=================+=========================================================================================================================================================+
   | OnlineAll       | Indicates that all newly detected disks are automatically brought online.                                                                               |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OfflineShared   | Indicates that all newly detected disks on sharable buses, such as FC or iSCSI, are offline by default, whereas disks on non-sharable buses are online. |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OfflineInternal | Indicates that all newly detected disks are offline.                                                                                                    |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+

The SAN policy of certain Windows OSs, such as Windows Server 2008/2012 Enterprise Edition and Data Center Edition, is **OfflineShared** by default.

Solution
--------

Use the disk partition management tool DiskPart to obtain and set the SAN policy on the ECS to **OnlineAll**.

#. Log in to the Windows ECS.

#. Press **Win+R** to run **cmd.exe**.

#. Run the following command to access DiskPart:

   **diskpart**

#. Run the following command to view the SAN policy on the ECS:

   **san**

   -  If the SAN policy is **OnlineAll**, run the **exit** command to exit DiskPart.

   -  If the SAN policy is not **OnlineAll**, go to step :ref:`5 <en-us_topic_0114225937__li5934113914122>`.

#. .. _en-us_topic_0114225937__li5934113914122:

   Run the following command to change the SAN policy to **OnlineAll**:

   **san policy=onlineall**

#. (Optional) Use the ECS with the SAN policy changed to create a private image so that the configuration takes effect permanently. After an ECS is created using this private image, the disks attached to the ECS are online by default. You only need to initialize them.
