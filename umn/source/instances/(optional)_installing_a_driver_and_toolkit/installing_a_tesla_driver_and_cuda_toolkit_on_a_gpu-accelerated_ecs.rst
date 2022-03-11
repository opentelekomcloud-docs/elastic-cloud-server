Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS
===================================================================

Scenarios
---------

Before using a GPU-accelerated ECS, make sure that the desired Tesla driver and CUDA toolkit have been installed on the ECS for computing acceleration.

-  A computing-accelerated (P series) ECS created using a Windows public image has had a Tesla driver of a specified version installed by default.
-  A computing-accelerated (P series) ECS created using a Linux public image does not have a Tesla driver installed by default. After the ECS is created, install a driver on it for computing acceleration.
-  After a GPU-accelerated ECS is created using a private image, it must have a Tesla driver installed. Otherwise, computing acceleration will not take effect.

This section describes how to install a Tesla driver and CUDA toolkit on a GPU-accelerated ECS.

Notes
-----

-  The target ECS has an EIP bound.
-  The Tesla driver and CUDA toolkit have not been installed on the ECS.

|image1|

-  Download the CUDA toolkit from the official NVIDIA website and install it. A Tesla driver matching the CUDA version will be automatically installed then. However, if there are specific requirements or dependencies on the Tesla driver version, download the matching Tesla driver from the official NVIDIA website first and then install the driver before installing the CUDA toolkit.
-  If a Tesla driver has been installed on the ECS, check the driver version. Before installing a new driver version, uninstall the original Tesla driver to prevent an installation failure due to driver conflicts.

Installation process:

-  `Obtaining a Tesla Driver and CUDA Toolkit <instances/(optional)_installing_a_driver_and_toolkit/obtaining_a_tesla_driver_and_cuda_toolkit>`__
-  Installing a Tesla Driver

   -  `Installing a Tesla Driver on a Linux ECS <#EN-US_TOPIC_0149470468__section1728514576397>`__
   -  `Installing a Tesla Driver on a Windows ECS <#EN-US_TOPIC_0149470468__section244363219171>`__

-  Installing a CUDA Toolkit

   -  `Installing the CUDA Toolkit on a Linux ECS <#EN-US_TOPIC_0149470468__section1034245773916>`__
   -  `Installing the CUDA Toolkit on a Windows ECS <#EN-US_TOPIC_0149470468__section0337133719497>`__

Installing a Tesla Driver on a Linux ECS
----------------------------------------

The following uses Ubuntu 16.04 64bit as an example to describe how to install the Tesla driver matching CUDA 10.1 on a GPU-accelerated ECS.

|image2|

The Linux kernel version is compatible with the driver version. If installing the driver failed, check the driver installation log, which is generally stored in **/var/log/nvidia-installer.log**. If the log shows that the failure was caused by a driver compilation error, for example, the **get_user_pages** parameter setting is incorrect, the kernel version is incompatible with the driver version. In such a case, select the desired kernel version and driver version and reinstall them. It is recommended that the release time of the kernel version and driver version be the same.

#. Log in to the ECS.

#. Update the system software based on the OS.

   -  Ubuntu

      Update the software installation source: **apt-get -y update**

      Install necessary programs: **apt-get install gcc g++ make**

   -  CentOS

      Update the software installation source: **yum -y update --exclude=kernel\* --exclude=centos-release\* --exclude=initscripts\***

      Install the desired program: **yum install -y kernel-devel-`uname -r\` gcc gcc-c++**

#. Download the NVIDIA driver package.

   Select a driver version at `NVIDIA Driver Downloads <https://www.nvidia.com/Download/index.aspx?lang=en-us>`__ based on the ECS type. Click **SEARCH**.

   | **Figure 1** Selecting a NVIDIA driver version
   | |image3|

#. Select a driver version as required. The following uses Tesla 418.67 as an example.\ **Figure 2** Selecting a driver version
   |image4|

#. Click the driver to be downloaded. On the **TESLA DRIVER FOR LINUX X64** page that is displayed, click **DOWNLOAD**.

#. Copy the download link.\ **Figure 3** Copying the download link
   |image5|

#. Run the following command on the ECS to download the driver:

   **wget** *Copied link*

   For example, **wget http://us.download.nvidia.com/tesla/418.67/NVIDIA-Linux-x86_64-418.67.run**

   | **Figure 4** Obtaining the installation package
   | |image6|

#. Run the following command to install the driver:

   **sh NVIDIA-Linux-x86_64-418.67.run**

