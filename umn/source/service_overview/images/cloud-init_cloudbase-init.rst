:original_name: en-us_topic_0048642616.html

.. _en-us_topic_0048642616:

Cloud-Init/Cloudbase-Init
=========================

Cloud-Init or Cloudbase-Init is an open-source cloud program that allows you to configure specific custom details of newly created ECSs (such as the hostname, key pair, and user data) during initialization.

All standard (Standard_xxx) and enterprise (Enterprise_xxx) images support Cloud-Init or Cloudbase-Init. Only certain community images (Community_xxx) do not support it.

Using Cloud-Init or Cloudbase-Init to initialize your ECSs will affect the use of your ECS, IMS, and AS services.

Impact on IMS
-------------

To ensure that ECSs that are created using a private image support custom configurations, you must install Cloud-Init or Cloudbase-Init on the ECSs before using them to create private images.

-  For Windows OSs, download and install Cloudbase-Init.
-  For Linux OSs, download and install Cloud-Init.

Once installed in an image, Cloud-Init or Cloudbase-Init will automatically configure initial attributes for the ECSs when they are created using this image.

For more information, see *Image Management Service User Guide*.

Impact on ECS
-------------

-  When creating an ECS, if the selected image supports Cloud-Init or Cloudbase-Init, you can inject custom information (such as the ECS login password) during the initialization. For details, see :ref:`Injecting User Data <en-us_topic_0032380449>`.
-  After Cloud-Init is supported, ECSs do not support password authentication anymore. All newly created ECSs use key pair authentication. This change will affect your login to ECSs. For details, see the following sections:

   -  :ref:`Login Overview (Linux) <en-us_topic_0013771089>`
   -  :ref:`What Is the Cloudbase-Init Account in Windows ECSs Used for? <en-us_topic_0037633087>`
   -  :ref:`Why Does the Login to My Linux ECS Using a Key File Fail? <en-us_topic_0031734664>`
   -  :ref:`Why Does the System Display a Message Indicating that the Password for Logging In to an ECS Cannot Be Obtained? <en-us_topic_0031736846>`

-  After Cloud-Init or Cloudbase-Init is supported, you can view and use metadata to configure and manage running ECSs. For details, see :ref:`Obtaining ECS Details Using Metadata <en-us_topic_0042400609>`.

Impact on AS
------------

-  When creating an AS configuration, you can use the **User Data** function to specify ECS configurations for initialization. If the AS configuration has taken effect in an AS group, the ECSs newly created in the AS group will automatically initialize their configurations based on the specified ECS configurations.

-  For an existing AS configuration, if its private image does not have Cloud-Init or Cloudbase-Init installed, the login mode of the ECSs created in the AS group where the AS configuration takes effect may fail to take effect.

   To resolve this issue, see "How Does Cloud-Init Affect the AS Service?" in *Auto Scaling User Guide*.

Notes
-----

-  When using Cloud-Init, enable DHCP in the VPC which the ECS belongs to.
-  When using Cloud-Init, ensure that security group rules for the outbound direction meet the following requirements:

   -  Protocol: TCP
   -  Port: 80
   -  Destination: 169.254.0.0/16

   .. note::

      If you use the default security group rules for the outbound direction, the metadata can be accessed because the default rules meet the preceding requirements. For details about the default security group rules for the outbound direction, see :ref:`Security Group <en-us_topic_0030828257__section15617142420109>`.
