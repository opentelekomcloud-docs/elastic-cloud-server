:original_name: en-us_topic_0000001143214829.html

.. _en-us_topic_0000001143214829:

How Do I Configure atop and kdump on Linux ECSs for Performance Analysis?
=========================================================================

Scenarios
---------

This section describes how you can configure atop and kdump on Linux ECSs for performance analysis.

The method for configuring atop varies with the OS version.

atop

-  :ref:`Introduction to atop <en-us_topic_0000001143214829__en-us_topic_0178319250_section0959133015350>`
-  :ref:`Configuring atop for CentOS 8 or RHEL 8 <en-us_topic_0000001143214829__en-us_topic_0178319250_section18897192721320>`
-  :ref:`Configuring atop for CentOS 7, RHEL 7, or EulerOS <en-us_topic_0000001143214829__en-us_topic_0178319250_section1972319582310>`
-  :ref:`Configuring atop for SUSE 12 or SUSE 15 <en-us_topic_0000001143214829__en-us_topic_0178319250_section3205824181917>`
-  :ref:`Configuring atop Using Its Source Package for SUSE, Fedora, Debian or Ubuntu <en-us_topic_0000001143214829__en-us_topic_0178319250_section012793312620>`

kdump

-  :ref:`Precautions for Configuring kdump <en-us_topic_0000001143214829__en-us_topic_0178319250_section1410131164120>`
-  :ref:`Introduction to kdump <en-us_topic_0000001143214829__en-us_topic_0178319250_section18450171174120>`
-  :ref:`Configuring kdump <en-us_topic_0000001143214829__en-us_topic_0178319250_section134381494320>`
-  :ref:`Checking Whether kdump Configurations Have Taken Effect <en-us_topic_0000001143214829__en-us_topic_0178319250_section1296112934412>`

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section0959133015350:

Introduction to atop
--------------------

atop is a monitor for Linux that can report the activity of all processes and resource consumption by all processes at regular intervals. It shows system-level activity related to the CPU, memory, disks, and network layers for every process. It also logs system and process activities daily and saves the logs in disks for long-term analysis.

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section18897192721320:

Configuring atop for CentOS 8 or RHEL 8
---------------------------------------

#. Run the following command to download the atop package:

   **# wget https://www.atoptool.nl/download/atop-2.6.0-1.el8.x86_64.rpm**

#. Run the following command to install the package:

   **# rpm -ivh atop-2.6.0-1.el8.x86_64.rpm**

#. Run the following command to modify the configuration file of atop:

   **# vi /etc/default/atop**

   Modify the following parameters, save the modification, and exit:

   -  Change the value of **LOGINTERVAL** to, for example, **15**. The default value of **LOGINTERVAL** is **600**, in seconds.

   -  Change the value of **LOGGENERATIONS** to, for example, **3**. The default retention period of atop logs is **28** days.

      .. code-block::

         LOGINTERVAL=15
         LOGGENERATIONS=3

4. Run the following command to restart atop:

   **# systemctl restart atop**

5. Run the following command to check the status of atop. If **active (running)** is displayed in the output, atop is running properly.

   **# systemctl status atop**

   .. code-block::

      atop.service - Atop advanced performance monitor
      Loaded: loaded (/usr/lib/systemd/system/atop.service; enabled; vendor preset: disabled)
      Active: active (running) since Sat 2021-06-19 14:46:10 CST; 8s ago
      Docs: man:atop(1)
      Process: 6391 ExecStartPost=/usr/bin/find ${LOGPATH} -name atop_* -mtime +${LOGGENERATIONS} -exec rm -v {} ; (code=exited, status=0/SUCCESS)
      Process: 6388 ExecStartPre=/bin/sh -c test -n "$LOGGENERATIONS" -a "$LOGGENERATIONS" -eq "$LOGGENERATIONS" (code=exited, status=0/SUCCESS)
      Process: 6387 ExecStartPre=/bin/sh -c test -n "$LOGINTERVAL" -a "$LOGINTERVAL" -eq "$LOGINTERVAL" (code=exited, status=0/SUCCESS)
      Main PID: 6390 (atop)
      Tasks: 1 (limit: 23716)
      Memory: 4.1M
      CGroup: /system.slice/atop.service
               └─6390 /usr/bin/atop -w /var/log/atop/atop_20210619 15

      Jun 19 14:46:10 ecs-centos8 systemd[1]: atop.service: Succeeded.
      Jun 19 14:46:10 ecs-centos8 systemd[1]: Stopped Atop advanced performance monitor.
      Jun 19 14:46:10 ecs-centos8 systemd[1]: Starting Atop advanced performance monitor...
      Jun 19 14:46:10 ecs-centos8 systemd[1]: Started Atop advanced performance monitor.

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section1972319582310:

