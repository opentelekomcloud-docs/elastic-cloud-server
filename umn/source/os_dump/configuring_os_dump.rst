:original_name: en-us_topic_0000001773122612.html

.. _en-us_topic_0000001773122612:

Configuring OS Dump
===================

Scenarios
---------

If your ECS OS becomes faulty, a system crash or blue screen of death (BSOD) may occur. In this case, you can configure OS dump to enable the memory data to be stored in a file. This helps fault location and analysis.

This section describes how to configure an OS dump.

-  :ref:`Configuring an OS Dump (Windows) <en-us_topic_0000001773122612__section0468125016518>`
-  :ref:`Configuring an OS Dump (Linux) <en-us_topic_0000001773122612__section1689212435212>`

Background
----------

An OS dump is also known as a kernel dump or crash dump. When a system crash occurs, the memory data is completely backed up in real time.

The OS dump function relies on the OS kernel's capability of processing hardware exceptions. The OS kernel can detect hardware exceptions and determine the handling method based on the exception type. If the system encounters an exception or error that cannot be handled, some or all information will be dumped to disks. The information includes the CPU register, physical memory, process status, file system status, and hardware device status.

An OS dump can be triggered in the following ways:

-  System crash: When an exception or error that cannot be handled occurs, such as invalid memory access or kernel panic, the system automatically triggers a dump.
-  Manual triggering: The system administrator can use commands or operations to manually trigger a dump. For example, in Linux, the system administrator can add the parameter **c** to **/proc/sysrq-trigger** to trigger a dump.
-  Scheduled triggering: The system administrator can schedule a dump at a specified time to simulate a system crash and obtain the system information at that time.

To obtain a dump file, you need to configure the OS of your ECS. For example, in the Linux OS, you need to configure kdump. The following describes how to manually trigger a dump.

Constraints
-----------

-  An OS dump will cause the ECS to restart. Back up data in advance to prevent data loss.
-  OS dump is only available for ECSs in the **Running** and **Faulty** state.
-  OS dump is only recommended for ECSs with at least 4 vCPUs and 8 GiB of memory.
-  The target location for storing the dump file must have sufficient available space, which must be greater than the memory size of the ECS.

.. _en-us_topic_0000001773122612__section0468125016518:

Configuring an OS Dump (Windows)
--------------------------------

Windows Server 2016 is used as an example. For operations on more versions, see the help documents provided on the corresponding official website.

#. :ref:`Log in to a Windows ECS <en-us_topic_0092494943>`.

#. Open **Control Panel** and choose **System** > **Advanced system settings**.


   .. figure:: /_static/images/en-us_image_0000001934673973.png
      :alt: **Figure 1** Advanced system settings

      **Figure 1** Advanced system settings

#. In the **Performance** area of the **System Properties** dialog box, click **Settings**.

#. In the **Virtual memory** area on the **Advanced** tab, click **Change**.


   .. figure:: /_static/images/en-us_image_0000001891661536.png
      :alt: **Figure 2** Performance options

      **Figure 2** Performance options

#. In the **Virtual Memory** dialog box, select **Automatically manage paging file size for all drives**.


   .. figure:: /_static/images/en-us_image_0000001891443900.png
      :alt: **Figure 3** Virtual memory

      **Figure 3** Virtual memory

#. Click **OK** to complete the virtual memory settings.

#. In the **Startup and Recovery** area of the **System Properties** dialog box, click **Settings**.

#. Configure required parameters.

   -  **Write debugging information**: Select **Complete memory dump**.
   -  **Dump file**: Change *%SystemRoot%\\MEMORY.DMP* to a local drive with sufficient disk space, such as *E:\\MEMORY.DMP*.


   .. figure:: /_static/images/en-us_image_0000001891436096.png
      :alt: **Figure 4** Startup and recovery settings

      **Figure 4** Startup and recovery settings

#. Click **OK**.

#. Restart the ECS to complete the settings.

.. _en-us_topic_0000001773122612__section1689212435212:

