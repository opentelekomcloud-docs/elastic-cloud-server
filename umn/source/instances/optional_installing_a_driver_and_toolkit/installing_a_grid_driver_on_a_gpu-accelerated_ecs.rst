:original_name: en-us_topic_0149610914.html

.. _en-us_topic_0149610914:

Installing a GRID Driver on a GPU-accelerated ECS
=================================================

Scenarios
---------

To use graphics acceleration, such as OpenGL, DirectX, or Vulkan, install a GRID driver and separately purchase and configure a GRID license. The GRID driver with a vDWS license also supports CUDA for both computing and graphics acceleration.

-  A graphics-accelerated (G series) ECS created using a Windows public image has had a GRID driver of a specified version installed by default, but the GRID license must be purchased and configured separately.
-  A graphics-accelerated (G series) ECS created using a Linux public image does not have a GRID driver installed by default. You are required to install a GRID driver and purchase and configure a GRID license separately.
-  If a GPU-accelerated ECS is created using a private image, install a GRID driver and separately purchase and configure a GRID license.

This section describes how to install a GRID driver, purchase or apply for a GRID license, and configure the license server.

Process of installing a GRID driver:

#. :ref:`Purchasing a GRID License <en-us_topic_0149610914__section1130184214229>`
#. :ref:`Downloading GRID Driver and Software License Packages <en-us_topic_0149610914__section91244318407>`
#. :ref:`Deploying and Configuring the License Server <en-us_topic_0149610914__section19229135113439>`
#. :ref:`Installing the GRID Driver and Configuring the License <en-us_topic_0149610914__section17545653184812>`

.. note::

   -  NVIDIA allows you to apply for a 90-day trial license.
   -  For details about GPU-accelerated ECSs with different specifications and application scenarios, see :ref:`GPU-accelerated ECSs <en-us_topic_0097289624>`.
   -  The screenshots in this section are for reference only.

.. _en-us_topic_0149610914__section1130184214229:

Purchasing a GRID License
-------------------------

-  Purchase a license.

   To obtain an official license, contact NVIDIA or their NVIDIA agent in your local country or region.

-  Apply for a trial license.

   Log in at the `official NVIDIA website <https://www.nvidia.com/object/nvidia-enterprise-account.html>`__ and enter desired information.

   For details about how to register for an account and apply for a trial license, see `official NVIDIA help page <https://nvid.nvidia.com/NvidiaUtilities/#/needHelp>`__.

   .. note::

      The method of using a trial license is the same as that of using an official license. You can use an official license to activate an account with a trial license to prevent repetitive registration. The trial license has a validity period of 90 days. After the trial license expires, it cannot be used anymore. Purchase an official license then.


   .. figure:: /_static/images/en-us_image_0178069404.png
      :alt: **Figure 1** Applying for a trial license

      **Figure 1** Applying for a trial license

.. _en-us_topic_0149610914__section91244318407:

Downloading GRID Driver and Software License Packages
-----------------------------------------------------

#. Obtain the driver installation package required for an OS. For details, see :ref:`Table 1 <en-us_topic_0149610914__table188851534175019>`.

   For more information about the GRID driver, see `NVIDIA vGPU Software Documentation <https://docs.nvidia.com/grid/index.html>`__.

   .. note::

      For a GPU passthrough ECS, select a GRID driver version as required.

      For a GPU virtualization ECS, select a driver version based on the following table.

   .. _en-us_topic_0149610914__table188851534175019:

   .. table:: **Table 1** GRID driver versions supported by GPU-accelerated ECSs

      ======== =============== ============================= ================
      ECS Type GPU Attachment  Driver Version                CPU Architecture
      ======== =============== ============================= ================
      G7       GPU passthrough Select a version as required. x86_64
      G6       GPU passthrough Select a version as required. x86_64
      P3       GPU passthrough Select a version as required. x86_64
      P2s      GPU passthrough Select a version as required. x86_64
      P2v      GPU passthrough Select a version as required. x86_64
      P2       GPU passthrough Select a version as required. x86_64
      P1       GPU passthrough Select a version as required. x86_64
      PI2      GPU passthrough Select a version as required. x86_64
      ======== =============== ============================= ================

