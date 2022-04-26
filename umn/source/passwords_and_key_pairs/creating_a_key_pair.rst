:original_name: en-us_topic_0014250631.html

.. _en-us_topic_0014250631:

Creating a Key Pair
===================

Overview
--------

A key pair that consists of a public key and a private key is required for authentication when you log in to an ECS. Both the public and private keys are used for authentication. Therefore, you must use an existing key pair or create a new one for remote login authentication.

-  Creating a key pair

   If no key pair is available, create one, in which the private key is used for login authentication. You can use either of the following methods to create a key pair:

   -  (Recommended) Create a key pair on the management console. After the creation, the public key is automatically stored in the system, and the private key is manually stored in a local directory. For details, see :ref:`Creating a Key Pair on the Management Console <en-us_topic_0014250631__section35336147204538>`.
   -  Create a key pair using **puttygen.exe**. After the creation, both the public key and private key are stored locally. For details, see :ref:`Creating a Key Pair Using puttygen.exe <en-us_topic_0014250631__section38463609165715>`. After the creation, import the key pair by following the instructions provided in :ref:`Importing a Key Pair <en-us_topic_0014250631__section62005706143441>`. Then, the key pair can be used.

-  Using an existing key pair

   If a key pair is available locally, for example, generated using PuTTYgen, you can import the public key on the management console so that the system maintains the public key file. For details, see :ref:`Importing a Key Pair <en-us_topic_0014250631__section62005706143441>`.

   .. note::

      If the public key of the existing key pair is stored by clicking **Save public key** of **puttygen.exe**, the public key cannot be imported to the management console.

      If this key pair must be used for remote authentication, see :ref:`Why Does a Key Pair Created Using puttygen.exe Fail to Be Imported on the Management Console? <en-us_topic_0047654687>`

Constraints
-----------

-  ECSs support the following encryption algorithms:

   -  SSH-2 (RSA, 1024)
   -  SSH-2 (RSA, 2048)
   -  SSH-2 (RSA, 4096)

-  The private key is one of the most important functions for protecting your ECS during remote login. Save the private key to your local directory and keep it secure. The private key can be downloaded only once.

.. _en-us_topic_0014250631__section35336147204538:

Creating a Key Pair on the Management Console
---------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the navigation pane on the left, choose **Key Pair**.

#. On the right side of the page, click **Create Key Pair**.

#. Enter the key name and click **OK**.

   An automatically allocated key name consists of **KeyPair-** and a 4-digit random number. Change it to an easy-to-remember one, for example, **KeyPair-xxxx_ecs**.

#. Manually or automatically download the private key file. The file name is the specified key pair name with a suffix of .pem. Securely store the private key file. In the displayed dialog box, click **OK**.

   .. note::

      This is the only opportunity for you to save the private key file. Keep it secure. When creating an ECS, provide the name of your desired key pair. Each time you log in to the ECS using SSH, provide the private key.

.. _en-us_topic_0014250631__section38463609165715:

Creating a Key Pair Using **puttygen.exe**
------------------------------------------

#. Download and install PuTTY and PuTTYgen.

   https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

   .. note::

      PuTTYgen is a key generator, which is used to create a key pair that consists of a public key and a private key for PuTTY.

#. Obtain the public and private keys.

   a. Double-click **puttygen.exe** to switch to the **PuTTY Key Generator** page.

      .. _en-us_topic_0014250631__en-us_topic_0037960038_fig4490538015580:

      .. figure:: /_static/images/en-us_image_0272917695.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 1** PuTTY Key Generator

   b. Click **Generate**.

      The key generator automatically generates a key pair that consists of a public key and a private key. The public key is shown in the red box in :ref:`Figure 2 <en-us_topic_0014250631__en-us_topic_0037960038_fig4678746517750>`.

      .. _en-us_topic_0014250631__en-us_topic_0037960038_fig4678746517750:

      .. figure:: /_static/images/en-us_image_0272919399.png
         :alt: **Figure 2** Obtaining the public and private keys
      

         **Figure 2** Obtaining the public and private keys

