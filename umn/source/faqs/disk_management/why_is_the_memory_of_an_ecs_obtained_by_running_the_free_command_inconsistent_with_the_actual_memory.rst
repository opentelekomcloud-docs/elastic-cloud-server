:original_name: en-us_topic_0093153741.html

.. _en-us_topic_0093153741:

Why Is the Memory of an ECS Obtained by Running the free Command Inconsistent with the Actual Memory?
=====================================================================================================

Symptom
-------

After you create an ECS, you run the **free -m** command to view the ECS memory. The ECS memory is less than the memory configured during ECS creation.

For example:

When you are creating an ECS, the configured memory size is 4194304 KB (4096 MB). After the ECS is created, you run the **free -m** command to view its memory. The command output is as follows:

.. code-block:: console

   [root@localhost ~]# free -m
   total used free shared buff/cache available
   Mem: 3790 167 3474 8 147 3414
   Swap: 1022 0 1022

The memory in the command output is 3790 MB, which is less than the configured 4096 MB.

Run the **dmidecode -t memory** command to check the actual memory configured for the ECS. The command output is as follows:

.. code-block:: console

   [root@localhost ~]# dmidecode -t memory
   # dmidecode 3.0
   Getting SMBIOS data from sysfs.
   SMBIOS 2.8 present.

   Handle 0x1000, DMI type 16, 23 bytes
   Physical Memory Array
   Location: Other
   Use: System Memory
   Error Correction Type: Multi-bit ECC
   Maximum Capacity: 4 GB
   Error Information Handle: Not Provided
   Number Of Devices: 1

   Handle 0x1100, DMI type 17, 40 bytes
   Memory Device
   Array Handle: 0x1000
   Error Information Handle: Not Provided
   Total Width: Unknown
   Data Width: Unknown
   Size: 4096 MB
   Form Factor: DIMM
   Set: None
   Locator: DIMM 0
   Bank Locator: Not Specified
   Type: RAM
   Type Detail: Other
   Speed: Unknown
   Manufacturer: QEMU
   Serial Number: Not Specified
   Asset Tag: Not Specified
   Part Number: Not Specified
   Rank: Unknown
   Configured Clock Speed: Unknown
   Minimum Voltage: Unknown
   Maximum Voltage: Unknown
   Configured Voltage: Unknown

The memory in the command output is the same as that configured during ECS creation.

Possible Causes
---------------

When the OS is started, related devices are initialized, which occupies memory. In addition, when the kernel is started, it also occupies memory. The memory occupied by kdump can be set. Unless otherwise specified, do not change the memory size occupied by kdump.

The command output of **free -m** shows the available memory of the ECS, and that of **dmidecode -t memory** shows the hardware memory.

Therefore, the memory obtained by running the **free -m** command is less than the memory configured for the ECS. This is a normal phenomenon.

.. note::

   This is a normal phenomenon even for physical servers.
