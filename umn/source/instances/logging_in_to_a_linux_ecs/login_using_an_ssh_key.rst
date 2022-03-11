Login Using an SSH Key
======================

Scenarios
---------

This section describes how to remotely log in to a Linux ECS using an SSH key pair from Windows and Linux, respectively.

Prerequisites
-------------

-  You have obtained the private key file used during ECS creation.
-  You have bound an EIP to the ECS. For details, see `Viewing Details About an ECS <instances/viewing_ecs_information/viewing_details_about_an_ecs>`__.

-  You have configured the inbound rules of the security group. For details, see `Configuring Security Group Rules <security/security_groups/configuring_security_group_rules>`__.
-  The network connection between the login tool (PuTTY) and the target ECS is normal. For example, the default port 22 is not blocked by the firewall.

Logging In to the Linux ECS from Local Windows
----------------------------------------------

To log in to the Linux ECS from local Windows, perform the operations described in this section.

**Method 1: Use PuTTY to log in to the ECS.**

The following operations use PuTTY as an example. Before logging in to the ECS using PuTTY, make sure that the private key file has been converted to .ppk format.

#. Check whether the private key file has been converted to .ppk format.

   -  If yes, go to step `7 <#EN-US_TOPIC_0017955380__li40879966111724>`__.
   -  If no, go to step `2 <#EN-US_TOPIC_0017955380__li8851985111724>`__.

#. Visit the following website and download PuTTY and PuTTYgen:

   https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

   |image1|

   PuTTYgen is a key generator, which is used to create a key pair that consists of a public key and a private key for PuTTY.

#. Run PuTTYgen.

#. In the **Actions** pane, click **Load** and import the private key file that you stored during ECS creation.

   Ensure that the format of **All files (*.*)** is selected.

#. Click **Save private key**.

#. Save the converted private key, for example, **kp-123.ppk**, to the local computer.

#. Double-click **PUTTY.EXE**. The **PuTTY Configuration** page is displayed.

#. Choose **Session** and enter the EIP of the ECS under **Host Name (or IP address)**.\ **Figure 1** Configuring the EIP
   |image2|

#. Choose **Connection** > **Data**. Enter the image username in **Auto-login username**.\ |image3|

   -  If a public image is used, see `Public Images Introduction <https://docs.otc.t-systems.com/en-us/ims/index.html>`__ for the image username.
   -  If a private image is used, use the username of the private image.

#. Choose **Connection** > **SSH** > **Auth**. In the last configuration item **Private key file for authentication**, click **Browse** and select the private key converted in step `6 <#EN-US_TOPIC_0017955380__li56738001111724>`__.

#. Click **Open**.

   Log in to the ECS.

**Method 2: Use Xshell to log in to the ECS.**

#. Start the Xshell tool.

#. Run the following command using the EIP to remotely log in to the ECS through SSH:

   **ssh** *Username*\ **@**\ *EIP*

   |image4|

   -  If a public image is used, see `Public Images Introduction <https://docs.otc.t-systems.com/en-us/ims/index.html>`__ for the image username.
   -  If a private image is used, use the username of the private image.

#. (Optional) If the system displays the **SSH Security Warning** dialog box, click **Accept & Save**.\ **Figure 2** SSH Security Warning
   |image5|

#. Select **Public Key** and click **Browse** beside the user key text box.

#. In the user key dialog box, click **Import**.

#. Select the locally stored key file and click **Open**.

#. Click **OK** to log in to the ECS.

Logging In to the Linux ECS from Local Linux
--------------------------------------------

To log in to the Linux ECS from local Linux, perform the operations described in this section. The following operations use private key file **kp-123.pem** as an example to log in to the ECS. The name of your private key file may differ.

#. On the Linux CLI, run the following command to change operation permissions:

   **chmod 400 /**\ *path*\ **/kp-123.pem**

   |image6|

   In the preceding command, *path* refers to the path where the key file is saved.

#. Run the following command to log in to the ECS:

   **ssh -i /**\ *path*\ **/kp-123.pem** *Default username*\ **@**\ *EIP*

   For example, if the default username is **root** and the EIP is **123.123.123.123**, run the following command:

   **ssh -i /path/kp-123.pem root@123.123.123.123**

   |image7|

   In the preceding command:

   -  *path* refers to the path under which the key file is stored.
   -  *EIP* is the EIP bound to the ECS.


.. |image1| image:: /_static/images/note_3.0-en-us.png
.. |image2| image:: /_static/images/en-us_image_0000001082643605.jpg
   :class: imgResize

.. |image3| image:: /_static/images/note_3.0-en-us.png
.. |image4| image:: /_static/images/note_3.0-en-us.png
.. |image5| image:: /_static/images/en-us_image_0178475901.png

.. |image6| image:: /_static/images/note_3.0-en-us.png
.. |image7| image:: /_static/images/note_3.0-en-us.png
