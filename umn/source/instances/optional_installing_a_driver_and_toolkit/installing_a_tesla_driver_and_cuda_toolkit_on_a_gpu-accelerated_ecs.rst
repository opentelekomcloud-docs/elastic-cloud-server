.. _en-us_topic_0149470468:

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

.. note::

   -  Download the CUDA toolkit from the official NVIDIA website and install it. A Tesla driver matching the CUDA version will be automatically installed then. However, if there are specific requirements or dependencies on the Tesla driver version, download the matching Tesla driver from the official NVIDIA website first and then install the driver before installing the CUDA toolkit.
   -  If a Tesla driver has been installed on the ECS, check the driver version. Before installing a new driver version, uninstall the original Tesla driver to prevent an installation failure due to driver conflicts.

Installation process:

-  :ref:`Obtaining a Tesla Driver and CUDA Toolkit <en-us_topic_0213874991>`
-  Installing a Tesla Driver

   -  :ref:`Installing a Tesla Driver on a Linux ECS <en-us_topic_0149470468__section1728514576397>`
   -  :ref:`Installing a Tesla Driver on a Windows ECS <en-us_topic_0149470468__section244363219171>`

-  Installing a CUDA Toolkit

   -  :ref:`Installing the CUDA Toolkit on a Linux ECS <en-us_topic_0149470468__section1034245773916>`
   -  :ref:`Installing the CUDA Toolkit on a Windows ECS <en-us_topic_0149470468__section0337133719497>`

.. _en-us_topic_0149470468__section1728514576397:

Installing a Tesla Driver on a Linux ECS
----------------------------------------

The following uses Ubuntu 16.04 64bit as an example to describe how to install the Tesla driver matching CUDA 10.1 on a GPU-accelerated ECS.

.. note::

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

   .. _en-us_topic_0149470468__fig545554125711:

   .. figure:: /_static/images/en-us_image_0234354896.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 1** Selecting a NVIDIA driver version

#. Select a driver version as required. The following uses Tesla 418.67 as an example.

   .. _en-us_topic_0149470468__fig52351103310:

   .. figure:: /_static/images/en-us_image_0234354931.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 2** Selecting a driver version

#. Click the driver to be downloaded. On the **TESLA DRIVER FOR LINUX X64** page that is displayed, click **DOWNLOAD**.

#. Copy the download link.

   .. _en-us_topic_0149470468__fig123801538205720:

   .. figure:: /_static/images/en-us_image_0234355284.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 3** Copying the download link

#. Run the following command on the ECS to download the driver:

   **wget** *Copied link*

   For example, **wget http://us.download.nvidia.com/tesla/418.67/NVIDIA-Linux-x86_64-418.67.run**

   .. _en-us_topic_0149470468__fig187219205141:

   .. figure:: /_static/images/en-us_image_0234355299.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 4** Obtaining the installation package

#. Run the following command to install the driver:

   **sh NVIDIA-Linux-x86_64-418.67.run**

#. (Optional) If the following information is displayed after the command for installing the driver is executed, disable the Nouveau driver.

   .. _en-us_topic_0149470468__fig2682182345814:

   .. figure:: /_static/images/en-us_image_0250287387.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 5** Disabling the Nouveau driver

   a. Run the following command to check whether the Nouveau driver has been installed:

      **lsmod \| grep nouveau**

      -  If the command output contains information about the Nouveau driver, the Nouveau driver has been installed and must be disabled. Then, go to step :ref:`9.b <en-us_topic_0149470468__li073251517124>`.
      -  If the command output does not contain information about the Nouveau driver, the Nouveau driver has been disabled. Then, go to step :ref:`9.d <en-us_topic_0149470468__li9819105753916>`.

   b. .. _en-us_topic_0149470468__li073251517124:

      Edit the **blacklist.conf** file.

      If the **/etc/modprobe.d/blacklist.conf** file is unavailable, create it.

      **vi /etc/modprobe.d/blacklist.conf**

      Add the following statement to the end of the file:

      .. code-block::

         blacklist nouveau
         options nouveau modeset=0

   c. Run the following command to back up and create an initramfs application:

      -  Ubuntu

         **sudo update-initramfs -u**

      -  CentOS:

         **mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r).img.bak**

         **dracut -v /boot/initramfs-$(uname -r).img $(uname -r)**

   d. .. _en-us_topic_0149470468__li9819105753916:

      Restart the ECS:

      **reboot**

