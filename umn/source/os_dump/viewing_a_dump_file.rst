:original_name: en-us_topic_0000001773282304.html

.. _en-us_topic_0000001773282304:

Viewing a Dump File
===================

Scenarios
---------

After triggering an OS dump, you can view the generated memory dump file on your ECS.

This section describes how to trigger an OS dump and view the generated kernel dump file.

-  :ref:`Triggering an OS Dump <en-us_topic_0000001773282304__section77341370519>`
-  :ref:`Viewing a Dump File (Windows) <en-us_topic_0000001773282304__section764411013336>`
-  :ref:`Viewing a Dump File (Linux) <en-us_topic_0000001773282304__section3834163333514>`

Prerequisites
-------------

Operations described in :ref:`Configuring OS Dump <en-us_topic_0000001773122612>` have been completed.

.. _en-us_topic_0000001773282304__section77341370519:

Triggering an OS Dump
---------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and project.
#. Under **Computing**, choose **Elastic Cloud Server**.
#. In the ECS list, locate the row containing the target ECS and choose **More** > **Troubleshoot** > **Trigger OS Dump** in the **Operation** column.
#. Learn about the OS dump risks and select the checkbox.
#. Click **OK** to trigger an OS dump.

.. _en-us_topic_0000001773282304__section764411013336:

Viewing a Dump File (Windows)
-----------------------------

Windows Server 2016 is used as an example. For operations on more versions, see the help documents provided on the corresponding official website.

#. :ref:`Log in to a Windows ECS <en-us_topic_0092494943>`.

#. Go to the path specified in :ref:`Configuring an OS Dump (Windows) <en-us_topic_0000001773122612__section0468125016518>` to view the generated kernel dump file.

   For example, view the generated **MEMORY.DMP** file in **E:\\**.

   You can use tools to check and analyze the dump files. For details, see `Analyzing a Kernel-Mode Dump File <https://learn.microsoft.com/en-us/windows-hardware/drivers/debugger/analyzing-a-kernel-mode-dump-file>`__.

.. _en-us_topic_0000001773282304__section3834163333514:

Viewing a Dump File (Linux)
---------------------------

CentOS 7.5 is used as an example. For operations on more versions, see the help documents provided on the corresponding official website.

#. :ref:`Log in to a Linux ECS <en-us_topic_0013771089>`.

#. Check whether a dump file is generated.

   **ls /var/crash/**

   .. code-block::

      127.0.0.1-2024-05-22-21:35:26

   You can use the crash tool in Linux to analyze the dump files. For details, see `Crash <https://crash-utility.github.io/crash_whitepaper.html#WHY_CRASH>`__.

.. |image1| image:: /_static/images/en-us_image_0000002188678994.png
