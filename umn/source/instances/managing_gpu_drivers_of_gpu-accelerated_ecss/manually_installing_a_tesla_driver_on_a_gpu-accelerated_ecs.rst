:original_name: en-us_topic_0149470468.html

.. _en-us_topic_0149470468:

Manually Installing a Tesla Driver on a GPU-accelerated ECS
===========================================================

Scenarios
---------

To enable compute acceleration on a GPU-accelerated ECS, you must install the Tesla driver and CUDA Toolkit.

-  A computing-accelerated (P series) ECS created using a Windows public image comes with a specific version of the Tesla driver preinstalled by default.
-  A computing-accelerated (P series) ECS created using a Linux public image does not have a specific version of the Tesla driver preinstalled by default. You must install the Tesla driver to enable compute acceleration.
-  If a GPU-accelerated ECS is created using a private image, you must install the Tesla driver and CUDA Toolkit to enable compute acceleration.

This section describes how to install the Tesla driver and CUDA Toolkit on a GPU-accelerated ECS manually.

Constraints
-----------

-  The GPU driver can be installed only on GPU-accelerated ECSs. For details about GPU-accelerated ECSs and their application scenarios, see :ref:`GPU-accelerated ECSs <en-us_topic_0097289624>`.

-  An EIP must be bound to the ECS.

-  The Tesla driver and CUDA Toolkit have not been installed on the ECS.

   .. note::

      -  When you download the CUDA Toolkit from the NVIDIA official website, a Tesla driver that matches the CUDA version is usually installed automatically, eliminating the need to install the driver separately. However, if there are specific requirements or dependencies on the Tesla driver version, download the matching Tesla driver from the official NVIDIA website and install the driver first before installing the CUDA Toolkit.
      -  If a Tesla driver has been installed on the ECS, check whether the driver version is available. If you need to install a new driver version, uninstall the old Tesla driver first to prevent installation failures caused by driver conflicts.

-  :ref:`Table 1 <en-us_topic_0149470468__table394113539174>` lists the relationship between ECS series and Tesla drivers.

   .. _en-us_topic_0149470468__table394113539174:

   .. table:: **Table 1** ECS series and corresponding Tesla drivers

      ========== ============ ============== =======
      ECS Series Product Type Product Series Product
      ========== ============ ============== =======
      P5e        Tesla        H-Series       H100
      P5s        Tesla        H-Series       H100
      P3         Tesla        A-Series       A100
      P2s        Tesla        V-Series       V100
      P2v        Tesla        V-Series       V100
      Pi5e       Tesla        H-Series       L4
      Pi2        Tesla        T- Series      T4
      G7v        Tesla        A-Series       A40
      G7         Tesla        A-Series       A40
      G6         Tesla        T- Series      T4
      ========== ============ ============== =======

Installing the Tesla Driver and CUDA Toolkit on a Linux ECS
-----------------------------------------------------------

The following describes how to install the Tesla driver corresponding to CUDA 10.1 and install CUDA 10.1 using the .run package on a GPU ECS running Ubuntu 20.04 64-bit.

.. note::

   The Linux kernel version must match the driver version. If driver installation fails, check the driver installation log, which is generally stored in **/var/log/nvidia-installer.log**. If the log shows that the failure was caused by a driver compilation error, for example, the **get_user_pages** parameter setting is incorrect, the kernel version is incompatible with the driver version. In such a case, select the desired kernel version and driver version and reinstall them. It is recommended that the release time of the kernel version and driver version be the same.

**Installing the Tesla Driver**

#. Log in to the ECS.

#. Update the system software based on the OS.

   -  Ubuntu

      Update the software package repositories: **apt-get -y update**

      Install necessary programs: **apt-get install gcc g++ make**

   -  CentOS

      Update the software package repositories: **yum -y update --exclude=kernel\* --exclude=centos-release\* --exclude=initscripts\***

      Install necessary programs: **yum install -y kernel-devel-`uname -r\` gcc gcc-c++**

#. Download the NVIDIA driver package.

   Download a driver from `NVIDIA Drivers <https://www.nvidia.com/Download/index.aspx?lang=en-us>`__ based on the ECS series.


   .. figure:: /_static/images/en-us_image_0000002114600494.png
      :alt: **Figure 1** Manual driver search

      **Figure 1** Manual driver search

#. Select a driver version as required. The following uses Tesla 418.67 as an example.


   .. figure:: /_static/images/en-us_image_0000002150126353.png
      :alt: **Figure 2** Selecting a driver version

      **Figure 2** Selecting a driver version

#. Click **View** in the row containing the driver to be downloaded.

#. Right-click **Download** and copy the download URL.

#. Run the following command on the ECS to download the driver:

   **wget** {*URL-for-downloading-the-NVIDIA-driver*}

   For example, **wget http://us.download.nvidia.com/tesla/418.67/NVIDIA-Linux-x86_64-418.67.run**


   .. figure:: /_static/images/en-us_image_0234355299.png
      :alt: **Figure 3** Obtaining the installation package

      **Figure 3** Obtaining the installation package

   .. note::

      You can run the **wget {URL for downloading the NVIDIA driver}** command to download the NVIDIA driver.

      If the error message "403: Forbidden" is displayed after the command is executed, run the following command to download the driver:

      **wget -U "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/96.0.4664.110 Safari/537.36" --referer="https://www.nvidia.com/" {**\ **URL for downloading the NVIDIA driver**\ **}**

