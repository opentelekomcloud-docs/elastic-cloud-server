:original_name: en-us_topic_0000001234335274.html

.. _en-us_topic_0000001234335274:

Creating a Key Pair Using PuTTYgen
==================================

Scenarios
---------

You can use PuTTYgen to create a key pair and store the public key and private key locally.

.. note::

   Key pairs created using puttygen.exe must be imported by referring to :ref:`Importing a Key Pair <en-us_topic_0000001278734873>` before they are used.

Procedure
---------

#. Download and install PuTTY and PuTTYgen.

   https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

   .. note::

      PuTTYgen is a key generator, which is used to create a key pair that consists of a public key and a private key for PuTTY.

#. Obtain the public and private keys.

   a. Double-click **puttygen.exe** to open **PuTTY Key Generator**.


      .. figure:: /_static/images/en-us_image_0000001234512206.png
         :alt: **Figure 1** PuTTY Key Generator

         **Figure 1** PuTTY Key Generator

   b. Click **Generate**.

      The key generator automatically generates a key pair that consists of a public key and a private key. The content shown in the red box in :ref:`Figure 2 <en-us_topic_0000001234335274__en-us_topic_0037960038_fig4678746517750>` is the public key.

      .. _en-us_topic_0000001234335274__en-us_topic_0037960038_fig4678746517750:

      .. figure:: /_static/images/en-us_image_0000001278632153.png
         :alt: **Figure 2** Generating the public and private keys

         **Figure 2** Generating the public and private keys

#. .. _en-us_topic_0000001234335274__li18403111116343:

   Copy the public key to a .txt file and save it to a local directory.

   .. note::

      Do not save the public key by clicking **Save public key** because this operation will change the format of the public key content and cause the public key to fail to be imported to the management console.

#. Save the private key and keep it secure. The private key can be downloaded only once.

   The format in which to save your private key file varies depending on application scenarios.

   -  When using PuTTY to log in to a Linux ECS:

      Save the private key file in the **.ppk** format.

      a. On the **PuTTY Key Generator** page, choose **File** > **Save private key**.


         .. figure:: /_static/images/en-us_image_0000001278352685.png
            :alt: **Figure 3** Saving a private key

            **Figure 3** Saving a private key

      b. Save the converted private key file, such as **kp-123.ppk**, locally.

   -  When using Xshell to log in to a Linux ECS or obtaining the password for logging in to a Windows ECS:

      Save the private key file in the **.pem** format.

      a. Choose **Conversions** > **Export OpenSSH key**.

         .. note::

            If you use this private file to obtain the password for logging in to a Windows ECS, do not specify **Key passphrase** for **Export OpenSSH key** so that you can obtain the password successfully.


         .. figure:: /_static/images/en-us_image_0000001278751917.png
            :alt: **Figure 4** Saving a private key

            **Figure 4** Saving a private key

      b. Save the private key, for example, **kp-123.pem**, locally.

#. After you have saved the key pair, import your public key to the ECS by referring to :ref:`Importing a Key Pair <en-us_topic_0000001278734873>`.