Configuring atop for CentOS 7, RHEL 7, or EulerOS
-------------------------------------------------

#. Run the following command to download the atop package:

   **# wget https://www.atoptool.nl/download/atop-2.6.0-1.el7.x86_64.rpm**

   Upload the **atop-2.6.0-1.el7.x86_64.rpm** package to the target ECS.

#. Run the following command to install atop:

   **# rpm -ivh atop-2.6.0-1.el7.x86_64.rpm --nodeps**

#. Run the following command to modify the configuration file of atop:

   **# vi /etc/default/atop**

   Modify the following parameters, save the modification, and exit:

   -  Change the value of **LOGINTERVAL** to, for example, **15**. The default value of **LOGINTERVAL** is **600**, in seconds.
   -  Change the value of **LOGGENERATIONS** to, for example, **3**. The default retention period of atop logs is **28** days.

   .. code-block::

      LOGINTERVAL=15
      LOGGENERATIONS=3

#. Run the following command to start atop:

   **# systemctl start atop**

#. Run the following command to check the status of atop. If **active (running)** is displayed in the output, atop is running properly.

   **# systemctl status atop**

   atop will sample system performance data based on the specified interval and save the data to the **/var/log/atop/** directory.

   .. code-block::

      atop.service - Atop advanced performance monitor
      Loaded: loaded (/usr/lib/systemd/system/atop.service; enabled; vendor preset: disabled)
      Active: active (running) since Sat 2021-06-19 11:49:47 CST; 2h 27min ago
      Docs: man:atop(1)
      Process: 8231 ExecStartPost=/usr/bin/find ${LOGPATH} -name atop_* -mtime +${LOGGENERATIONS} -exec rm -v {} ; (code=exited, status=0/SUCCESS)
      Process: 8225 ExecStartPre=/bin/sh -c test -n "$LOGGENERATIONS" -a "$LOGGENERATIONS" -eq "$LOGGENERATIONS" (code=exited, status=0/SUCCESS)
      Process: 8223 ExecStartPre=/bin/sh -c test -n "$LOGINTERVAL" -a "$LOGINTERVAL" -eq "$LOGINTERVAL" (code=exited, status=0/SUCCESS)
      Main PID: 8229 (atop)
      CGroup: /system.slice/atop.service
               └─8229 /usr/bin/atop -w /var/log/atop/atop_20210619 15

      Jun 19 11:49:47 ecs-centos7 systemd[1]: Stopped Atop advanced performance monitor.
      Jun 19 11:49:47 ecs-centos7 systemd[1]: Starting Atop advanced performance monitor...
      Jun 19 11:49:47 ecs-centos7 systemd[1]: Started Atop advanced performance monitor.

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section3205824181917:

Configuring atop for SUSE 12 or SUSE 15
---------------------------------------

#. Run the following command to download the atop source package:

   **# wget https://www.atoptool.nl/download/atop-2.6.0-1.src.rpm**

#. Run the following command to install the package:

   **# rpm -ivh atop-2.6.0-1.src.rpm**

#. Run the following command to install atop dependencies.

   **# zypper -n install rpm-build ncurses-devel zlib-devel**

#. Run the following command to compile atop:

   **# cd /usr/src/packages/SPECS**

   **# rpmbuild -bb atop-2.6.0.spec**

#. Run the following command to install atop:

   **# cd /usr/src/packages/RPMS/x86_64**

   **# rpm -ivh atop-2.6.0-1.x86_64.rpm**

#. Run the following command to modify the configuration file of atop:

   **# vi /etc/default/atop**

   Modify the following parameters, save the modification, and exit:

   -  Change the value of **LOGINTERVAL** to, for example, **15**. The default value of **LOGINTERVAL** is **600**, in seconds.
   -  Change the value of **LOGGENERATIONS** to, for example, **3**. The default retention period of atop logs is **28** days.

   .. code-block::

      LOGINTERVAL=15
      LOGGENERATIONS=3

7. Run the following command to restart atop:

   **# systemctl restart atop**

8. Run the following command to check the status of atop. If **active (running)** is displayed in the output, atop is running properly.

   **# systemctl status atop**

   .. code-block::

      atop.service - Atop advanced performance monitor
      Loaded: loaded (/usr/lib/systemd/system/atop.service; enabled; vendor preset: disabled)
      Active: active (running) since Sat 2021-06-19 16:50:01 CST; 6s ago
      Docs: man:atop(1)
      Process: 2242 ExecStartPost=/usr/bin/find ${LOGPATH} -name atop_* -mtime +${LOGGENERATIONS} -exec rm -v {} ; (code=exited, status=0/SUCCESS)
      Process: 2240 ExecStartPre=/bin/sh -c test -n "$LOGGENERATIONS" -a "$LOGGENERATIONS" -eq "$LOGGENERATIONS" (code=exited, status=0/SUCCESS)
      Process: 2239 ExecStartPre=/bin/sh -c test -n "$LOGINTERVAL" -a "$LOGINTERVAL" -eq "$LOGINTERVAL" (code=exited, status=0/SUCCESS)
      Main PID: 2241 (atop)
      Tasks: 1 (limit: 4915)
      CGroup: /system.slice/atop.service
               └─2241 /usr/bin/atop -w /var/log/atop/atop_20210619 15

      Jun 19 16:50:01 ecs-suse15 systemd[1]: Starting Atop advanced performance monitor...
      Jun 19 16:50:01 ecs-suse15 systemd[1]: Started Atop advanced performance monitor.

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section012793312620:

Configuring atop Using Its Source Package for SUSE, Fedora, Debian or Ubuntu
----------------------------------------------------------------------------

#. Download the atop source package.

   **# wget https://www.atoptool.nl/download/atop-2.6.0.tar.gz**

2. Decompress the source package.

   **# tar -zxvf atop-2.6.0.tar.gz**

3. Query the systemctl version.

   **# systemctl --version**

   If the version is 220 or later, go to the next step.

   Otherwise, delete parameter **--now** from the Makefile of atop.

   **# vi atop-2.6.0/Makefile**

   Delete parameter **--now** following the systemctl command.

   .. code-block::

                      then   /bin/systemctl disable  atop     2> /dev/null; \
                              /bin/systemctl disable  atopacct 2> /dev/null; \
                              /bin/systemctl daemon-reload;                   \
                              /bin/systemctl enable   atopacct;          \
                              /bin/systemctl enable   atop;              \
                              /bin/systemctl enable   atop-rotate.timer; \

4. Install atop dependencies.

   -  SUSE 12 or SUSE 15

      **# zypper -n install make gcc zlib-devel ncurses-devel**

   -  Fedora

      **# yum install make gcc zlib-devel ncurses-devel -y**

   -  Debian 9, Debian 10, or Ubuntu

      **# apt install make gcc zlib1g-dev libncurses5-dev libncursesw5-dev -y**

5. Compile and install atop.

   **# cd atop-2.6.0**

   **# make systemdinstall**

6. Modify the configuration file of atop.

   **# vi /etc/default/atop**

   Make the following modifications, save the file, and exit.

   -  Change the value of **LOGINTERVAL** to, for example, **15**. The default value of **LOGINTERVAL** is **600**, in seconds.

   -  Change the value of **LOGGENERATIONS** to, for example, **3**. The default retention period of atop logs is **28** days.

      .. code-block::

         LOGOPTS=""
         LOGINTERVAL=15
         LOGGENERATIONS=3
         LOGPATH=/var/log/atop

7. Restart atop.

   **# systemctl restart atop**

8. Run the following command to check the status of atop. If **active (running)** is displayed in the output, atop is running properly.

   **# systemctl status atop**

   .. code-block::

      atop.service - Atop advanced performance monitor
         Loaded: loaded (/lib/systemd/system/atop.service; enabled)
         Active: active (running) since Sun 2021-07-25 19:29:40 CST; 4s ago
           Docs: man:atop(1)
        Process: 5192 ExecStartPost=/usr/bin/find ${LOGPATH} -name atop_* -mtime +${LOGGENERATIONS} -exec rm -v {} ; (code=exited, status=0/SUCCESS)
        Process: 5189 ExecStartPre=/bin/sh -c test -n "$LOGGENERATIONS" -a "$LOGGENERATIONS" -eq "$LOGGENERATIONS" (code=exited, status=0/SUCCESS)
        Process: 5188 ExecStartPre=/bin/sh -c test -n "$LOGINTERVAL" -a "$LOGINTERVAL" -eq "$LOGINTERVAL" (code=exited, status=0/SUCCESS)
       Main PID: 5191 (atop)
         CGroup: /system.slice/atop.service
                 └─5191 /usr/bin/atop -w /var/log/atop/atop_20210725 15

      Jul 25 19:29:40 atop systemd[1]: Starting Atop advanced performance monitor...
      Jul 25 19:29:40 atop systemd[1]: Started Atop advanced performance monitor.

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section1410131164120:

Precautions for Configuring kdump
---------------------------------

The method for configuring kdump described in this section applies to KVM ECSs running EulerOS or CentOS 7.x. For details, see `Documentation for kdump <https://www.kernel.org/doc/Documentation/kdump/kdump.txt>`__.

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section18450171174120:

Introduction to kdump
---------------------

kdump is a feature of the Linux kernel that creates crash dumps in the event of a kernel crash. In the event of a kernel crash, kdump boots another Linux kernel and uses it to export an image of RAM, which is known as vmcore and can be used to debug and determine the cause of the crash.

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section134381494320:

Configuring kdump
-----------------

#. Run the following command to check whether kexec-tools is installed:

   **# rpm -q kexec-tools**

   If it is not installed, run the following command to install it:

   **# yum install -y kexec-tools**

#. Run the following command to enable kdump to run at system startup:

   **# systemctl enable kdump**

#. Configure the parameters for the crash kernel to reserve the memory for the capture kernel.

   Check whether the parameters are configured.

   **# grep crashkernel /proc/cmdline**

   If the command output is displayed, this parameter has been configured.

   Edit the **/etc/default/grub** file to configure the following parameters:

   .. code-block::

      GRUB_TIMEOUT=5
      GRUB_DEFAULT=saved
      GRUB_DISABLE_SUBMENU=true
      GRUB_TERMINAL_OUTPUT="console"
      GRUB_CMDLINE_LINUX="crashkernel=auto rd.lvm.lv=rhel00/root rd.lvm.lv=rhel00/swap
      rhgb quiet"
      GRUB_DISABLE_RECOVERY="true"

   Locate parameter **GRUB_CMDLINE_LINUX** and add **crashkernel=auto** after it.

