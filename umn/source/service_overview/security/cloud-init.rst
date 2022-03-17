Cloud-Init
==========

Cloud-Init is an open-source cloud initialization program, which initializes some of the customized configurations of a newly created ECS, such as the hostname, key pair, and user data.

All standard (Standard_xxx) and enterprise (Enterprise_xxx) images support Cloud-Init. Only certain community images (Community_xxx) do not support it.

Using Cloud-Init to initialize your ECSs will affect your ECS, IMS, and AS services.

Impact on IMS
-------------

To ensure that ECSs created using a private image support customized configurations, you must install Cloud-Init or Cloudbase-Init on the ECSs before using them to create private images.

-  For Windows OSs, download and install Cloudbase-Init.
-  For Linux OSs, download and install Cloud-Init.

After Cloud-Init or Cloudbase-Init is installed in an image, Cloud-Init or Cloudbase-Init automatically configures initial attributes for the ECSs created using this image.

For more information, see *Image Management Service User Guide*.

Impact on ECS
-------------

-  When creating an ECS, if the selected image supports Cloud-Init, you can use the **User Data** function to specify custom configuration, such as ECS login password to the ECS. Such custom settings will take effect upon ECS initialization. `Passing User Data to ECSs <../../instances/obtaining_metadata_and_passing_user_data/passing_user_data_to_ecss.html>`__\ For details, see `Passing User Data to ECSs <../../instances/obtaining_metadata_and_passing_user_data/passing_user_data_to_ecss.html>`__.
-  If Cloud-Init is supported, ECSs do not support password authentication anymore. All newly created ECSs use key pair authentication. This change will influence your ECS logins. For details, see the following sections:

   -  `Login Overview <../../instances/logging_in_to_a_linux_ecs/login_overview.html>`__
   -  `What Is the cloudbase-init Account in Windows ECSs Used for? <../../faqs/passwords_and_key_pairs/what_is_the_cloudbase-init_account_in_windows_ecss_used_for.html>`__
   -  `Why Does the Login to My Linux ECS Using a Key File Fail? <../../faqs/passwords_and_key_pairs/why_does_the_login_to_my_linux_ecs_using_a_key_file_fail.html>`__
   -  `Why Does the System Display a Message Indicating that the Password for Logging In to a Windows ECS Cannot Be Viewed? <../../faqs/login_and_connection/why_does_the_system_display_a_message_indicating_that_the_password_for_logging_in_to_a_windows_ecs_cannot_be_viewed.html>`__

-  If Cloud-Init is supported, you can view and use metadata to configure and manage running ECSs. `Obtaining Metadata <../../instances/obtaining_metadata_and_passing_user_data/obtaining_metadata.html>`__\ For more information, see `Obtaining Metadata <../../instances/obtaining_metadata_and_passing_user_data/obtaining_metadata.html>`__.

Impact on AS
------------

-  When creating an AS configuration, you can use the **User Data** function to specify ECS configurations for initialization. If the AS configuration has taken effect in an AS group, the ECSs newly created in the AS group will automatically initialize their configurations based on the specified ECS configurations.

-  For an existing AS configuration, if its private image does not have Cloud-Init or Cloudbase-Init installed, the login mode of the ECSs created in the AS group where the AS configuration takes effect may fail to take effect.

   To resolve this issue, see "How Does Cloud-Init Affect the AS Service?" in *Auto Scaling User Guide*.

Notes
-----

-  When using Cloud-Init, enable DHCP in the VPC to which the ECS belongs.
-  When using Cloud-Init, ensure that security group rules for the outbound direction meet the following requirements:

   -  **Protocol**: **TCP**
   -  **Port**: **80**
   -  **Destination**: **169.254.0.0/16**

   .. note::

      If you use the default security group rules for the outbound direction, the preceding requirements are met. Then, the metadata can be accessed. Default security group rules for the outbound direction are as follows:

      -  **Protocol**: **All**
      -  **Port**: **All**
      -  **Destination**: **0.0.0.0/0**


