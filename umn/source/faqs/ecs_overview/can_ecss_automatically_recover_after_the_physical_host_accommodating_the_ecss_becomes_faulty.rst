:original_name: en-us_topic_0095020344.html

.. _en-us_topic_0095020344:

Can ECSs Automatically Recover After the Physical Host Accommodating the ECSs Becomes Faulty?
=============================================================================================

Yes.

ECSs run on physical hosts. Although there are multiple mechanisms to ensure system reliability, fault tolerance, and high availability, host hardware might be damaged or power failures might occur. If physical hosts cannot be powered on or restarted due to damage, CPU and memory data will be lost and live migration cannot be used to recovery ECSs.

The cloud platform provides automatic recovery by default to restart ECSs through cold migration, ensuring high availability and dynamic ECS migration. If a physical host accommodating ECSs breaks down, the ECSs will automatically be migrated to a functional physical host to minimize the impact on your services. During the process, the ECSs will restart.

.. note::

   -  Automatic recovery does not ensure user data consistency.
   -  An ECS can be automatically recovered only if the physical server on which it is deployed becomes faulty. This function does not take effect if the fault is caused by the ECS itself.
   -  An ECS can be automatically recovered only after the physical server on which it is deployed is shut down. If the physical server is not shut down due to a fault, for example, a memory fault, automatic recovery fails to take effect.
   -  An ECS can be automatically recovered only once within 12 hours if the server on which it is deployed becomes faulty.
   -  ECS automatic recovery may fail in the following scenarios:

      -  No physical server is available for migration due to a system fault.
      -  The target physical server does not have sufficient temporary capacity.

   -  An ECS with any of the following resources cannot be automatically recovered:

      -  Local disk
      -  Passthrough FPGA card
      -  Passthrough InfiniBand NIC
