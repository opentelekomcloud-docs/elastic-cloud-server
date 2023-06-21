:original_name: en-us_topic_0046566932.html

.. _en-us_topic_0046566932:

License Types
=============

Using License from the System
-----------------------------

You can use OS licenses provided by the cloud platform. After creating an ECS with a license authorized, you can use the authorized OS. The platform manages license compliance for you.

BYOL
----

**What Is BYOL?**

Bring your own license (BYOL) allows you to use your existing OS license. In such a case, you do not need to apply for a license again. In BYOL license type, you do not need to pay for the license fee when creating an ECS.

**How to Use BYOL?**

If you select the BYOL license type, you are required to manage licenses by yourself. The cloud platform provides functions for you to maintain license compliance during the license lifecycle. For example, when deploying ECSs on DeHs, you need to manage licenses by yourself. If you have obtained an OS license, you do not need to apply for a license.

The OSs supporting BYOL are as follows:

-  SUSE Linux Enterprise Server
-  Oracle Enterprise Linux
-  Red Hat Enterprise Linux

**Application Scenarios**

The system does not support dynamic license type changing. ECSs support BYOL in the following scenarios:

-  Creating an ECS

   After creating an ECS, you cannot change its license type. If the license type must be changed, reinstall or change the ECS OS.

-  Reinstalling an ECS OS

   When reinstalling an ECS OS, you can set the license type for the ECS.

-  Changing an ECS OS

   When changing an ECS OS, you can set the license type for the ECS.

-  Attaching a system disk

   The license type of a system disk is determined by the ECS license type after the ECS is created, the ECS OS is reinstalled, or the ECS OS is changed. If the system disk is detached and then attached to a new ECS or the original ECS, ensure that the ECS license type is the same as the system disk license type.