Configuring an OS Dump (Linux)
------------------------------

CentOS 7.5 is used as an example. For operations on more versions, see the help documents provided on the corresponding official website.

#. :ref:`Log in to a Linux ECS <en-us_topic_0013771089>`.

#. Install kexec-tools.

   **yum install kexec-tools**

#. Check the size of the memory reserved for **crashkernel**.

   **cat /etc/default/grub**

   .. code-block::

      GRUB_TIMEOUT=5
      GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"
      GRUB_DEFAULT=saved
      GRUB_DISABLE_SUBMENU=true
      GRUB_TERMINAL_OUTPUT="console"
      GRUB_CMDLINE_LINUX="net.ifnames=0 consoleblank=600 console=tty0 console=ttyS0,115200n8 spectre_v2=off nopti crashkernel=auto  "
      GRUB_DISABLE_RECOVERY="true"

#. Adjust the reserved memory size by changing the value of **crashkernel**.

   **vim /etc/default/grub**

   The reserved memory size for **crashkernel** is **auto**. You can adjust the reserved memory size by changing the value of **crashkernel** in the **GRUB_CMDLINE_LINUX** field.

   .. code-block::

      GRUB_TIMEOUT=5
      GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"
      GRUB_DEFAULT=saved
      GRUB_DISABLE_SUBMENU=true
      GRUB_TERMINAL_OUTPUT="console"
      GRUB_CMDLINE_LINUX="net.ifnames=0 consoleblank=600 console=tty0 console=ttyS0,115200n8 spectre_v2=off nopti crashkernel=256M"
      GRUB_DISABLE_RECOVERY="true"

   .. note::

      You can determine the reserved memory size for **crashkernel** based on the system architecture. If the size is too small, the coredump file may fail to be generated.

      In this example, the system memory is 8 GiB, and the reserved memory is 256 MiB.

#. Generate a new grub configuration file.

   **grub2-mkconfig -o /boot/grub2/grub.cfg**

#. Edit the kernel parameter file **/etc/sysctl.conf**.

   **vim /etc/sysctl.conf**

   Add the following parameters to the **/etc/sysctl.conf** file to enable the system to trigger a kernel panic when receiving an unrecoverable or unknown NMI, allowing kdump to generate a memory dump.

   .. code-block::

      kernel.panic_on_unrecovered_nmi=1
      kernel.unknown_nmi_panic=1

#. Reboot the system.

   **reboot**

#. Open **/etc/kdump.conf** and modify the default configuration.

   **vim /etc/kdump.conf**

   .. code-block::

      # Specify the path where the coredump file is stored.
      path /var/crash
      # Add the parameter -c to compress the coredump file.
      core_collector makedumpfile -c -l --message-level 1 -d 31
      # Reboot the system after the coredump file is generated.
      default reboot

#. Start kdump and enable auto-start upon system boot.

   **systemctl start kdump.service**

   **systemctl enable kdump.service**

#. Check whether kdump is started.

   **service kdump status**

   .. code-block::

      Redirecting to /bin/systemctl status kdump.service
      ● kdump.service - Crash recovery kernel arming
         Loaded: loaded (/usr/lib/systemd/system/kdump.service; enabled; vendor preset: enabled)
         Active: active (exited) since Wed 2024-05-22 21:19:47 CST; 11min ago
       Main PID: 591 (code=exited, status=0/SUCCESS)
         CGroup: /system.slice/kdump.service

   **systemctl is-active kdump.service**

   .. code-block::

      active

Triggering an OS Dump
---------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and project.
#. Under **Computing**, choose **Elastic Cloud Server**.
#. In the ECS list, locate the row containing the target ECS and choose **More** > **Troubleshoot** > **Trigger OS Dump** in the **Operation** column.
#. Learn about the OS dump risks and select the checkbox.
#. Click **OK** to trigger an OS dump.

.. |image1| image:: /_static/images/en-us_image_0000002188678994.png