#. Run the following command to install the driver:

   **sh NVIDIA-Linux-x86_64-418.67.run**

#. (Optional) If the following information is displayed after the command for installing the driver is executed, disable the Nouveau driver.


   .. figure:: /_static/images/en-us_image_0250287387.png
      :alt: **Figure 4** Disabling the Nouveau driver

      **Figure 4** Disabling the Nouveau driver

   a. Run the following command to check whether the Nouveau driver has been installed:

      **lsmod \| grep nouveau**

      -  If the command output contains information about the Nouveau driver, the Nouveau driver has been installed. In this case, it must be disabled. Then, go to :ref:`9.b <en-us_topic_0149470468__li5326124474>`.
      -  If the command output does not contain information about the Nouveau driver, the Nouveau driver has been disabled. Then, go to :ref:`10 <en-us_topic_0149470468__li63268416718>`.

   b. .. _en-us_topic_0149470468__li5326124474:

      Edit the **blacklist.conf** file.

      If the **/etc/modprobe.d/blacklist.conf** file was not found, create one.

      **vi /etc/modprobe.d/blacklist.conf**

      Add the following content to the end of the file:

      .. code-block::

         blacklist nouveau
         options nouveau modeset=0

   c. Back up the current initramfs and generate a new one.

      -  Ubuntu

         **sudo update-initramfs -u**

      -  CentOS

         **mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r).img.bak**

         **dracut -v /boot/initramfs-$(uname -r).img $(uname -r)**

   d. Run the following command to restart the ECS:

      **reboot**

#. .. _en-us_topic_0149470468__li63268416718:

   Select **OK** for three consecutive times as prompted to complete the driver installation.


   .. figure:: /_static/images/en-us_image_0250287611.png
      :alt: **Figure 5** Completing the NVIDIA driver installation

      **Figure 5** Completing the NVIDIA driver installation

#. Run the following command to set systemd:

   **systemctl set-default multi-user.target**

#. Run the **reboot** command to restart the ECS.

#. Log in to the ECS and run the **nvidia-smi** command. If the command output contains the installed driver version, the driver has been installed.


   .. figure:: /_static/images/en-us_image_0234355305.png
      :alt: **Figure 6** Viewing the NVIDIA driver version

      **Figure 6** Viewing the NVIDIA driver version

**Installing the CUDA Toolkit**

#. Log in to the ECS.

#. Update the system software based on the OS.

   -  Ubuntu

      Update the software installation source: **apt-get -y update**

      Install necessary programs: **apt-get install gcc g++ make**

   -  CentOS

      Update the software installation source: **yum -y update --exclude=kernel\* --exclude=centos-release\* --exclude=initscripts\***

      Install the desired program: **yum install -y kernel-devel-`uname -r\` gcc gcc-c++**

#. On the CUDA download page, set parameters based on the information provided in :ref:`Obtaining a Tesla Driver and CUDA Toolkit <en-us_topic_0213874991>`.


   .. figure:: /_static/images/en-us_image_0000002606704981.png
      :alt: **Figure 7** Selecting a CUDA version

      **Figure 7** Selecting a CUDA version

#. View the URL for downloading CUDA 10.1 corresponding to Ubuntu 20.04 64-bit and copy the URL.

5. Run the following command on the ECS to download CUDA:

   **wget** *copied-URL*

   For example, **wget https://developer.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda_10.1.105_418.39_linux.run**


   .. figure:: /_static/images/en-us_image_0000002575984996.png
      :alt: **Figure 8** Downloading CUDA

      **Figure 8** Downloading CUDA

6.  Install CUDA.

    Follow the instructions provided on the official NVIDIA website.

7.  Run the following command to install CUDA:

    **sh cuda_10.1.243_418.87.00_linux.run**

8.  Select **accept** on the installation page and press **Enter**.


    .. figure:: /_static/images/en-us_image_0000002606704983.png
       :alt: **Figure 9** Installing CUDA_1

       **Figure 9** Installing CUDA_1

9.  Select **Install** and press **Enter** to start the installation.


    .. figure:: /_static/images/en-us_image_0000002576264970.png
       :alt: **Figure 10** Installing CUDA_2

       **Figure 10** Installing CUDA_2


    .. figure:: /_static/images/en-us_image_0000002575984998.png
       :alt: **Figure 11** Completing the installation

       **Figure 11** Completing the installation

10. (Optional) Check whether CUDA has been installed.

    If the CUDA version is 11.5 or earlier, perform the following operations to check whether CUDA has been installed. If the CUDA version is 11.6 or later, skip this step.

    a. Run the following command to switch to **/usr/local/cuda-10.1/samples/1_Utilities/deviceQuery**:

       **cd /usr/local/cuda-10.1/samples/1_Utilities/deviceQuery**

    b. Run the **make** command to automatically compile the deviceQuery program.

    c. Run the following command to check whether CUDA has been installed:

       **./deviceQuery**

       If the command output contains the CUDA version, CUDA has been installed.


       .. figure:: /_static/images/en-us_image_0000002606465001.png
          :alt: **Figure 12** deviceQuery common output

          **Figure 12** deviceQuery common output

11. Check the CUDA version.

    **/usr/local/cuda/bin/nvcc -V**


    .. figure:: /_static/images/en-us_image_0000002606704985.png
       :alt: **Figure 13** Checking the CUDA version

       **Figure 13** Checking the CUDA version

12. Run the following command to enable the persistent mode:

    **sudo nvidia-smi -pm 1**

    Enabling the persistent mode optimizes the GPU performance on Linux ECSs.

Installing the Tesla Driver and CUDA Toolkit on a Windows ECS
-------------------------------------------------------------

The following describes how to install the Tesla driver and CUDA 10.1 on a GPU ECS running Windows Server 2016 Standard 64-bit.

**Installing the Tesla Driver**

#. Log in to the ECS.

#. Download the NVIDIA driver package.

   Select a driver version at `NVIDIA Drivers <https://www.nvidia.com/Download/index.aspx?lang=en-us>`__ based on the ECS series.


   .. figure:: /_static/images/en-us_image_0000002114450902.png
      :alt: **Figure 14** Selecting a driver type (Windows)

      **Figure 14** Selecting a driver type (Windows)

