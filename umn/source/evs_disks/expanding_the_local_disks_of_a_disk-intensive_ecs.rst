.. _en-us_topic_0037470901:

Expanding the Local Disks of a Disk-intensive ECS
=================================================



.. _en-us_topic_0037470901__section53331929201453:

Scenarios
---------

Disk-intensive ECSs can use both local disks and EVS disks to store data. Local disks are generally used to store service data and feature higher throughput than EVS disks.

Disk-intensive ECSs do not support modifying specifications. Therefore, when the idle capacity of the local disks of such an ECS is insufficient, you must create a new disk-intensive ECS with higher specifications for capacity expansion. In such a case, the data stored in the original ECS can be migrated to the new ECS through an EVS disk.



.. _en-us_topic_0037470901__section712673201458:

Procedure
---------

#. `Create an EVS disk <https://docs.otc.t-systems.com/usermanual/evs/en-us_topic_0021738346.html>`__ according to the volume of data to be migrated.

#. Attach the EVS disk to the disk-intensive ECS.

#. Back up the data stored in the local disks to the EVS disk that is newly attached to the disk-intensive ECS.

#. Detach the EVS disk from the ECS.

   a. On the **Elastic Cloud Server** page, select this disk-intensive ECS and ensure that it is **Stopped**.

      If the ECS is in the **Running** state, choose **More** > **Stop** to stop it.

   b. Click the name of the disk-intensive ECS. The page providing details about the ECS is displayed.

   c. Click the **Disks** tab. Locate the row containing the EVS data disk and click **Detach** to detach the disk from the ECS.

#. Ensure that a new disk-intensive ECS with higher specifications than the original one is available.

   The idle local disk capacity of the new ECS must meet service requirements.

#. Attach the EVS disk to the new disk-intensive ECS.

   On the **Elastic Cloud Server** page, click the name of the ECS described in step 5. The page providing details about the ECS is displayed.

#. Click the **Disks** tab. Then, click **Attach Disk**.

   In the displayed dialog box, select the EVS disk detached in step 4 and the device name.

#. Migrate the data from the EVS disk to the local disks of the new disk-intensive ECS.
