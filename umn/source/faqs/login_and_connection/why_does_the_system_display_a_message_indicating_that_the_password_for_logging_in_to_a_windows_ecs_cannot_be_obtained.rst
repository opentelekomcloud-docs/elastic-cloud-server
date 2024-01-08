:original_name: en-us_topic_0031736846.html

.. _en-us_topic_0031736846:

Why Does the System Display a Message Indicating that the Password for Logging In to a Windows ECS Cannot Be Obtained?
======================================================================================================================

Symptom
-------

Password authentication is required to log in to a Windows ECS. Therefore, you require a key file to obtain the initial password for logging in to the ECS. However, after you click **Get Password** (see :ref:`Obtaining the Password for Logging In to a Windows ECS <en-us_topic_0031107266>`), the system displays a message indicating that the password could not be obtained, resulting in an ECS login failure.

Possible Causes
---------------

Possible causes vary depending on the image used to create the Windows ECS.

-  Cause 1: The image used to create the Windows ECS is a private image, on which Cloudbase-Init has not been installed.
-  Cause 2: Cloudbase-Init has been installed on the image, but the key pair has not been obtained when the Windows ECS was created.

Solution
--------

-  If the issue is a result of cause 1, proceed as follows:

   If a private image is created without Cloudbase-Init installed, the ECS configuration cannot be customized. As a result, you can log in to the ECS only using the original image password.

   The original image password is the OS password configured when the private image was created.

-  If the issue is a result of cause 2, proceed as follows:

   #. Locate the row containing the target ECS, click **More** in the **Operation** column, and select **Restart**.
   #. Click **More** in the **Operation** column and select **Get Password** to check whether the password can be obtained.

      -  If you can obtain the password, no further action is required.
      -  If you cannot obtain the password, contact customer service.
