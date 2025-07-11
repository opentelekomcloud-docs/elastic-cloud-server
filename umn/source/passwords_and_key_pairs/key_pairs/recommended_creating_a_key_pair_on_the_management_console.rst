:original_name: en-us_topic_0000001278350057.html

.. _en-us_topic_0000001278350057:

(Recommended) Creating a Key Pair on the Management Console
===========================================================

Scenarios
---------

You can create a key pair on the management console. After the key pair is created, the public key is automatically stored in the system, and the private key is stored in your local computer. After a key pair is created for an ECS on the management console, ensure that you store your private key in a secure place. Without a private key, you will not be able to log in to the ECS.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the navigation pane on the left, choose **Key Pair**.

#. On the displayed page, click **Create Key Pair**.

#. Enter a key pair name.

   A key pair name consists of two parts: KeyPair and four random digits (KeyPair-xxxx).

#. Click **OK**.

#. Manually or automatically download a .pem private key file with the name that you specify as the key name. Store it in a secure place and click **OK**.

   .. note::

      This is the only chance for you to save the private key file. Keep it secure. You'll need to provide the key pair name when you create an ECS, and the corresponding private key each time you connect to the ECS through SSH.

.. |image1| image:: /_static/images/en-us_image_0000001234668870.png
