:original_name: en-us_topic_0017955633.html

.. _en-us_topic_0017955633:

Login Using an SSH Password
===========================

Scenarios
---------

This section describes how to remotely log in to a Linux ECS using an SSH password from Windows and Linux, respectively.

.. important::

   Logging in to a Linux ECS using SSH password authentication is disabled by default. If you require password authentication, configure it after logging in to the ECS. To ensure system security, reset the common user password for logging in to the Linux ECS after configuring SSH password authentication.

Prerequisites
-------------

-  The target ECS is running.
-  You have bound an EIP to the ECS. For details, see :ref:`Binding an EIP <en-us_topic_0174917535>`.

-  Access to port 22 is allowed in the inbound direction of the security group to which the ECS belongs. For details, see :ref:`Configuring Security Group Rules <en-us_topic_0030878383>`.
-  The network connection between the login tool (PuTTY) and the target ECS is normal. For example, the default port 22 is not blocked by the firewall.
-  You have obtained the SSH login permission and reset the common user password for logging in to the Linux ECS. For details, see :ref:`Configuring the Login Permission Using SSH Password Authentication <en-us_topic_0017955633__section6207684794951>`.

.. _en-us_topic_0017955633__section6207684794951:

Configuring the Login Permission Using SSH Password Authentication
------------------------------------------------------------------

**Assigning the remote login permission using SSH key authentication**

#. Use the SSH key to log in to the Linux ECS. For details, see :ref:`Login Using an SSH Key <en-us_topic_0017955380>`.

#. Run the following command to change the value of **PasswordAuthentication** in **/etc/ssh/sshd_config** to **yes**:

   **sudo vi /etc/ssh/sshd_config**

   .. note::

      For the ECSs running the SUSE or OpenSUSE OSs, ensure that the values of **PasswordAuthentication**, **ChallengeResponseAuthentication**, and **UsePAM** in **/etc/ssh/sshd_config** are all **yes**.

#. Run the following command to change the **ssh_pwauth** value to **1** or **true** in **/etc/cloud/cloud.cfg**:

   **sudo vi /etc/cloud/cloud.cfg**

#. Run the following command to reload the sshd service:

   **sudo service sshd reload**

**To ensure system security, reset the common user password for logging in to the Linux ECS.**

#. Run the following command to reset the ECS password:

   If the ECS username is **linux**, run the following command:

   **sudo passwd linux**

   .. note::

      To remotely log in to an ECS as user **root**, perform the following operations:

      a. Run the following command to change the **disable_root** value to **0** or **false** and the **ssh_pwauth** value to **1** or **true** in **/etc/cloud/cloud.cfg**:

         **sudo vi /etc/cloud/cloud.cfg**

      b. Run the following command to set the user **root** password:

         **sudo passwd root**

#. Enter the new password as prompted and press **Enter**.

#. Confirm the password and press **Enter**.

#. Verify that the information displayed is similar to the following, indicating that the password has been reset:

   .. code-block::

      passwd: all authentication tokens updated successfully.

.. _en-us_topic_0017955633__section62068112020:

Logging In to the Linux ECS from a Local Windows Server
-------------------------------------------------------

To log in to the Linux ECS from a local Windows server, perform the operations described in this section.

The following operations use PuTTY as an example to log in to the ECS.

#. Visit the following website and download PuTTY and PuTTYgen:

   https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

#. Run PuTTY.

#. Click **Session**.

   a. **Host Name (or IP address)**: EIP bound to the ECS

   b. **Port**: **22**

   c. **Connection type**: **SSH**

   d. **Saved Sessions**: Task name, which can be clicked for remote connection when you use PuTTY next time

      .. _en-us_topic_0017955633__fig74247114018:

      .. figure:: /_static/images/en-us_image_0159943784.png
         :alt: Click to enlarge
         :figclass: imgResize


         **Figure 1** Session

#. Click **Window**. Then, select **UTF-8** for **Received data assumed to be in which character set:** in **Translation**.

#. Click **Open**.

   If you log in to the ECS for the first time, PuTTY displays a security warning dialog box, asking you whether to accept the ECS security certificate. Click **Yes** to save the certificate to your local registry.

#. After the SSH connection to the ECS is set up, enter the username and password as prompted to log in to the ECS.

.. _en-us_topic_0017955633__section20811823174313:

Logging In to the Linux ECS from a Local Linux Server
-----------------------------------------------------

To log in to the Linux ECS from a local Linux server, run the following command:

**ssh** *EIP bound to the ECS*
