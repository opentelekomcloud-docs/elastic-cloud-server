:original_name: en-us_topic_0037470901.html

.. _en-us_topic_0037470901:

Expanding the Local Disks of a Disk-intensive ECS
=================================================

Scenarios
---------

Disk-intensive ECSs can use both local disks and EVS disks to store data. Local disks are generally used to store service data and feature higher throughput than EVS disks.

Disk-intensive ECSs do not support specifications modification. When the capacity of local disks is insufficient, you can create a new disk-intensive ECS with higher specifications for capacity expansion. The data stored in the original ECS can be migrated to the new ECS through EVS.

Procedure
---------

#. `Create an EVS disk <https://docs.otc.t-systems.com/usermanual/evs/en-us_topic_0021738346.html>`__ according to the volume of data to be migrated.

#. Attach the EVS disk to the disk-intensive ECS for which you want to expand the capacity.

#. Back up the data stored in the local disks to the EVS disk that is newly attached to the disk-intensive ECS.

#. .. _en-us_topic_0037470901__li19170660143341:

   Detach the EVS disk from the ECS.

   a. On the **Elastic Cloud Server** page, select this disk-intensive ECS and ensure that it has been stopped.

      If the ECS is running, choose **More** > **Stop** to stop the ECS.

   b. Click the name of the disk-intensive ECS. The page providing details about the ECS is displayed.

   c. Click the **Disks** tab. Locate the row containing the EVS data disk and click **Detach** to detach the disk from the ECS.

#. .. _en-us_topic_0037470901__li5892076615240:

   Ensure that a new disk-intensive ECS with higher specifications than the original one is available.

   The local disk capacity is sufficient enough to meet your requirements.

#. Attach the EVS disk to the new disk-intensive ECS.

   On the **Elastic Cloud Server** page, click the name of the ECS described in step :ref:`5 <en-us_topic_0037470901__li5892076615240>` to view details.

#. Click the **Disks** tab. Then, click **Attach Disk**.

   In the displayed dialog box, select the EVS disk detached in step :ref:`4 <en-us_topic_0037470901__li19170660143341>` and the device name.

#. Migrate the data from the EVS disk to the local disks of the new disk-intensive ECS.