#. Select a driver version as required. The following uses Tesla 425.25 as an example.


   .. figure:: /_static/images/en-us_image_0000002114454596.png
      :alt: **Figure 15** Selecting a driver version (Windows)

      **Figure 15** Selecting a driver version (Windows)

#. Click **View** in the row containing the driver to be downloaded.

#. Click **Download** to download the installation package.

#. Double-click the driver and click **Run**.


   .. figure:: /_static/images/en-us_image_0234357053.png
      :alt: **Figure 16** Running the NVIDIA driver installation program

      **Figure 16** Running the NVIDIA driver installation program

#. Select an installation path and click **OK**.


   .. figure:: /_static/images/en-us_image_0234357336.png
      :alt: **Figure 17** Selecting an installation path

      **Figure 17** Selecting an installation path

#. Install the NVIDIA program as prompted.


   .. figure:: /_static/images/en-us_image_0234357355.png
      :alt: **Figure 18** Completing the driver installation

      **Figure 18** Completing the driver installation

#. Restart the ECS.

#. Check whether the NVIDIA driver has been installed.

   a. Switch to **Device Manager** and click **Display adapters**.


      .. figure:: /_static/images/en-us_image_0234357385.png
         :alt: **Figure 19** Display adapters

         **Figure 19** Display adapters

   b. Open the **cmd** window on the ECS and run the following commands:

      **cd C:\\Program Files\\NVIDIA Corporation\\NVSMI**

      **nvidia-smi**

      If the command output contains the installed driver version, the driver has been installed.


      .. figure:: /_static/images/en-us_image_0234357365.png
         :alt: **Figure 20** Viewing the NVIDIA driver version

         **Figure 20** Viewing the NVIDIA driver version

**Installing the CUDA Toolkit**

#. Log in to the ECS.

#. On the CUDA download page, set parameters based on the information provided in :ref:`Obtaining a Tesla Driver and CUDA Toolkit <en-us_topic_0213874991>`.


   .. figure:: /_static/images/en-us_image_0000002576264972.png
      :alt: **Figure 21** Selecting a CUDA version

      **Figure 21** Selecting a CUDA version

#. View the URL for downloading CUDA 10.1 corresponding to Windows Server 2016 Standard 64-bit.


   .. figure:: /_static/images/en-us_image_0000002575985000.png
      :alt: **Figure 22** URL for downloading CUDA

      **Figure 22** URL for downloading CUDA

#. Click **Download** to download the CUDA Toolkit.

#. Double-click the installation file and click **Run** to install the CUDA Toolkit.


   .. figure:: /_static/images/en-us_image_0000002606465003.png
      :alt: **Figure 23** Installing CUDA on a Windows ECS

      **Figure 23** Installing CUDA on a Windows ECS

#. On the **CUDA Setup Package** page, select an installation path and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002606704987.png
      :alt: **Figure 24** Selecting an installation path

      **Figure 24** Selecting an installation path

#. Follow the prompts to install the CUDA Toolkit.


   .. figure:: /_static/images/en-us_image_0000002576264974.png
      :alt: **Figure 25** CUDA installation completed

      **Figure 25** CUDA installation completed

8. Check whether CUDA has been installed.

   Open the **cmd** window and run the following command:

   **nvcc -V**

   If the command output contains the CUDA version, CUDA has been installed.


   .. figure:: /_static/images/en-us_image_0000002575985002.png
      :alt: **Figure 26** Successful CUDA installation

      **Figure 26** Successful CUDA installation
