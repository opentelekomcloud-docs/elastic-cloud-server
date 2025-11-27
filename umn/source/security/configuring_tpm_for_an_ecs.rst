:original_name: en-us_topic_0000002424701056.html

.. _en-us_topic_0000002424701056:

Configuring TPM for an ECS
==========================

Scenarios
---------

A Trusted Platform Module (TPM) is a virtual device that complies with the TPM 2.0 specifications. A TPM can be used as the root of trust of an ECS to build a trust chain that covers system boot and user-specified applications and implement remote attestation. In addition, a TPM can securely store tenant identity authentication data, such as passwords, certificates, and encryption keys. A TPM can generate keys and use them for cryptographic functions, such as hashing, signing, encryption, and decryption.

A TPM provides measured boot. During the process, the bootloader and OS create a cryptographic hash for each boot binary file and combine them with the previous values in the Platform Configuration Registers (PCRs) of the TPM. With measured boot, you can obtain signed PCR values from a TPM and use them to prove the integrity of the boot software of an instance to a remote entity. This is called remote attestation.

With a TPM, keys and secrets can be tagged with specific PCR values so that they can never be accessed if the PCR values and instance integrity change. This special form of conditional access is called sealing and unsealing. OS technologies, such as BitLocker, can use a TPM to seal drive decryption keys so that drives can only be decrypted when the OS is correctly booted and in a known good state.

Constraints
-----------

-  If you want to modify the specifications of an ECS booted using an image with TPM enabled, the new specifications must also support TPM.
-  The boot mode of the image with TPM enabled must be UEFI.
-  BitLocker volumes encrypted using TPM keys can only be used on the original instance.
-  The TPM status of an ECS is not displayed in the ECS list.
-  The TPM status is not included in image snapshots.
-  Currently, the following instance types support TPM: Pi5e.

Billing Rules
-------------

There is no additional cost for using TPMs. You only pay for the ECS resources you use.


Configuring TPM for an ECS
--------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. Click **Create ECS**.

#. Set **Trusted Settings** based on service requirements.

   -  To enable TPM, select **TPM**.
   -  To disable TPM, deselect **TPM**.

   For details about how to configure basic, network, and advanced settings when creating an ECS, see :ref:`Overview <en-us_topic_0163572588>`.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000002188678994.png
