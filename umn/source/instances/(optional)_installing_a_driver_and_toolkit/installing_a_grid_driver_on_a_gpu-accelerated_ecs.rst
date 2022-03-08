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

#. `Purchasing a GRID License <#EN-US_TOPIC_0149610914__section1130184214229>`__
#. `Downloading GRID Driver and Software License Packages <#EN-US_TOPIC_0149610914__section91244318407>`__
#. `Deploying and Configuring the License Server <#EN-US_TOPIC_0149610914__section19229135113439>`__
#. `Installing the GRID Driver and Configuring the License <#EN-US_TOPIC_0149610914__section17545653184812>`__

|image1|

-  NVIDIA allows you to apply for a 90-day trial license.
-  For details about GPU-accelerated ECSs with different specifications and application scenarios, see `GPU-accelerated ECSs <en-us_topic_0097289624.html>`__.

Purchasing a GRID License
-------------------------

-  Purchase a license.

   To obtain an official license, contact NVIDIA or their NVIDIA agent in your local country or region.

-  Apply for a trial license.

   Log in at the `official NVIDIA website <https://www.nvidia.com/object/nvidia-enterprise-account.html>`__ and enter desired information.

   For details about how to register an account and apply for a trial license, see `official NVIDIA help page <https://nvid.nvidia.com/NvidiaUtilities/#/needHelp>`__.\ |image2|

   The method of using a trial license is the same as that of using an official license. You can use an official license to activate an account with a trial license to prevent repetitive registration. The trial license has a validity period of 90 days. After the trial license expires, it cannot be used anymore. Purchase an official license then.

   | **Figure 1** Applying for a trial license
   | |image3|

Downloading GRID Driver and Software License Packages
-----------------------------------------------------

#. Obtain the driver installation package required for an OS. For details, see `Table 1 <#EN-US_TOPIC_0149610914__table188851534175019>`__.For more information about the GRID driver, see `NVIDIA vGPU Software Documentation <https://docs.nvidia.com/grid/index.html>`__.\ |image4|

   For a GPU passthrough ECS, select a GRID driver version as required.

   For a GPU virtualization ECS, select a driver version based on the following table.

   