#. (Optional) If the following information is displayed after the command for installing the driver is executed, disable the Nouveau driver.\ **Figure 5** Disabling the Nouveau driver
   |image7|

   a. Run the following command to check whether the Nouveau driver has been installed:

      **lsmod \| grep nouveau**

      -  If the command output contains information about the Nouveau driver, the Nouveau driver has been installed and must be disabled. Then, go to step `9.b <#EN-US_TOPIC_0149470468__li073251517124>`__.
      -  If the command output does not contain information about the Nouveau driver, the Nouveau driver has been disabled. Then, go to step `9.d <#EN-US_TOPIC_0149470468__li9819105753916>`__.

   b. Edit the **blacklist.conf** file.

      If the **/etc/modprobe.d/blacklist.conf** file is unavailable, create it.

      **vi /etc/modprobe.d/blacklist.conf**

      Add the following statement to the end of the file:

      .. code::

         blacklist nouveau
         options nouveau modeset=0

   c. Run the following command to back up and create an initramfs application:

      -  Ubuntu

         **sudo update-initramfs -u**

      -  CentOS:

         **mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r).img.bak**

         **dracut -v /boot/initramfs-$(uname -r).img $(uname -r)**

   d. Restart the ECS:

      **reboot**

#. Select **OK** for three consecutive times as prompted to complete the driver installation.\ **Figure 6** Completing the NVIDIA driver installation
   |image8|

#. Run the following command to set systemd:

   **systemctl set-default multi-user.target**

#. Run the **reboot** command to restart the ECS.

#. Log in to the ECS and run the **nvidia-smi** command. If the command output contains the installed driver version, the driver has been installed.\ **Figure 7** Viewing the NVIDIA driver version
   |image9|

Installing a Tesla Driver on a Windows ECS
------------------------------------------

The following uses Windows Server 2016 Standard 64bit as an example to describe how to install a Tesla driver on a GPU-accelerated ECS.

#. Log in to the ECS.

#. Download the NVIDIA driver package.

   Select a driver version at `NVIDIA Driver Downloads <https://www.nvidia.com/Download/index.aspx?lang=en-us>`__ based on the ECS type.

   | **Figure 8** Selecting a driver type (Windows)
   | |image10|

#. Select a driver version as required. The following uses Tesla 425.25 as an example.\ **Figure 9** Selecting a driver version (Windows)
   |image11|

#. Click the driver to be downloaded. On the **TESLA DRIVER FOR WINDOWS** page that is displayed, click **DOWNLOAD**.

#. Click **Agree & Download** to download the installation package.\ **Figure 10** Downloading the driver installation package
   |image12|

#. Double-click the driver and click **Run**.\ **Figure 11** Running the NVIDIA driver installation program
   |image13|

#. Select an installation path and click **OK**.\ **Figure 12** Selecting an installation path
   |image14|

#. Install the NVIDIA program as prompted.\ **Figure 13** Completing the driver installation
   |image15|

#. Restart the ECS.

#. Check whether the NVIDIA driver has been installed.

   a. Switch to **Device Manager** and click **Display adapters**.\ **Figure 14** Display adapters
      |image16|

   b. Open the **cmd** window on the ECS and run the following commands:

      **cd C:\Program Files\NVIDIA Corporation\NVSMI**

      **nvidia-smi**

      If the command output contains the installed driver version, the driver has been installed.

      | **Figure 15** Viewing the NVIDIA driver version
      | |image17|

Installing the CUDA Toolkit on a Linux ECS
------------------------------------------

The following uses Ubuntu 16.04 64bit as an example to describe how to install the CUDA 10.1 toolkit on a GPU-accelerated ECS.

#. Log in to the ECS.
#. Update the system software based on the OS.

   -  Ubuntu

      Update the software installation source: **apt-get -y update**

      Install necessary programs: **apt-get install gcc g++ make**

   -  CentOS

      Update the software installation source: **yum -y update --exclude=kernel\* --exclude=centos-release\* --exclude=initscripts\***

      Install the desired program: **yum install -y kernel-devel-`uname -r\` gcc gcc-c++**

#. On the CUDA download page, set parameters according to the information shown in `Obtaining a Tesla Driver and CUDA Toolkit <instances/(optional)_installing_a_driver_and_toolkit/obtaining_a_tesla_driver_and_cuda_toolkit>`__.\ **Figure 16** Selecting a CUDA version
   |image18|
#. Find the link for downloading CUDA 10.1 and copy the link.\ **Figure 17** Copying the link for downloading CUDA
   |image19|

5. Run the following command on the ECS to download CUDA:

   **wget** *Copied link*

   For example, **wget https://developer.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda_10.1.105_418.39_linux.run**

   | **Figure 18** Downloading CUDA
   | |image20|

6.  Install CUDA.Follow the instructions provided on the official NVIDIA website.\ **Figure 19** Installing CUDA
    |image21|

7.  Run the following command to install CUDA:

    **sh cuda_10.1.243_418.87.00_linux.run**

8.  Select **accept** on the installation page and press **Enter**.\ **Figure 20** Installing CUDA_1
    |image22|

9.  Select **Install** and press **Enter** to start the installation.\ **Figure 21** Installing CUDA_2
    |image23|
    **Figure 22** Completing the installation
    |image24|

10. Run the following command to switch to **/usr/local/cuda-10.1/samples/1_Utilities/deviceQuery**:

    **cd /usr/local/cuda-10.1/samples/1_Utilities/deviceQuery**

11. Run the **make** command to automatically compile the deviceQuery program.

12. Run the following command to check whether CUDA has been installed:

    **./deviceQuery**

    If the command output contains the CUDA version, CUDA has been installed.

    | **Figure 23** deviceQuery common output
    | |image25|

13. Check the CUDA version.

    **/usr/local/cuda/bin/nvcc -V**

    | **Figure 24** Checking the CUDA version
    | |image26|

14. Run the following command to enable the persistent mode:

    **sudo nvidia-smi -pm 1**

    Enabling the persistent mode optimizes the GPU performance on Linux ECSs.

Installing the CUDA Toolkit on a Windows ECS
--------------------------------------------

The following uses Windows Server 2016 Standard 64bit as an example to describe how to install the CUDA 10.1 toolkit on a GPU-accelerated ECS.

#. Log in to the ECS.
#. On the CUDA download page, set parameters according to the information shown in `Downloading a CUDA Toolkit <instances/(optional)_installing_a_driver_and_toolkit/obtaining_a_tesla_driver_and_cuda_toolkit#EN-US_TOPIC_0213874991__section10203125783920>`__.\ **Figure 25** Selecting a CUDA version
   |image27|
