:original_name: en-us_topic_0100005619.html

.. _en-us_topic_0100005619:

How Can I Log In to an ECS After Its System Disk Is Exchanged with That Attached to Another ECS Running the Same OS?
====================================================================================================================

Symptom
-------

Two ECSs run the same OS, for example, both run Windows or Linux. The system disks attached to the two ECSs are exchanged offline. After the exchanging, the login keys of the ECSs may change. In such a case, how can I log in to the ECSs?

.. note::

   Before stopping an ECS for disk detachment, release the IP address assigned to the ECS using DHCP so that ECS can correctly obtain an IP address later. To do so, perform the following operations:

   #. Log in to the Windows ECS.

   #. Run the following command to release the IP address:

      **ipconfig /release**

      This operation will interrupt network connections and affect the use of the ECS. After the ECS is restarted, network connections will automatically recover.

Windows
-------

For example, there are two Windows ECSs with parameters configured in :ref:`Table 1 <en-us_topic_0100005619__table1365540183310>`.

.. _en-us_topic_0100005619__table1365540183310:

.. table:: **Table 1** Parameter configurations

   ====== =========== ==========
   ECS    System Disk Key Pair
   ====== =========== ==========
   ecs_01 vol_01      Keypair_01
   ecs_02 vol_02      Keypair_02
   ====== =========== ==========

System disk vol_01 is detached from ecs_01 offline and then attached to ecs_02 as the system disk. How can I log in to ecs_02?

The random password for logging in to ecs_02 must be resolved again. The procedure is as follows:

#. Delete the initial password for logging in to ecs_02.

   Locate the row containing ecs_02, click **More** in the **Operation** column, and select **Delete Password** from the drop-down list. Then, click **Delete**.

   .. note::

      ecs_02 must be in **Stopped** state.

#. Start ecs_02.

   Locate the row containing ecs_02, click **More** in the **Operation** column, and select **Start** from the drop-down list. Then, in the **Start ECS** dialog box, click **OK**.

#. .. _en-us_topic_0100005619__li138721252141517:

   Obtain the password for logging in to ecs_02.

   a. Locate the row containing ecs_02, click **More** in the **Operation** column, and select **Get Password** from the drop-down list.
   b. Click **Select File** and upload private key file **Keypair_02** of ecs_02.
   c. Click **Get Password** to obtain a new random password.

#. Use the random password obtained in step :ref:`3 <en-us_topic_0100005619__li138721252141517>` to log in to ecs_02 with the system disk replaced.

Linux
-----

For example, there are two Linux ECSs with parameters configured in :ref:`Table 2 <en-us_topic_0100005619__table9561950195614>`.

.. _en-us_topic_0100005619__table9561950195614:

.. table:: **Table 2** Parameter configurations

   ====== =========== ==========
   ECS    System Disk Key Pair
   ====== =========== ==========
   ecs_01 vol_01      Keypair_01
   ecs_02 vol_02      Keypair_02
   ====== =========== ==========

System disk vol_01 is detached from ecs_01 offline and then attached to ecs_02 as the system disk. How can I log in to ecs_02?

Use either of the following methods to log in to ecs_02:

-  Use private key file **Keypair_01** of ecs_01.
-  Use private key file **Keypair_02** of ecs_02.
