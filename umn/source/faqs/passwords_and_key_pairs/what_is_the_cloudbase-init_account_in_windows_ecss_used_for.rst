:original_name: en-us_topic_0037633087.html

.. _en-us_topic_0037633087:

What Is the cloudbase-init Account in Windows ECSs Used for?
============================================================

Description
-----------

In Windows ECSs, **cloudbase-init** is the default account of the Cloudbase-Init agent program. It is used to obtain the metadata and execute configurations when the ECS starts.

.. note::

   This account is unavailable on Linux ECSs.

Do not modify or delete this account or uninstall the Cloudbase-Init agent program. Otherwise, you will be unable to insert data to initialize an ECS created using a Windows private image.

Security Hardening for Randomized **cloudbase-init** Passwords
--------------------------------------------------------------

In Cloudbase-Init 0.9.10, the security of randomized **cloudbase-init** passwords has been hardened to ensure that the hash values (LM-HASH and NTLM-HASH) of the passwords are different.

In Windows, the hash passwords are in the format of "Username:RID:LM-HASH value:NT-HASH value".

For example, in "Administrator:500:C8825DB10F2590EAAAD3B435B51404EE:683020925C5D8569C23AA724774CE9CC:::",

-  Username: **Administrator**
-  RID: **500**
-  LM-HASH value: **C8825DB10F2590EAAAD3B435B51404EE**
-  NT-HASH value: **683020925C5D8569C23AA724774CE9CC**

Use an image to create two ECSs, ecs01 and ecs02. Then, verify that the hash values of the **cloudbase-init** account for the two ECSs are different.

-  LM-HASH and NTLM-HASH values of the **cloudbase-init** account for ecs01


   .. figure:: /_static/images/en-us_image_0202311481.gif
      :alt: **Figure 1** ecs01

      **Figure 1** ecs01

-  LM-HASH and NTLM-HASH values of the **cloudbase-init** account for ecs02


   .. figure:: /_static/images/en-us_image_0202311491.gif
      :alt: **Figure 2** ecs02

      **Figure 2** ecs02
