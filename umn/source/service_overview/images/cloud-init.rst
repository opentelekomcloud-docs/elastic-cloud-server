:original_name: en-us_topic_0048642616.html

.. _en-us_topic_0048642616:

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

After being installed in an image, Cloud-Init or Cloudbase-Init automatically configures initial attributes for the ECSs created using this image.

For more information, see *Image Management Service User Guide*.

Impact on ECS
-------------

-  When creating an ECS, if the selected image supports Cloud-Init, you can use the **User Data** function to specify custom configuration, such as ECS login password to the ECS. Such custom settings will take effect upon ECS initialization. For details, see :ref:`Passing User Data to ECSs <en-us_topic_0032380449>`.
-  If Cloud-Init is supported, ECSs do not support password authentication anymore. All newly created ECSs use key pair authentication. This change will influence your ECS logins. For details, see the following sections:

   -  :ref:`Login Overview <en-us_topic_0013771089>`
   -  :ref:`What Is the cloudbase-init Account in Windows ECSs Used for? <en-us_topic_0037633087>`
   -  :ref:`Why Does the Login to My Linux ECS Using a Key File Fail? <en-us_topic_0031734664>`
   -  :ref:`Why Does the System Display a Message Indicating that the Password for Logging In to a Windows ECS Cannot Be Obtained? <en-us_topic_0031736846>`

-  If Cloud-Init is supported, you can view and use metadata to configure and manage running ECSs. For details, see :ref:`Obtaining Metadata <en-us_topic_0042400609>`.

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

      If you use the default security group rules for the outbound direction, the metadata can be accessed because the default rules meet the preceding requirements. Default security group rules for the outbound direction are as follows:

      -  **Protocol**: **All**
      -  **Port**: **All**
      -  **Destination**: **0.0.0.0/0**
