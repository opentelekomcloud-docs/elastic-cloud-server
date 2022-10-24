:original_name: en-us_topic_0000001278734873.html

.. _en-us_topic_0000001278734873:

Importing a Key Pair
====================

Scenarios
---------

You need to import a key pair in either of the following scenarios:

-  Create a key pair using PuTTYgen and import the public key to the ECS.

-  Import the public key of an existing key pair to the ECS to let the system maintain your public key.

   .. note::

      If the public key of the existing key pair is stored by clicking **Save public key** on PuTTY Key Generator, the public key cannot be imported to the management console.

      If you want to use this existing key pair for remote login, see :ref:`Why Does a Key Pair Created Using puttygen.exe Fail to Be Imported on the Management Console? <en-us_topic_0047654687>`

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the navigation pane on the left, choose **Key Pair**.

#. On the **Key Pair Service** page, click **Import Key Pair**.


   .. figure:: /_static/images/en-us_image_0000001234671514.png
      :alt: **Figure 1** Import Public Key

      **Figure 1** Import Public Key

#. Use either of the following methods to import the key pair:

   -  Selecting a file

      a. In the **Import Key Pair** dialog box of the management console, click **Select File** and select the locally stored public key file (for example, the .txt file saved in :ref:`3 <en-us_topic_0000001234335274__li18403111116343>` in :ref:`Creating a Key Pair Using PuTTYgen <en-us_topic_0000001234335274>`).

         .. note::

            Make sure that the file to be imported is a public key file.

      b. Click **OK**.

         After the public key is imported, you can change its name.

   -  Copying the public key content

      a. Copy the public key content from the locally stored .txt file into the **Public Key Content** text box.
      b. Click **OK**.

Helpful Links
-------------

-  :ref:`What Should I Do If a Key Pair Cannot Be Imported? <en-us_topic_0019883415>`
-  :ref:`Why Does a Key Pair Created Using puttygen.exe Fail to Be Imported on the Management Console? <en-us_topic_0047654687>`

.. |image1| image:: /_static/images/en-us_image_0210779229.png