#. Find the link for downloading CUDA 10.1.\ **Figure 26** Finding the link for downloading CUDA
   |image28|
#. Click **Download** to download the CUDA toolkit.
#. Double-click the installation file and click **Run** to install the CUDA toolkit.\ **Figure 27** Installing CUDA
   |image29|
#. On the **CUDA Setup Package** page, select an installation path and click **OK**.\ **Figure 28** Selecting an installation path
   |image30|
#. Install the CUDA toolkit as prompted.\ **Figure 29** Completing the installation
   |image31|

8. Check whether CUDA has been installed

   Open the **cmd** window and run the following command:

   **nvcc -V**

   If the command output contains the CUDA version, CUDA has been installed.

   | **Figure 30** Successful installation
   | |image32|


.. |image1| image:: /_static/images/note_3.0-en-us.png
.. |image2| image:: /_static/images/note_3.0-en-us.png
.. |image3| image:: /_static/images/en-us_image_0234354896.png
   :class: imgResize

.. |image4| image:: /_static/images/en-us_image_0234354931.png
   :class: imgResize

.. |image5| image:: /_static/images/en-us_image_0234355284.png
   :class: imgResize

.. |image6| image:: /_static/images/en-us_image_0234355299.png
   :class: imgResize

.. |image7| image:: /_static/images/en-us_image_0250287387.png
   :class: imgResize

.. |image8| image:: /_static/images/en-us_image_0250287611.png
   :class: imgResize

.. |image9| image:: /_static/images/en-us_image_0234355305.png
   :class: imgResize

.. |image10| image:: /_static/images/en-us_image_0234356929.png
   :class: imgResize

.. |image11| image:: /_static/images/en-us_image_0234356990.png
   :class: imgResize

.. |image12| image:: /_static/images/en-us_image_0234357031.png
   :class: imgResize

.. |image13| image:: /_static/images/en-us_image_0234357053.png
   :class: imgResize

.. |image14| image:: /_static/images/en-us_image_0234357336.png
   :class: imgResize

.. |image15| image:: /_static/images/en-us_image_0234357355.png
   :class: imgResize

.. |image16| image:: /_static/images/en-us_image_0234357385.png
   :class: imgResize

.. |image17| image:: /_static/images/en-us_image_0234357365.png
   :class: imgResize

.. |image18| image:: /_static/images/en-us_image_0250288087.png
   :class: imgResize

.. |image19| image:: /_static/images/en-us_image_0250288474.png
   :class: imgResize

.. |image20| image:: /_static/images/en-us_image_0234358619.png
   :class: imgResize

.. |image21| image:: /_static/images/en-us_image_0250288371.png
   :class: imgResize

.. |image22| image:: /_static/images/en-us_image_0234358634.png
   :class: imgResize

.. |image23| image:: /_static/images/en-us_image_0234358642.png
   :class: imgResize

.. |image24| image:: /_static/images/en-us_image_0234358704.png
   :class: imgResize

.. |image25| image:: /_static/images/en-us_image_0234358719.png
   :class: imgResize

.. |image26| image:: /_static/images/en-us_image_0234358804.png
   :class: imgResize

.. |image27| image:: /_static/images/en-us_image_0250288895.png
   :class: imgResize

.. |image28| image:: /_static/images/en-us_image_0250289123.png
   :class: imgResize

.. |image29| image:: /_static/images/en-us_image_0234360248.png

.. |image30| image:: /_static/images/en-us_image_0234360274.png
   :class: imgResize

.. |image31| image:: /_static/images/en-us_image_0234360255.png
   :class: imgResize

.. |image32| image:: /_static/images/en-us_image_0234360293.png