#. Run the following command for the configuration to take effect:

   **# grub2-mkconfig -o /boot/grub2/grub.cfg**

#. Open the **/etc/kdump.conf** file, locate parameter **path**, and add **/var/crash** after it.

   .. code-block::

      path  /var/crash

   By default, the file is saved in the **/var/crash** directory.

   You can save the file to another directory, for example, **/home/kdump**. Then add **/home/kdump** after parameter **path**:

   .. code-block::

      path  /home/kdump

   .. note::

      There must be enough space in the specified path for storing the vmcore file. It is recommended that the available space be greater than or equal to the RAM size. You can also store the vmcore file on a shared device such as SAN or NFS.

#. Set the vmcore dump level.

   Add the following content to file **/etc/kdump.conf**. If the content already exists, skip this step.

   .. code-block::

      core_collector makedumpfile -d 31 -c

   where

   **-c** indicates compressing the vmcore file.

   **-d** indicates leaving out irrelevant data. Generally, the value following **-d** is **31**, which is calculated based on the following values. You can adjust the value if needed.

   .. code-block::

      zero pages   = 1
      cache pages   = 2
      cache private = 4
      user  pages   = 8
      free  pages   = 16

#. Run the following command to restart the system for the configurations to take effect:

   **# reboot**

.. _en-us_topic_0000001143214829__en-us_topic_0178319250_section1296112934412:

