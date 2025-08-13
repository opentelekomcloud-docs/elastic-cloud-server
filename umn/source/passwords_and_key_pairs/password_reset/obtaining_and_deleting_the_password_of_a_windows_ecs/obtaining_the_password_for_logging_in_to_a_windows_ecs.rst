:original_name: en-us_topic_0031107266.html

.. _en-us_topic_0031107266:

Obtaining the Password for Logging In to a Windows ECS
======================================================

Scenarios
---------

Password authentication is required to log in to a Windows ECS. You must use the private key bound to the ECS when the ECS was created to obtain the administrator password generated during the ECS creation. The administrator user is **Administrator** or the user configured using Cloudbase-Init. This password is randomly generated, offering high security.

You can obtain the initial password for logging in to a Windows ECS through the management console or APIs. For details, see this section.

Prerequisites
-------------

You have obtained the private key file (.pem file) which was generated during the ECS creation.

Obtaining the Password Through the Management Console
-----------------------------------------------------

#. Obtain the private key file (.pem file) used when you created the ECS.

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the **Elastic Cloud Server** page, select the target ECS.

#. In the **Operation** column, click **More** and select **Get Password**.


   .. figure:: /_static/images/en-us_image_0000002385408725.png
      :alt: **Figure 1** Get Password

      **Figure 1** Get Password

#. Use either of the following methods to obtain the password through the private key:

   -  Click **Select File** and upload the private key from a local directory.
   -  Copy the content of the private key file and paste it into the text box.

#. Click **Get Password** to obtain a random password.

Obtaining the Password Through APIs
-----------------------------------

#. Obtain the private key file (.pem file) used when you created the ECS.

#. Set up the API calling environment.

#. Call APIs. For details, see `API Usage Guidelines <https://docs.otc.t-systems.com/api/ecs/en-us_topic_0020805967.html>`__ in the *Elastic Cloud Server API Reference*.

#. .. _en-us_topic_0031107266__li5770130102852:

   Obtain the ciphertext password.

   Call the password obtaining APIs to obtain the ciphertext password of the public key encrypted using RSA. The API URI is in the format "GET /v2/{*project_id*}/servers/{*server_id*}/os-server-password".

   .. note::

      For details, see `Obtaining the Password for Logging In to an ECS <https://docs.otc.t-systems.com/elastic-cloud-server/api-ref/native_openstack_nova_apis/key_and_password_management/obtaining_the_password_for_logging_in_to_an_ecs.html#en-us-topic-0031176553>`__.

#. Decrypt the ciphertext password.

   Use the private key file used when you created the ECS to decrypt the ciphertext password obtained in step :ref:`4 <en-us_topic_0031107266__li5770130102852>`.

   a. Run the following command to convert the ciphertext password format to ".key -nocrypt" using OpenSSL:

      **openssl pkcs8 -topk8 -inform PEM -outform DER -in rsa_pem.key -out pkcs8_der.key -nocrypt**

   b. Invoke the Java class library **org.bouncycastle.jce.provider.BouncyCastleProvider** and use the key file to edit the code decryption ciphertext.

.. |image1| image:: /_static/images/en-us_image_0000002324093730.png
