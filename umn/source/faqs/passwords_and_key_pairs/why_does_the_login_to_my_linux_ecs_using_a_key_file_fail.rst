:original_name: en-us_topic_0031734664.html

.. _en-us_topic_0031734664:

Why Does the Login to My Linux ECS Using a Key File Fail?
=========================================================

Symptom
-------

When you use the key file created during your Linux ECS creation to log in to the ECS, the login fails.

Possible Causes
---------------

Possible causes vary depending on the image used to create the Linux ECS.

-  Cause 1: The image that you used to create the Linux ECS is a private image, on which Cloud-Init is not installed.
-  Cause 2: Cloud-Init is installed on the image, but you did not obtain the key pair when you created the ECS.

Solution
--------

-  If the issue is a result of cause 1, proceed as follows:

   If you created a private image without installing Cloud-Init, you cannot customize the ECS configuration. As a result, you can log in to the ECS only using the original image password or key pair.

   The original image password or key pair is the OS password or key pair you configured when you created the private image.

-  If the issue is a result of cause 2, proceed as follows:

   #. Locate the row containing the target ECS, click **More** in the **Operation** column, and select **Restart**.
   #. Use the key file to log in to the ECS again and check whether the login is successful.

      -  If the login is successful, no further action is required.
      -  If the login fails, contact customer service for technical support.