.. _EN-US_TOPIC_0149610914__table188851534175019:

   .. table:: **Table 1** GRID driver versions supported by GPU-accelerated ECSs

      +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
      | ECS Type              | GPU Attachment        | OS                    | Driver Version        | CPU Architecture      |
      +=======================+=======================+=======================+=======================+=======================+
      | G6                    | GPU passthrough       | -  Windows Server     | Select a version as   | x86_64                |
      |                       |                       |    2016 Standard      | required.             |                       |
      |                       |                       |    64bit              |                       |                       |
      +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
      | P2s                   | GPU passthrough       | -  Windows Server     | Select a version as   | x86_64                |
      |                       |                       |    2019 Standard      | required.             |                       |
      |                       |                       |    64bit              |                       |                       |
      |                       |                       | -  Windows Server     |                       |                       |
      |                       |                       |    2016 Standard      |                       |                       |
      |                       |                       |    64bit              |                       |                       |
      |                       |                       | -  Windows Server     |                       |                       |
      |                       |                       |    2012 R2 Standard   |                       |                       |
      |                       |                       |    64bit              |                       |                       |
      |                       |                       | -  Ubuntu Server      |                       |                       |
      |                       |                       |    20.04 64bit        |                       |                       |
      |                       |                       | -  Ubuntu Server      |                       |                       |
      |                       |                       |    18.04 64bit        |                       |                       |
      |                       |                       | -  Ubuntu Server      |                       |                       |
      |                       |                       |    16.04 64bit        |                       |                       |
      |                       |                       | -  CentOS 7.7 64bit   |                       |                       |
      |                       |                       | -  CentOS 7.4 64bit   |                       |                       |
      |                       |                       | -  EulerOS 2.5 64bit  |                       |                       |
      |                       |                       | -  Oracle Linux 7.6   |                       |                       |
      |                       |                       |    64bit              |                       |                       |
      +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
      | P2v                   | GPU passthrough       | -  Windows Server     | Select a version as   | x86_64                |
      |                       |                       |    2019 Standard      | required.             |                       |
      |                       |                       |    64bit              |                       |                       |
      |                       |                       | -  Windows Server     |                       |                       |
      |                       |                       |    2016 Standard      |                       |                       |
      |                       |                       |    64bit              |                       |                       |
      |                       |                       | -  Windows Server     |                       |                       |
      |                       |                       |    2012 R2 Standard   |                       |                       |
      |                       |                       |    64bit              |                       |                       |
      |                       |                       | -  Ubuntu Server      |                       |                       |
      |                       |                       |    16.04 64bit        |                       |                       |
      |                       |                       | -  CentOS 7.7 64bit   |                       |                       |
      |                       |                       | -  EulerOS 2.5 64bit  |                       |                       |
      |                       |                       | -  Oracle Linux 7.6   |                       |                       |
      |                       |                       |    64bit              |                       |                       |
      +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
      | P2                    | GPU passthrough       | Ubuntu Server 16.04   | Select a version as   | x86_64                |
      |                       |                       | 64bit                 | required.             |                       |
      +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
      | P1                    | GPU passthrough       | -  Windows Server     | Select a version as   | x86_64                |
      |                       |                       |    2012 R2 Standard   | required.             |                       |
      |                       |                       |    64bit              |                       |                       |
      |                       |                       | -  Ubuntu Server      |                       |                       |
      |                       |                       |    16.04 64bit        |                       |                       |
      |                       |                       | -  CentOS 7.4 64bit   |                       |                       |
      |                       |                       | -  Debian 9.0 64bit   |                       |                       |
      +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
      | PI2                   | GPU passthrough       | -  Windows Server     | Select a version as   | x86_64                |
      |                       |                       |    2019 Standard      | required.             |                       |
      |                       |                       |    64bit              |                       |                       |
      |                       |                       | -  Windows Server     |                       |                       |
      |                       |                       |    2016 Standard      |                       |                       |
      |                       |                       |    64bit              |                       |                       |
      |                       |                       | -  Windows Server     |                       |                       |
      |                       |                       |    2012 R2 Standard   |                       |                       |
      |                       |                       |    64bit              |                       |                       |
      |                       |                       | -  Ubuntu Server      |                       |                       |
      |                       |                       |    16.04 64bit        |                       |                       |
      |                       |                       | -  CentOS 7.8 64bit   |                       |                       |
      +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+

#. After the registration, log in at the `official NVIDIA website <https://nvid.nvidia.com/dashboard/>`__ and enter the account.

#. Check whether NVIDIA is used for the first time.

   a. If yes, go to step `4 <#EN-US_TOPIC_0149610914__li1859773663819>`__.
   b. If no, go to step `6 <#EN-US_TOPIC_0149610914__li0791101412396>`__.

#. Obtain the Product Activation Key (PAK) from the email indicating successful registration with NVIDIA.\ **Figure 2** PAK
   |image5|

#. Enter the PAK obtained in step `4 <#EN-US_TOPIC_0149610914__li1859773663819>`__ on the **Redeem Product Activation Keys** page and click **Redeem**.\ **Figure 3** Redeem Product Activation Keys
   |image6|

#. Specify **Username** and **Password** and click **LOGIN**.\ **Figure 4** Logging in to the official NVIDIA website
   |image7|

#. Log in at the official NVIDIA website as prompted and select **SOFTWARE DOWNLOADS**.\ **Figure 5** **SOFTWARE DOWNLOADS** page
   |image8|

#. Download the GRID driver of the required version. For details, see `Table 1 <#EN-US_TOPIC_0149610914__table188851534175019>`__.

#. Decompress the GRID driver installation package and install the driver that matches your ECS OS.

#. On the **SOFTWARE DOWNLOADS** page, click **ADDITIONAL SOFTWARE** to download the license software package.\ **Figure 6** ADDITIONAL SOFTWARE
   |image9|

Deploying and Configuring the License Server
--------------------------------------------

The following uses an ECS running CentOS 7.5 as an example to describe how to deploy and configure the license server on the ECS.

|image10|