#. After the registration, log in at the `official NVIDIA website <https://nvid.nvidia.com/dashboard/>`__ and enter the account.

#. Check whether NVIDIA is used for the first time.

   a. If yes, go to step :ref:`4 <en-us_topic_0149610914__li1859773663819>`.
   b. If no, go to step :ref:`6 <en-us_topic_0149610914__li0791101412396>`.

#. .. _en-us_topic_0149610914__li1859773663819:

   Obtain the Product Activation Key (PAK) from the email indicating successful registration with NVIDIA.


   .. figure:: /_static/images/en-us_image_0178334448.png
      :alt: **Figure 2** PAK

      **Figure 2** PAK

#. Enter the PAK obtained in step :ref:`4 <en-us_topic_0149610914__li1859773663819>` on the **Redeem Product Activation Keys** page and click **Redeem**.


   .. figure:: /_static/images/en-us_image_0178334449.png
      :alt: **Figure 3** Redeem Product Activation Keys

      **Figure 3** Redeem Product Activation Keys

#. .. _en-us_topic_0149610914__li0791101412396:

   Specify **Username** and **Password** and click **LOGIN**.


   .. figure:: /_static/images/en-us_image_0178334450.png
      :alt: **Figure 4** Logging in to the official NVIDIA website

      **Figure 4** Logging in to the official NVIDIA website

#. Log in at the official NVIDIA website as prompted and select **SOFTWARE DOWNLOADS**.


   .. figure:: /_static/images/en-us_image_0000001093447741.png
      :alt: **Figure 5** **SOFTWARE DOWNLOADS** page

      **Figure 5** **SOFTWARE DOWNLOADS** page

#. Download the GRID driver of the required version. For details, see :ref:`Table 1 <en-us_topic_0149610914__table188851534175019>`.

#. Decompress the GRID driver installation package and install the driver that matches your ECS OS.

#. .. _en-us_topic_0149610914__li1783092110416:

   On the **SOFTWARE DOWNLOADS** page, click **ADDITIONAL SOFTWARE** to download the license software package.


   .. figure:: /_static/images/en-us_image_0000001093667097.png
      :alt: **Figure 6** ADDITIONAL SOFTWARE

      **Figure 6** ADDITIONAL SOFTWARE

.. _en-us_topic_0149610914__section19229135113439:

Deploying and Configuring the License Server
--------------------------------------------

The following uses an ECS running CentOS 7.5 as an example to describe how to deploy and configure the license server on the ECS.

.. note::

   -  The target ECS must have at least 2 vCPUs and 4 GiB of memory.
   -  Ensure that the MAC address of the target ECS has been recorded.
   -  If the license server is used in the production environment, deploy it in high availability mode. For details, see `official NVIDIA documentation for license server high availability <https://docs.nvidia.com/grid/ls/2019.05/grid-license-server-user-guide/index.html#license-server-high-availability>`__.

#. Configure the network.

   -  If the license server is to be accessed using the VPC, ensure that the license server and the GPU-accelerated ECS with the GRID driver installed are in the same VPC subnet.
   -  If the license server is to be accessed using a public IP address, configure the security group to which license server belongs and add inbound rules for TCP 7070 and TCP 8080.

