:original_name: en-us_topic_0057711189.html

.. _en-us_topic_0057711189:

Obtaining ECS Console Logs
==========================

Scenarios
---------

When an ECS cannot start or run properly, you can download and view ECS console logs for troubleshooting, for example, checking whether the kernel and service configuration are correct.

The ECS console logs record ECS operations, such as ECS starting, stopping, restarting, or forcibly restarting. Through the management console, you can obtain the ECS logs within one hour.

Notes
-----

-  The system does not record the logs for forcible ECS stopping.
-  The ECSs running Windows do not support console logs.
-  The system can save up to 100 KB log files.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the **Elastic Cloud Server** page, click the name of the target ECS.

#. On the ECS details page, click the **Console Logs** tab.

#. Choose the number of lines to be displayed for a log from the **Displayed Lines** drop-down list.

#. Click **Query**.

   View details of the displayed log.

   .. note::

      After you click **Query**, the system will not automatically update the displayed log. To view the latest log, click **Query** again.

      If console logs cannot be queried, check the default OS boot configuration by referring to :ref:`Configuring the Default OS Boot Configuration <en-us_topic_0057711189__section85971730182315>`.

#. (Optional) Click **Download** to download the information of the displayed log.

   Downloaded log files are in .txt format.

.. _en-us_topic_0057711189__section85971730182315:

Configuring the Default OS Boot Configuration
---------------------------------------------

#. Log in to the ECS.

#. Check and modify the grub file.

   The configuration method varies depending on the OS.

   .. note::

      To prevent impact on the start of the recovery mode, you are advised to modify only the item used for the default start.

   -  For CentOS 6 and Red Hat 6, perform the following steps:

      a. Run the following command to open the configuration file:

         **vi /boot/grub/menu.lst**

      b. Locate the row that contains **linux**, **linux16**, or **kernel** (depending on the system), add **console=ttyS0** to its end, and delete parameter **rhgb quiet**. If **console=ttyS0** already exists, you do not need to add it. Save the change and exit.

   -  For CentOS 7, Red Hat 7, and Ubuntu 14, perform the following steps:

      a. Run the following command to open the configuration file:

         **vi /boot/grub2/grub.cfg**

      b. Locate the row that contains **linux**, **linux16**, or **kernel** (depending on the system), add **console=ttyS0** to its end, and delete parameter **rhgb quiet**. If **console=ttyS0** already exists, you do not need to add it. Save the change and exit.

   -  For SUSE Linux 11, perform the following steps:

      a. Run the following command to open the configuration file:

         **vi /boot/grub/menu.1st**

      b. Locate the row that contains **linux**, **linux16**, or **kernel** (depending on the system) and add **console=ttyS0** to its end. If **console=ttyS0** already exists, you do not need to add it. Save the change and exit.

   -  For SUSE Linux 12, openSUSE 13, and openSUSE 42, perform the following steps:

      a. Run the following command to open the configuration file:

         **vi /boot/grub2/grub.cfg**

      b. Locate the row that contains **linux**, **linux16**, or **kernel** (depending on the system) and add **console=ttyS0** to its end. If **console=ttyS0** already exists, you do not need to add it. Save the change and exit.

   -  For Debian and Ubuntu 16, perform the following steps:

      a. Run the following command to open the configuration file:

         **vi /boot/grub/grub.cfg**

      b. Locate the row that contains **linux**, **linux16**, or **kernel** (depending on the system) and add **console=ttyS0** to its end. If **console=ttyS0** already exists, you do not need to add it. Save the change and exit.

   -  For Fedora, perform the following steps:

      a. Run the following command to open the configuration file:

         **vi /boot/grub2/grub.cfg**

      b. Locate the row that contains **linux**, **linux16**, or **kernel** (depending on the system) and add **console=ttyS0** to its end. If **console=ttyS0** already exists, you do not need to add it. Save the change and exit.

   -  For FreeBSD, perform the following steps:

      a. Run the following command to open the configuration file:

         **vi /boot/loader.conf**

      b. Add **console="comconsole"**. If **console="comconsole"** already exists, you do not need to add it. Save the change and exit.

   -  For CoreOS, perform the following steps:

      a. Run the following command to check whether **ttyS0** has been configured:

         **cat /proc/cmdline \| grep ttyS0**

         -  If yes, **ttyS0** has been configured.
         -  If no, **ttyS0** has not been configured. Go to :ref:`2.b <en-us_topic_0057711189__en-us_topic_0057450886_li29451607172853>`.

      b. .. _en-us_topic_0057711189__en-us_topic_0057450886_li29451607172853:

         Run the following command to open the configuration file to be edited:

         **vi /usr/share/oem/grub.cfg**

         .. note::

            If the **/usr/share/oem/grub.cfg** configuration file does not exist, manually create the file.

      c. Add **set linux_append="console=ttyS0"**. If **set linux_append="console=ttyS0"** already exists, you do not need to add it. Save the change and exit.

#. On the **Elastic Cloud Server** page, click **Restart**.

Related Links
-------------

:ref:`Why Does the System Display a Question Mark When I Attempt to Obtain Console Logs? <en-us_topic_0088241338>`

.. |image1| image:: /_static/images/en-us_image_0000002188678994.png
