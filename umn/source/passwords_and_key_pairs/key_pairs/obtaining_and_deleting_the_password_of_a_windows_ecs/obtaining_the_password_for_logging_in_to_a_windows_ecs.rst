:original_name: en-us_topic_0031107266.html

.. _en-us_topic_0031107266:

Obtaining the Password for Logging In to a Windows ECS
======================================================

Scenarios
---------

Password authentication is required to log in to a Windows ECS. Therefore, you must use the key file used when you created the ECS to obtain the administrator password generated during ECS creation. The administrator user is **Administrator** or the user configured using Cloudbase-Init. This password is randomly generated, offering high security.

You can obtain the initial password for logging in to a Windows ECS through the management console or APIs. For details, see this section.

Obtaining the Password Through the Management Console
-----------------------------------------------------

#. Obtain the private key file (.pem file) used when you created the ECS.

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the **Elastic Cloud Server** page, select the target ECS.

#. In the **Operation** column, click **More** and select **Get Password**.


   .. figure:: /_static/images/en-us_image_0000001659531420.png
      :alt: **Figure 1** Get Password

      **Figure 1** Get Password

#. Use either of the following methods to obtain the password through the key file:

   -  Click **Select File** and upload the key file from a local directory.
   -  Copy the key file content to the text field.

#. Click **Get Password** to obtain a random password.

Obtaining the Password Through APIs
-----------------------------------

#. Obtain the private key file (.pem file) used when you created the ECS.

#. Set up the API calling environment.

#. Call APIs. For details, see `API Usage Guidelines <https://docs.otc.t-systems.com/api/ecs/en-us_topic_0020805967.html>`__ in *Elastic Cloud Server API Reference*.

#. .. _en-us_topic_0031107266__li5770130102852:

   Obtain the ciphertext password.

   Call the password obtaining APIs to obtain the ciphertext password of the public key encrypted using RSA. The API URI is in the format "GET /v2/{*tenant_id*}/servers/{*server_id*}/os-server-password".

   .. note::

      For details, see `Obtaining the Password for Logging In to an ECS <https://docs.otc.t-systems.com/api/ecs/en-us_topic_0031176553.html>`__.

#. Decrypt the ciphertext password.

   Use the private key file used when you created the ECS to decrypt the ciphertext password obtained in step :ref:`4 <en-us_topic_0031107266__li5770130102852>`.

   a. Run the following command to convert the ciphertext password format to ".key -nocrypt" using OpenSSL:

      **openssl pkcs8 -topk8 -inform PEM -outform DER -in rsa_pem.key -out pkcs8_der.key -nocrypt**

   b. Invoke the Java class library **org.bouncycastle.jce.provider.BouncyCastleProvider** and use the key file to edit the code decryption ciphertext.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