#. .. _en-us_topic_0014250631__li24584709151818:

   Copy the public key content to a .txt file and save the file in a local directory.

   .. note::

      Do not save the public key by clicking **Save public key**. Storing a public key by clicking **Save public key** of **puttygen.exe** will change the format of the public key content. Such a key cannot be imported to the management console.

#. Save the private key and keep it secure. The private key can be downloaded only once.

   The format in which to save your private key varies depending on application scenarios:

   -  Saving the private key in .ppk format

      When you are required to log in to a Linux ECS using PuTTY, you must use the .ppk private key. To save the private key in .ppk format, perform the following operations:

      a. On the **PuTTY Key Generator** page, choose **File** > **Save private key**.

         .. _en-us_topic_0014250631__fig1031955919299:

         .. figure:: /_static/images/en-us_image_0276033982.png
            :alt: Click to enlarge
            :figclass: imgResize
         

            **Figure 3** Save private key

      b. Save the converted private key, for example, **kp-123.ppk**, in a local directory.

   -  Saving the private key in .pem format

      When you are required to log in to a Linux ECS using Xshell or attempt to obtain the password for logging in to a Windows ECS, you must use the .pem private key for authentication. To save the private key in .pem format, perform the following operations:

      a. Choose **Conversions** > **Export OpenSSH key**.

         .. note::

            If you use this private file to obtain the password for logging in to a Windows ECS, when you choose **Export OpenSSH key**, do not configure **Key passphrase**. Otherwise, obtaining the password will fail.

         .. _en-us_topic_0014250631__fig15752222153016:

         .. figure:: /_static/images/en-us_image_0272919409.png
            :alt: Click to enlarge
            :figclass: imgResize
         

            **Figure 4** Export OpenSSH key

      b. Save the private key, for example, **kp-123.pem**, in a local directory.

#. Import the public key to the system. For details, see "Copying the public key content" in :ref:`Importing a Key Pair <en-us_topic_0014250631__section62005706143441>`.

.. _en-us_topic_0014250631__section62005706143441:

Importing a Key Pair
--------------------

If you store a public key by clicking **Save public key** of **puttygen.exe**, the format of the public key content will change. Such a key cannot be imported to the management console. To resolve this issue, obtain the public key content in correct format and import the content to the management console. For details, see :ref:`Why Does a Key Pair Created Using puttygen.exe Fail to Be Imported on the Management Console? <en-us_topic_0047654687>`

#. Log in to the management console.

#. Click |image2| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the navigation pane on the left, choose **Key Pair**.

#. On the right side of the page, click **Import Key Pair**.

   .. _en-us_topic_0014250631__fig30209536143442:

   .. figure:: /_static/images/en-us_image_0037980515.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 5** Import Key Pair

#. Use either of the following methods to import the key pair:

   -  Selecting a file

      a. On the **Import Key Pair** page of the management console, click **Select File** and select the local public key file, for example, the .txt file saved in :ref:`3 <en-us_topic_0014250631__li24584709151818>`.

         .. note::

            When importing a key pair, ensure that the public key is imported. Otherwise, the importing will fail.

      b. Click **OK**.

         After the public key is imported, you can change its name.

   -  Copying the public key content

      a. Copy the content of the public key in .txt file into the **Public Key Content** text box.
      b. Click **OK**.

Helpful Links
-------------

-  :ref:`What Should I Do If a Key Pair Cannot Be Imported? <en-us_topic_0019883415>`
-  :ref:`Why Does a Key Pair Created Using puttygen.exe Fail to Be Imported on the Management Console? <en-us_topic_0047654687>`

.. |image1| image:: /_static/images/en-us_image_0210779229.png

.. |image2| image:: /_static/images/en-us_image_0210779229.png

