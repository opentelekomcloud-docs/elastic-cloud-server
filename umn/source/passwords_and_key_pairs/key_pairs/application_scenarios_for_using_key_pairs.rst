:original_name: en-us_topic_0000001278335673.html

.. _en-us_topic_0000001278335673:

Application Scenarios for Using Key Pairs
=========================================

Key Pairs
---------

Key pairs are a set of security credentials for identity authentication when you remotely log in to ECSs.

A key pair consists of a public key and a private key. Key Pair Service (KPS) stores the public key and you store the private key. If you have imported a public key into a Linux ECS, you can use the corresponding private key to log in to the ECS without a password. Therefore, you do not need to worry about password interception, cracking, or leakage.

Scenarios
---------

When purchasing an ECS, you are advised to select the key pair login mode. For Windows ECSs, key pairs are required to decrypt the passwords so that you can use the decrypted password to log in.

-  Logging in to a Linux ECS

   You can directly use a key pair to log in.

   -  When you are creating the ECS, select the key pair login mode. For details, see "Set Login Mode" in :ref:`Step 3: Configure Advanced Settings <en-us_topic_0163572591>`.
   -  After the ECS is created, bind a key pair to the ECS by referring to "Binding a Key Pair" in the *Data Encryption Workshop User Guide*.

-  Logging in to a Windows ECS

   You can use the key pair to obtain a password for login. The password is randomly generated and therefore is more secure.

   For details, see :ref:`Obtaining the Password for Logging In to a Windows ECS <en-us_topic_0031107266>`.

Creating a Key Pair
-------------------

You can create a key pair or use an existing one for remote login authentication.

-  Creating a key pair

   You can create a key pair using either of the following method:

   -  Follow the instructions in :ref:`(Recommended) Creating a Key Pair on the Management Console <en-us_topic_0000001278350057>`. The public key is automatically stored in the system, and the private key is stored locally.

   -  Follow the instructions in :ref:`Creating a Key Pair Using PuTTYgen <en-us_topic_0000001234335274>`. Both the public and private keys are stored locally.

      After the key pair is created, import the key pair following the instructions provided in :ref:`Importing a Key Pair <en-us_topic_0000001278734873>` so that you can use it.

-  Using an existing key pair

   If an existing key pair (created using PuTTYgen, for example) is available, you can import the public key by referring to :ref:`Importing a Key Pair <en-us_topic_0000001278734873>` on the management console to let the system maintain the public key for you.

   .. note::

      If the public key of the existing key pair is stored by clicking **Save public key** on PuTTY Key Generator, the public key cannot be imported to the management console.

      If you want to use this existing key pair for remote login, see :ref:`Why Does a Key Pair Created Using puttygen.exe Fail to Be Imported on the Management Console? <en-us_topic_0047654687>`

Constraints
-----------

-  Key pairs can be used to remotely log in to Linux ECSs only.
-  SSH-2 key pairs created on the console support only the RSA-2048 cryptographic algorithms.
-  Key pairs are only for one user but they can be imported to other users.
-  Key pairs can be used only for ECSs in the same region.
-  Imported key pairs support the following cryptographic algorithms:

   -  RSA-1024
   -  RSA-2048
   -  RSA-4096

-  Store your private key in a secure place because you need to use it to prove your identity when logging in to your ECS. The private key can be downloaded once only.
