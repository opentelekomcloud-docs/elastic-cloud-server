:original_name: en-us_topic_0047654687.html

.. _en-us_topic_0047654687:

Why Does a Key Pair Created Using **puttygen.exe** Fail to Be Imported on the Management Console?
=================================================================================================

Symptom
-------

When you try to import a key pair that you created using **puttygen.exe** on the management console, the system displays a message indicating that the import failed.

Possible Causes
---------------

The format of the public key content does not meet system requirements.

If you store a public key by clicking **Save public key** on PuTTY Key Generator, the format of the public key content will change. Therefore, you cannot import the key on the management console.

Solution
--------

Use the locally stored private key and **PuTTY Key Generator** to restore the format of the public key content. Then, import the public key to the management console.

#. Double-click **puttygen.exe** to open **PuTTY Key Generator**.


   .. figure:: /_static/images/en-us_image_0000001234512206.png
      :alt: **Figure 1** PuTTY Key Generator

      **Figure 1** PuTTY Key Generator

#. Click **Load** and select the private key.

   The system automatically loads the private key and restores the format of the public key content in **PuTTY Key Generator**. The content in the red box in :ref:`Figure 2 <en-us_topic_0047654687__fig5530274016810>` is the public key whose format meets system requirements.

   .. _en-us_topic_0047654687__fig5530274016810:

   .. figure:: /_static/images/en-us_image_0037982934.png
      :alt: **Figure 2** Restoring the format of the public key content

      **Figure 2** Restoring the format of the public key content

#. Copy the public key content to a .txt file and save the file in a local directory.

#. Import the public key to the management console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner and select your region and project.
   c. Under **Computing**, click **Elastic Cloud Server**.
   d. In the navigation pane on the left, choose **Key Pair**.
   e. On the key pair page, click **Import Key Pair**.
   f. Copy the public key content in the .txt file to **Public Key Content** and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