#. Select **OK** for three consecutive times as prompted to complete the driver installation.

   .. _en-us_topic_0149470468__fig1643713142594:

   .. figure:: /_static/images/en-us_image_0250287611.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 6** Completing the NVIDIA driver installation

#. Run the following command to set systemd:

   **systemctl set-default multi-user.target**

#. Run the **reboot** command to restart the ECS.

#. Log in to the ECS and run the **nvidia-smi** command. If the command output contains the installed driver version, the driver has been installed.

   .. _en-us_topic_0149470468__fig61971535809:

   .. figure:: /_static/images/en-us_image_0234355305.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 7** Viewing the NVIDIA driver version

.. _en-us_topic_0149470468__section244363219171:

Installing a Tesla Driver on a Windows ECS
------------------------------------------

The following uses Windows Server 2016 Standard 64bit as an example to describe how to install a Tesla driver on a GPU-accelerated ECS.

#. Log in to the ECS.

#. Download the NVIDIA driver package.

   Select a driver version at `NVIDIA Driver Downloads <https://www.nvidia.com/Download/index.aspx?lang=en-us>`__ based on the ECS type.

   .. _en-us_topic_0149470468__fig62897581106:

   .. figure:: /_static/images/en-us_image_0234356929.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 8** Selecting a driver type (Windows)

#. Select a driver version as required. The following uses Tesla 425.25 as an example.

   .. _en-us_topic_0149470468__fig5291626204819:

   .. figure:: /_static/images/en-us_image_0234356990.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 9** Selecting a driver version (Windows)

#. Click the driver to be downloaded. On the **TESLA DRIVER FOR WINDOWS** page that is displayed, click **DOWNLOAD**.

#. Click **Agree & Download** to download the installation package.

   .. _en-us_topic_0149470468__fig37451434818:

   .. figure:: /_static/images/en-us_image_0234357031.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 10** Downloading the driver installation package

#. Double-click the driver and click **Run**.

   .. _en-us_topic_0149470468__fig177611624821:

   .. figure:: /_static/images/en-us_image_0234357053.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 11** Running the NVIDIA driver installation program

#. Select an installation path and click **OK**.

   .. _en-us_topic_0149470468__fig1378440121:

   .. figure:: /_static/images/en-us_image_0234357336.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 12** Selecting an installation path

#. Install the NVIDIA program as prompted.

   .. _en-us_topic_0149470468__fig46181053128:

   .. figure:: /_static/images/en-us_image_0234357355.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 13** Completing the driver installation

#. Restart the ECS.

#. Check whether the NVIDIA driver has been installed.

   a. Switch to **Device Manager** and click **Display adapters**.

      .. _en-us_topic_0149470468__fig8540781030:

      .. figure:: /_static/images/en-us_image_0234357385.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 14** Display adapters

   b. Open the **cmd** window on the ECS and run the following commands:

      **cd C:\Program Files\NVIDIA Corporation\NVSMI**

      **nvidia-smi**

      If the command output contains the installed driver version, the driver has been installed.

      .. _en-us_topic_0149470468__fig125251621439:

      .. figure:: /_static/images/en-us_image_0234357365.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 15** Viewing the NVIDIA driver version

.. _en-us_topic_0149470468__section1034245773916:

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

#. On the CUDA download page, set parameters according to the information shown in :ref:`Obtaining a Tesla Driver and CUDA Toolkit <en-us_topic_0213874991>`.

   .. _en-us_topic_0149470468__fig1930101643513:

   .. figure:: /_static/images/en-us_image_0250288087.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 16** Selecting a CUDA version

#. Find the link for downloading CUDA 10.1 and copy the link.

   .. _en-us_topic_0149470468__fig970482862918:

   .. figure:: /_static/images/en-us_image_0250288474.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 17** Copying the link for downloading CUDA

5. Run the following command on the ECS to download CUDA:

   **wget** *Copied link*

   For example, **wget https://developer.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda_10.1.105_418.39_linux.run**

   .. _en-us_topic_0149470468__fig8354143184612:

   .. figure:: /_static/images/en-us_image_0234358619.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 18** Downloading CUDA

