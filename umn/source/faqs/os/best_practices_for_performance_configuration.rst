:original_name: en-us_topic_0000002498531278.html

.. _en-us_topic_0000002498531278:

Best Practices for Performance Configuration
============================================

C-states control the sleep levels that a CPU can enter when it is idle. The sleep levels are numbered from C0 (the CPU is executing instructions) to C6 (the deepest sleep level where the CPU is in a very low-power state). When the CPU enters a deeper C-state, the wake-up time increases. In some load scenarios that require high real-time performance, the performance is affected. Therefore, if you have high requirements on performance stability, set the C-state to C1 to reduce the CPU response, ping, and TCP/UDP latency.

Procedure
---------

This section uses c9.large.2 and HCE 2.0 as an example to describe how to disable deep hibernation for CPUs. The command output varies depending on ECS flavors and images.

#. Log in to the target ECS.

   For details, see `Login Overview (Linux) <https://docs.otc.t-systems.com/en-us/usermanual/ecs/en-us_topic_0013771089.html>`__.

#. Run the following command to check **CPUidle driver** and supported C-states:

   .. code-block:: text

      cpupower idle-info

   The figure below shows the command output. **Number of idle states** indicates the number of supported C-states, and **Available idle states** indicates the supported C-states.

   .. note::

      If no **CPUidle driver** is displayed in the command output, you may need to update the image.

   |image1|

#. Modify the C-states parameters in the **/etc/default/grub** file.

   a. Open the **/etc/default/grub** file.

      .. code-block:: text

         sudo vim /etc/default/grub

   b. Press **i** to enter insert mode.

   c. Locate the **GRUB_CMDLINE_LINUX=** line and add **intel_idle.max_cstate=1** and **processor.max_cstate=1** to the end of it to set the deepest C-state of idle CPUs to C1.

      |image2|

   d. Press **Esc**, type **:wq**, and press **Enter** to save the file and exit.

   e. Regenerate the grub configuration file.

      .. code-block:: text

         sudo grub2-mkconfig -o /boot/grub2/grub.cfg

      .. note::

         The GRUB file address varies depending on the image or boot mode. For example, in the HCE 2.0 UEFI boot mode, the command is **sudo grub2-mkconfig -o /boot/efi/EFI/hce/grub.cfg**.

         Run the following command to query the boot mode:

         .. code-block:: text

            [ -d /sys/firmware/efi ] && echo "UEFI Boot Detected" || echo "Legacy BIOS Boot Detected"

#. Restart the ECS for the configuration to take effect.

   .. code-block:: text

      sudo reboot

#. Run the following command to check **CPUidle driver** and supported C-states:

   .. code-block:: text

      cpupower idle-info

   If the command output shown in the following figure is displayed, the system supports only two C-states (POLL and C1).

   |image3|

.. |image1| image:: /_static/images/en-us_image_0000002279078497.png
.. |image2| image:: /_static/images/en-us_image_0000002278168889.png
.. |image3| image:: /_static/images/en-us_image_0000002278999697.png
