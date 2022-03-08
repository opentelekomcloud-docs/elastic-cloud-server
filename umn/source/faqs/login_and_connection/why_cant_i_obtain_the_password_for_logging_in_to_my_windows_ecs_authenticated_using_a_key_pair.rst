Why Can't I Obtain the Password for Logging In to My Windows ECS Authenticated Using a Key Pair?
================================================================================================

Symptom
-------

A private key cannot be used to obtain the password for logging in to a Windows ECS that is authenticated using a key pair.

Possible Causes
---------------

The password fails to inject using Cloudbase-Init due to:

-  A network fault, leading to the failure of the connection from the ECS to the Cloudbase-Init server.
-  No configuration on the image for Cloudbase-Init to obtain the password.
-  Other reasons.

Solution
--------

If logging in to an ECS with Cloudbase-Init enabled failed, perform the following operations to locate the fault:

#. Ensure that Cloudbase-Init has been correctly configured on the image that was used to create the ECS.

   -  If Cloudbase-Init has not been configured, your ECS will not allow customized configurations, and you can log in to it only by using the original image password.

   -  The ECSs created using a public image have Cloudbase-Init installed by default. Therefore, you do not need to install and configure Cloudbase-Init anymore.

   -  If you created your ECS by using an external image file, install and configure Cloudbase-Init.

      For details, see "Installing and Configuring Cloudbase-Init" in *Image Management Service User Guide*.

2. Ensure that the key pair for logging in to the ECS is correct.

   The key used for obtaining the password must be the key used during the ECS creation.

3. Ensure that DHCP is enabled in the VPC to which the ECS belongs.

   On the management console, check whether DHCP has been enabled in the target subnet.

4. Ensure that the ECS has an EIP bound.

5. Ensure that traffic to and from port 80 is allowed in security group rules.

6. Check Cloudbase-Init logs to identify the cause.

   a. Stop the affected ECS and detach the system disk from it.
   b. Use a public image to create a temporary Windows ECS and attach the system disk detached in `6.a <#EN-US_TOPIC_0081525054__li16969123912115>`__ to the ECS.
   c. Log in to the temporary ECS, open the **Server Manager** page, choose **File and Storage Services** > **Volumes** > **Disks**, right-click the offline disk, and choose **Online** from the shortcut menu.\ **Figure 1** Setting disk online
      |image1|
   d. Switch to the **cloudbase-init** file in **/Program Files/Cloudbase Solution/Cloudbase-Init/log** of this disk to view the log for fault locating.\ **Figure 2** cloudbase-init
      |image2|


.. |image1| image:: /_static/images/en-us_image_0275724694.png
   :class: imgResize

.. |image2| image:: /_static/images/en-us_image_0275726221.png