2. Install the license server.

   a. Run the following command to decompress the installation package. The **Installer.zip** in the command indicates the name of the software package obtained in :ref:`10 <en-us_topic_0149610914__li1783092110416>`.

      **unzip Installer.zip**

   b. Run the following command to assign execution permissions to the installer:

      **chmod +x setup.bin**

   c. Run the installer as user **root**:

      **sudo ./setup.bin -i console**

   d. In the Introduction section, press **Enter** to continue.

      |image1|

   e. In the License Agreement section, press **Enter** to turn to last pages and accept the license agreement.

      Enter **Y** and press **Enter**.

      |image2|

   f. In the Choose Install Folder section, press **Enter** to retain the default path for installing the License Server software.

   g. In the Choose Local Tomcat Server Path section, enter the Tomcat's local path in the "/var/lib/*Tomcat version*" format, for example, /var/lib/tomcat8.

   h. In the Choose Firewall Options section, confirm the port to be enabled in the firewall and press **Enter**.

      |image3|

   i. In the Pre-Installation Summary section, confirm the information and press **Enter** to start the installation.

      |image4|

   j. In the Install Complete section, press **Enter** to end the installation.

      |image5|

3. Obtain the license file.

   a. Log in to the `NVIDIA website <http://nvid.nvidia.com/dashboard/>`__ on a new tab and select **LICENSE SERVERS**.


      .. figure:: /_static/images/en-us_image_0000001093449637.png
         :alt: **Figure 7** LICENSE SERVERS

         **Figure 7** LICENSE SERVERS

   b. Click **CREATE SERVER**.

   c. On the displayed **Create License Server** page, configure parameters.


      .. figure:: /_static/images/en-us_image_0000001626671598.png
         :alt: **Figure 8** Create License Server

         **Figure 8** Create License Server

      .. table:: **Table 2** Parameters for creating a license server

         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                              |
         +===================================+==========================================================================================================================================================+
         | Server Name                       | License server name, which can be customized.                                                                                                            |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Description                       | License description information.                                                                                                                         |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
         | MAC Address                       | MAC address of the ECS where the license server is deployed.                                                                                             |
         |                                   |                                                                                                                                                          |
         |                                   | You can log in to the ECS and run **ipconfig -a** to query the MAC address.                                                                              |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Feature                           | Select a feature, enter the number of required licenses in the **Licenses** text box, and click **ADD**.                                                 |
         |                                   |                                                                                                                                                          |
         |                                   | In active/standby deployment, enter the name of the standby server in **Failover License Server** and enter the MAC address in **Failover MAC Address**. |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

   d. Click **CREATE LICENSE SERVER**.

   e. Download the license file.


      .. figure:: /_static/images/en-us_image_0000001093310123.png
         :alt: **Figure 9** Downloading the license file

         **Figure 9** Downloading the license file

4. In the web browser, access the homepage of the license server management page using the link configured during the installation.

   Default URL: http://*IP address of the EIP*:8080/licserver

5. In the navigation pane on the left, click **License Server** > **License Management**.

6. Select the .bin license file to be uploaded and click **Upload**.


   .. figure:: /_static/images/en-us_image_0178325096.png
      :alt: **Figure 10** Uploading a license file

      **Figure 10** Uploading a license file

.. _en-us_topic_0149610914__section17545653184812:

Installing the GRID Driver and Configuring the License
------------------------------------------------------

#. Install the GRID driver of a desired version, for example, on a GPU-accelerated Windows ECS.

   .. note::

      Microsoft remote login protocols do not support GPU 3D hardware acceleration. To use this function, install third-party desktop protocol-compliant software, such as VNC, PCoIP, or NICE DCV, and access the ECS through the client.

#. Open the NVIDIA control panel on the Windows control panel.

#. Enter the IP address and port number of the deployed license server in the level-1 license server, and then click **Apply**. If the message indicating that you have obtained a GRID license is displayed, the installation is successful. Additionally, the MAC address of the GPU-accelerated ECS with the GRID driver installed is displayed on the **Licensed Clients** page of the license server management console.


   .. figure:: /_static/images/en-us_image_0178370293.png
      :alt: **Figure 11** License server management console

      **Figure 11** License server management console

.. |image1| image:: /_static/images/en-us_image_0000001674064185.png
.. |image2| image:: /_static/images/en-us_image_0000001625786470.png
.. |image3| image:: /_static/images/en-us_image_0000001674067605.png
.. |image4| image:: /_static/images/en-us_image_0000001625473206.png
.. |image5| image:: /_static/images/en-us_image_0000001673953273.png
