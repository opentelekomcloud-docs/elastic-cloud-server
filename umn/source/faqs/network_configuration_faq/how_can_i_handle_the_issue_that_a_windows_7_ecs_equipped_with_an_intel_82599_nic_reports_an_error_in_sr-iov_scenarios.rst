:original_name: en-us_topic_0053287548.html

.. _en-us_topic_0053287548:

How Can I Handle the Issue that a Windows 7 ECS Equipped with an Intel 82599 NIC Reports an Error in SR-IOV Scenarios?
======================================================================================================================

Symptom
-------

When the 20.4.1 driver package downloaded at Intel website `https://downloadcenter.intel.com/search?keyword=Intel++Ethernet+Connections+CD <https://downloadcenter.intel.com/search?keyword=Intel%2B%2BEthernet%2BConnections%2BCD>`__ was installed in a Windows 7 64bit ECS with SR-IOV passthrough enabled, the system displayed the message "No Intel adapter found".

Cause Analysis
--------------

The OS identifies an Intel 82599 passthrough NIC without a driver installed as an Ethernet controller. When the 20.4.1 driver package was installed, the OS did not identify the Intel NIC, leading to the error.

Solution
--------

Run **Autorun.exe** in the folder where the 20.4.1 driver package is stored. Install a driver on the NIC before installing the driver package so that the NIC can be identified as an Intel 82599 virtual function (VF) device by the OS. Use either of the following methods to install the driver:

-  Method 1: Update the version.

   #. Download the 18.6 driver package at the Intel website.
   #. Run **Autorun.exe**.
   #. Run **Autorun.exe** in the folder where the 20.4.1 driver package is stored to update the driver.

-  Method 2: Use the device manager.

   #. Start the Windows resource manager. Right-click **Computer** and choose **Manage** from the shortcut menu. In the **Device Manager** window, locate the NIC. When the NIC has no driver installed, the NIC locates in **Other devices** and is named **Ethernet Controller**.
   #. Right-click **Ethernet Controller** and choose **Update Driver Software**.
   #. Click **Browse**, select the path where the driver package is stored, and click **Next**.
   #. Locate the NIC in **Network Adapter** of **Device Manager**.
   #. Run **Autorun.exe** to install the 20.4.1 driver package.