-  The target ECS must have at least 2 vCPUs and 4 GiB of memory.
-  Ensure that the MAC address of the target ECS has been recorded.
-  If the license server is used in the production environment, deploy it in high availability mode. For details, see `official NVIDIA documentation for license server high availability <https://docs.nvidia.com/grid/ls/2019.05/grid-license-server-user-guide/index.html#license-server-high-availability>`__.

#. Configure the network.

   -  If the license server is to be accessed using the VPC, ensure that the license server and the GPU-accelerated ECS with the GRID driver installed are in the same VPC subnet.
   -  If the license server is to be accessed using a public IP address, configure the security group to which license server belongs and add inbound rules for TCP 7070 and TCP 8080.

2. Install the license server.

   For details, see the `official NVIDIA documentation for installing the license server <https://docs.nvidia.com/grid/ls/latest/grid-license-server-user-guide/index.html#installing-nvidia-grid-license-server>`__.

3. Obtain the license file.

   a. Log in to the `NVIDIA website <http://nvid.nvidia.com/dashboard/>`__ on a new tab and select **LICENSE SERVERS**.\ **Figure 7** LICENSE SERVERS
      |image11|

   b. Click **CREATE SERVER**.

   c. Set **Server Name**, **Description**, and **MAC Address** (MAC address of the license server).

   d. Select **Feature**, enter the number of required licenses in the **Licenses** text box, and click **ADD**.

      In active/standby deployment, enter the name of the standby server in **Failover License Server** and enter the MAC address in **Failover MAC Address**.

   e. Click **CREATE LICENSE SERVER**.\ **Figure 8** Create License Server
      |image12|

   f. Download the license file.\ **Figure 9** Downloading the license file
      |image13|

4. In the web browser, access the homepage of the license server management page using the link configured during the installation.

   Default URL: http://*IP address of the EIP*:8080/licserver

5. Choose **License Server** > **License Management**, select the .bin license file to be uploaded, and click **Upload**.\ **Figure 10** Uploading a license file
   |image14|

Installing the GRID Driver and Configuring the License
------------------------------------------------------

#. Install the GRID driver of a desired version, for example, on a GPU-accelerated Windows ECS.\ |image15|

   Microsoft remote login protocols do not support GPU 3D hardware acceleration. To use this function, install third-party desktop protocol-compliant software, such as VNC, PCoIP, or NICE DCV, and access the ECS through the client.

#. Open the NVIDIA control panel on the Windows control panel.

#. Enter the IP address and port number of the deployed license server in the level-1 license server, and then click **Apply**. If the message indicating that you have obtained a GRID license, the installation is successful. Additionally, the MAC address of the GPU-accelerated ECS with the GRID driver installed is displayed on the **Licensed Clients** page of the license server management console.\ **Figure 11** License server management console
   |image16|


.. |image1| image:: /_static/images/note_3.0-en-us.png
.. |image2| image:: /_static/images/note_3.0-en-us.png
.. |image3| image:: /_static/images/en-us_image_0178069404.png
   :class: imgResize

.. |image4| image:: /_static/images/note_3.0-en-us.png
.. |image5| image:: /_static/images/en-us_image_0178334448.png
   :class: imgResize

.. |image6| image:: /_static/images/en-us_image_0178334449.png
   :class: imgResize

.. |image7| image:: /_static/images/en-us_image_0178334450.png

.. |image8| image:: /_static/images/en-us_image_0000001093447741.png
   :class: imgResize

.. |image9| image:: /_static/images/en-us_image_0000001093667097.png
   :class: imgResize

.. |image10| image:: /_static/images/note_3.0-en-us.png
.. |image11| image:: /_static/images/en-us_image_0000001093449637.png
   :class: imgResize

.. |image12| image:: /_static/images/en-us_image_0000001093450009.png
   :class: imgResize

.. |image13| image:: /_static/images/en-us_image_0000001093310123.png
   :class: imgResize

.. |image14| image:: /_static/images/en-us_image_0178325096.png
   :class: imgResize

.. |image15| image:: /_static/images/note_3.0-en-us.png
.. |image16| image:: /_static/images/en-us_image_0178370293.png
   :class: imgResize