Checking Whether kdump Configurations Have Taken Effect
-------------------------------------------------------

#. Run the following command and check whether **crashkernel=auto** is displayed:

   **#** **cat /proc/cmdline \|grep crashkernel**

   .. code-block::

      BOOT_IMAGE=/boot/vmlinuz-3.10.0-514.44.5.10.h142.x86_64 root=UUID=6407d6ac-c761-43cc-a9dd-1383de3fc995 ro crash_kexec_post_notifiers softlockup_panic=1 panic=3 reserve_kbox_mem=16M nmi_watchdog=1 rd.shell=0 fsck.mode=auto fsck.repair=yes net.ifnames=0 spectre_v2=off nopti noibrs noibpb crashkernel=auto LANG=en_US.UTF-8

#. Run the following command and check whether the configuration in the output is correct:

   **# grep core_collector /etc/kdump.conf \|grep -v ^"#"**

   .. code-block::

      core_collector makedumpfile -l --message-level 1 -d 31

#. Run the following command and check whether the path configuration in the output is correct:

   **# grep path /etc/kdump.conf \|grep -v ^"#"**

   .. code-block::

      path /var/crash

#. Run the following command and check whether the value of **Active** in the output is **active (exited)**:

   **# systemctl status kdump**

   .. code-block::

      ● kdump.service - Crash recovery kernel arming
      Loaded: loaded (/usr/lib/systemd/system/kdump.service; enabled; vendor preset: enabled)
      Active: active (exited) since Tue 2019-04-09 19:30:24 CST; 8min ago
      Process: 495 ExecStart=/usr/bin/kdumpctl start (code=exited, status=0/SUCCESS)
      Main PID: 495 (code=exited, status=0/SUCCESS)
      CGroup: /system.slice/system-hostos.slice/kdump.service

#. Run the following test command:

   **# echo c > /proc/sysrq-trigger**

   After the command is executed, kdump will be triggered, the system will be restarted, and the generated vmcore file will be saved to the path specified by **path**.

#. Run the following command to check whether the vmcore file has been generated in the specified path, for example, **/var/crash/**:

   **# ll /var/crash/**