6.  Install CUDA.

    Follow the instructions provided on the official NVIDIA website.

    .. _en-us_topic_0149470468__fig11827757103913:

    .. figure:: /_static/images/en-us_image_0250288371.png
       :alt: Click to enlarge
       :figclass: imgResize
    

       **Figure 19** Installing CUDA

7.  Run the following command to install CUDA:

    **sh cuda_10.1.243_418.87.00_linux.run**

8.  Select **accept** on the installation page and press **Enter**.

    .. _en-us_topic_0149470468__fig514958145414:

    .. figure:: /_static/images/en-us_image_0234358634.png
       :alt: Click to enlarge
       :figclass: imgResize
    

       **Figure 20** Installing CUDA_1

9.  Select **Install** and press **Enter** to start the installation.

    .. _en-us_topic_0149470468__fig20943181255411:

    .. figure:: /_static/images/en-us_image_0234358642.png
       :alt: Click to enlarge
       :figclass: imgResize
    

       **Figure 21** Installing CUDA_2

    .. _en-us_topic_0149470468__fig148915619526:

    .. figure:: /_static/images/en-us_image_0234358704.png
       :alt: Click to enlarge
       :figclass: imgResize
    

       **Figure 22** Completing the installation

10. Run the following command to switch to **/usr/local/cuda-10.1/samples/1_Utilities/deviceQuery**:

    **cd /usr/local/cuda-10.1/samples/1_Utilities/deviceQuery**

11. Run the **make** command to automatically compile the deviceQuery program.

12. Run the following command to check whether CUDA has been installed:

    **./deviceQuery**

    If the command output contains the CUDA version, CUDA has been installed.

    .. _en-us_topic_0149470468__fig1282815711392:

    .. figure:: /_static/images/en-us_image_0234358719.png
       :alt: Click to enlarge
       :figclass: imgResize
    

       **Figure 23** deviceQuery common output

13. Check the CUDA version.

    **/usr/local/cuda/bin/nvcc -V**

    .. _en-us_topic_0149470468__fig18749997817:

    .. figure:: /_static/images/en-us_image_0234358804.png
       :alt: Click to enlarge
       :figclass: imgResize
    

       **Figure 24** Checking the CUDA version

14. Run the following command to enable the persistent mode:

    **sudo nvidia-smi -pm 1**

    Enabling the persistent mode optimizes the GPU performance on Linux ECSs.

.. _en-us_topic_0149470468__section0337133719497:

Installing the CUDA Toolkit on a Windows ECS
--------------------------------------------

The following uses Windows Server 2016 Standard 64bit as an example to describe how to install the CUDA 10.1 toolkit on a GPU-accelerated ECS.

#. Log in to the ECS.

#. On the CUDA download page, set parameters according to the information shown in :ref:`Downloading a CUDA Toolkit <en-us_topic_0213874991__section10203125783920>`.

   .. _en-us_topic_0149470468__fig17127316719:

   .. figure:: /_static/images/en-us_image_0250288895.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 25** Selecting a CUDA version

#. Find the link for downloading CUDA 10.1.

   .. _en-us_topic_0149470468__fig22798411673:

   .. figure:: /_static/images/en-us_image_0250289123.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 26** Finding the link for downloading CUDA

#. Click **Download** to download the CUDA toolkit.

#. Double-click the installation file and click **Run** to install the CUDA toolkit.

   .. _en-us_topic_0149470468__fig696324171118:

   .. figure:: /_static/images/en-us_image_0234360248.png
      :alt: **Figure 27** Installing CUDA
   

      **Figure 27** Installing CUDA

#. On the **CUDA Setup Package** page, select an installation path and click **OK**.

   .. _en-us_topic_0149470468__fig18644103851215:

   .. figure:: /_static/images/en-us_image_0234360274.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 28** Selecting an installation path

#. Install the CUDA toolkit as prompted.

   .. _en-us_topic_0149470468__fig2266175711165:

   .. figure:: /_static/images/en-us_image_0234360255.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 29** Completing the installation

8. Check whether CUDA has been installed

   Open the **cmd** window and run the following command:

   **nvcc -V**

   If the command output contains the CUDA version, CUDA has been installed.

   .. _en-us_topic_0149470468__fig6475101453:

   .. figure:: /_static/images/en-us_image_0234360293.png
      :alt: **Figure 30** Successful installation
   

      **Figure 30** Successful installation
