:original_name: en-us_topic_0017955380.html

.. _en-us_topic_0017955380:

Login Using an SSH Key
======================

Scenarios
---------

This section describes how to use an SSH key pair to remotely log in to a Linux ECS from a Windows and a Linux server, respectively.

Prerequisites
-------------

-  You have obtained the private key file used for creating the ECS. For details about how to create a key pair, see :ref:`(Recommended) Creating a Key Pair on the Management Console <en-us_topic_0000001278350057>`.
-  You have bound an EIP to the ECS. For details, see :ref:`Viewing ECS Details (List View) <en-us_topic_0017130261>`.

-  You have configured the inbound rules of the security group. For details, see :ref:`Configuring Security Group Rules <en-us_topic_0030878383>`.
-  The network connection between the login tool (PuTTY) and the target ECS is normal. For example, the default port 22 is not blocked by the firewall.

.. _en-us_topic_0017955380__section47918167111724:

Logging In to a Linux ECS from a Local Windows Server
-----------------------------------------------------

You have two methods to log in to a Linux ECS from a local Windows server.

**Method 1: Use PuTTY to log in to the ECS.**

The following operations use PuTTY as an example. Before using PuTTY to log in, make sure that the private key file has been converted to .ppk format.

#. Check whether the private key file has been converted to .ppk format.

   -  If yes, go to step :ref:`7 <en-us_topic_0017955380__li40879966111724>`.
   -  If no, go to step :ref:`2 <en-us_topic_0017955380__li8851985111724>`.

#. .. _en-us_topic_0017955380__li8851985111724:

   Visit the following website and download PuTTY and PuTTYgen:

   https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

   .. note::

      PuTTYgen is a key generator, which is used to create a key pair that consists of a public key and a private key for PuTTY.

#. Run PuTTYgen.

#. In the **Actions** pane, click **Load** and import the private key file that you stored during ECS creation.

   Ensure that the format of **All files (*.*)** is selected.

#. Click **Save private key**.

#. .. _en-us_topic_0017955380__li56738001111724:

   Save the converted private key, for example, **kp-123.ppk**, to the local computer.

#. .. _en-us_topic_0017955380__li40879966111724:

   Double-click **PUTTY.EXE**. The **PuTTY Configuration** page is displayed.

#. Choose **Session** and enter the EIP of the ECS under **Host Name (or IP address)**.


   .. figure:: /_static/images/en-us_image_0000001082643605.jpg
      :alt: **Figure 1** Configuring the EIP

      **Figure 1** Configuring the EIP

#. Choose **Connection** > **Data**. Enter the image username in **Auto-login username**.

   .. note::

      -  If a public image is used, see `Public Images Introduction <https://docs.otc.t-systems.com/image-management-service/public-images/>`__ for the image username.
      -  If a private image is used, use the username of the private image.

#. Choose **Connection** > **SSH** > **Auth**. In the last configuration item **Private key file for authentication**, click **Browse** and select the private key converted in step :ref:`6 <en-us_topic_0017955380__li56738001111724>`.

#. Click **Open** to log in to the ECS.

**Method 2: Use Xshell to log in to the ECS.**

#. Start the Xshell tool.

#. Run the following command using the EIP to remotely log in to the ECS through SSH:

   **ssh** **Username**\ **@\ EIP**

   .. note::

      -  If a public image is used, see `Public Images Introduction <https://docs.otc.t-systems.com/image-management-service/public-images/>`__ for the image username.
      -  If a private image is used, use the username of the private image.

#. (Optional) If the system displays the **SSH Security Warning** dialog box, click **Accept & Save**.


   .. figure:: /_static/images/en-us_image_0178475901.png
      :alt: **Figure 2** SSH Security Warning

      **Figure 2** SSH Security Warning

#. Select **Public Key** and click **Browse** beside the user key text box.

#. In the user key dialog box, click **Import**.

#. Select the locally stored key file and click **Open**.

#. Click **OK** to log in to the ECS.

.. _en-us_topic_0017955380__section3666784111724:

Logging In to a Linux ECS from a Local Linux Server
---------------------------------------------------

To log in to the Linux ECS from local Linux, perform the operations described in this section. The following operations use private key file **kp-123.pem** as an example to log in to the ECS. The name of your private key file may differ.

#. On the Linux CLI, run the following command to change operation permissions:

   **chmod 400 /**\ *path*\ **/kp-123.pem**

   .. note::

      In the preceding command, replace *path* with the actual path where the key file is saved.

#. Run the following command to log in to the ECS:

   **ssh -i /path/kp-123.pem** **Default username**\ **@**\ **EIP**

   For example, if the default username is **root** and the EIP is **123.123.123.123**, run the following command:

   **ssh -i /path/kp-123.pem root@123.123.123.123**

   .. note::

      In the preceding command:

      -  *path* refers to the path under which the key file is stored.
      -  *EIP* is the EIP bound to the ECS.
