:original_name: en-us_topic_0000001469584572.html

.. _en-us_topic_0000001469584572:

Configuring Secure Boot for an ECS
==================================

Scenarios
---------

Secure boot is used to check the integrity of each component (driver loader, kernel, and kernel driver) during device startup. This prevents security threats to the system and user data caused by loading and running unauthenticated components.

Secure boot is a feature of the Unified Extensible Firmware Interface (UEFI) that requires all low-level firmware and software components to be verified before being loaded. During the boot process, UEFI secure boot checks the signature of each boot software, including the UEFI firmware driver (or option ROM), Extensible Firmware Interface (EFI) application, OS driver, and binary files. If the signature is valid or recognized by the original equipment manufacturer (OEM), the device will boot, and the firmware will hand over control to the OS.

Secure boot uses key pairs to sign and verify boot devices, ensuring that ECSs only boot software signed by encryption keys. This protects software from threats during the boot process. The secure boot key is stored in the key database of the UEFI non-volatile variable storage.

-  After secure boot is enabled, the system verifies component integrity during system startup, which does not affect services.
-  After secure boot is disabled, the system does not verify component integrity during system startup, which does not affect services.

Background
----------

UEFI is a standard that describes a new type of interface. It enables an OS to automatically load from a pre-boot operating environment to an OS.

The OSs that use the UEFI boot mode support secure boot. Secure boot provides verification of the boot chain status to ensure that only encrypted and verified UEFI binary files are executed after the firmware is initialized. These binary files include UEFI drivers, primary boot loaders, and chain loading components.

By default, secure boot is disabled and the system is in SetupMode. When the system is in SetupMode, all key variables can be updated without a cryptographic signature. After secure boot is enabled, the system exits SetupMode.

.. important::

   After secure boot is enabled, the system enforces signature validation on any UEFI binary files.

Secure boot uses key databases in a chain of trust, as shown in :ref:`Table 1 <en-us_topic_0000001469584572__table5792532133>`. These databases are stored in the UEFI variable storage.

.. _en-us_topic_0000001469584572__table5792532133:

.. table:: **Table 1** Key databases

   +-------------------------------+--------------+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | Key Database                  | Abbreviation | Mandatory   | Description                                                                                                                                                          | Format Constraints                                                    |
   +===============================+==============+=============+======================================================================================================================================================================+=======================================================================+
   | Platform key database         | PK           | Yes         | The PK database is the root of trust for the secure boot instance.                                                                                                   | -  DER, ESL, and AUTH certificate formats are supported.              |
   |                               |              |             |                                                                                                                                                                      | -  Only one certificate is supported.                                 |
   |                               |              |             | The PK database contains a public PK key, which is used in the chain of trust to update the key exchange key (KEK) database.                                         | -  Only X.509 signatures are supported.                               |
   |                               |              |             |                                                                                                                                                                      | -  Certificate digest is not supported.                               |
   |                               |              |             | To change the PK database, you must have the private PK key to sign an update request. This includes deleting the PK database by writing an empty PK key.            |                                                                       |
   +-------------------------------+--------------+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | Key exchange key database     | KEK          | Yes         | The KEK database is a list of public KEK keys used in the chain of trust to update the signature (DB) and the revocation list (DBX) databases.                       | -  DER, ESL, and AUTH certificate formats are supported.              |
   |                               |              |             |                                                                                                                                                                      | -  Only X.509 signatures are supported for ESL and AUTH files.        |
   |                               |              |             | The private KEK is used to add keys to the DB, which is a list of authorized signatures to be booted on the system.                                                  | -  Certificate digest is not supported.                               |
   |                               |              |             |                                                                                                                                                                      |                                                                       |
   |                               |              |             | To change the public KEK database, you must have the private PK key to sign an update request.                                                                       |                                                                       |
   +-------------------------------+--------------+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | Signature database            | DB           | Yes         | The DB database is a list of public keys and hash values used in the chain of trust to verify all UEFI boot binary files.                                            | -  DER, ESL, and AUTH certificate formats are supported.              |
   |                               |              |             |                                                                                                                                                                      | -  Only X.509 signatures are supported for ESL and AUTH files.        |
   |                               |              |             | The DB list contains the authorized keys that are allowed to boot on the system. To modify the list, you must have a private KEK.                                    | -  Certificate digest is not supported.                               |
   |                               |              |             |                                                                                                                                                                      |                                                                       |
   |                               |              |             | To change the DB database, you must have either the private PK key or any of the private KEK keys to sign an update request.                                         |                                                                       |
   +-------------------------------+--------------+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | Forbidden signatures database | DBX          | No          | The DBX database is a list of untrusted public keys and binary hashes used to revoke files in the chain of trust.                                                    | -  ESL and AUTH certificate formats are supported.                    |
   |                               |              |             |                                                                                                                                                                      | -  Only X.509 signatures are supported.                               |
   |                               |              |             | The DBX database always takes precedence over all other key databases.                                                                                               | -  SHA256, SHA384, SHA512, and SM3 certificate digests are supported. |
   |                               |              |             |                                                                                                                                                                      |                                                                       |
   |                               |              |             | To change the DBX database, you must have either the private PK key or any of the private KEK keys to sign an update request.                                        |                                                                       |
   |                               |              |             |                                                                                                                                                                      |                                                                       |
   |                               |              |             | You can obtain a publicly available DBX from the UEFI forum. For details, see `Unified Extensible Firmware Interface Forum <https://uefi.org/revocationlistfile>`__. |                                                                       |
   +-------------------------------+--------------+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | Timestamp signatures database | DBT          | No          | The DBT database retains the signature of the code in the timestamp signature database.                                                                              | -  DER, ESL, and AUTH certificate formats are supported.              |
   |                               |              |             |                                                                                                                                                                      | -  Only X.509 signatures are supported for ESL and AUTH files.        |
   |                               |              |             |                                                                                                                                                                      | -  Certificate digest is not supported.                               |
   +-------------------------------+--------------+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+

Constraints
-----------

-  UEFI secure boot is supported by the following instance flavors: Pi5e, C9, and M9. In the eu-de-01 region, the instance must have at least eight vCPUs.
-  Keys can be imported only when a private image is being created. Keys cannot be imported on the BIOS boot interface of an ECS.
-  Keys or related configurations cannot be imported to an ECS using the mokutil tool.
-  For details about the OSs that support UEFI boot, see `OSs Supporting UEFI Boot Mode <https://docs.otc.t-systems.com/image-management-service/umn/overview/supported_oss/oss_supporting_uefi_boot_mode.html>`__.
-  For Windows, you need to download the corresponding certificate from the OS's official website. For details, see `Keys Required for Secure Boot on all PCs <https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-secure-boot-key-creation-and-management-guidance?view=windows-11#15-keys-required-for-secure-boot-on-all-pcs>`__.

Process Flow
------------


.. figure:: /_static/images/en-us_image_0000001892208774.png
   :alt: **Figure 1** Configuring secure boot for an ECS

   **Figure 1** Configuring secure boot for an ECS

Creating Secure Boot Keys (Linux)
---------------------------------

You need to create keys based on the UEFI secure boot standard, create a certificate for each key, convert each certificate into a UEFI signature list (binary file), and sign each certificate using the related key.

#. **Create a globally unique identifier (GUID).**

   Before creating a key pair, create a GUID for key generation.

   a. :ref:`Connect to an ECS <en-us_topic_0013771089>`.

   b. Create a GUID for key generation.

      .. code-block:: text

         uuidgen --random > GUID.txt

#. **(Mandatory) Create a platform key (PK).**

   A PK is the root of trust for the UEFI secure boot instance.

   a. Create a key and name the variable **PK**.

      .. code-block:: text

         openssl req -newkey rsa:4096 -nodes -keyout PK.key -new -x509 -sha256 -days 3650 -subj "/CN=Platform key/" -out PK.crt

      Parameters in this command are described as follows:

      -  **keyout PK.key**: the private key file
      -  **days 3650**: the certificate validity period
      -  **out PK.crt**: the certificate for creating a UEFI variable
      -  **CN=Platform key**: common name (CN) of the key. You can enter the name of your enterprise instead of the platform key.

   b. Create a certificate.

      .. code-block:: text

         openssl x509 -outform DER -in PK.crt -out PK.cer

   c. Convert the certificate into a UEFI signature list.

      .. code-block:: text

         cert-to-efi-sig-list -g "$(< GUID.txt)" PK.crt PK.esl

   d. Use the private PK to sign the UEFI signature list.

      .. code-block:: text

         sign-efi-sig-list -g "$(< GUID.txt)" -k PK.key -c PK.crt PK PK.esl PK.auth

#. **(Mandatory) Create a key exchange key (KEK).**

   The private KEK is used to add keys to the signature database (DB), which is the list of authorized signatures to boot on the system.

   a. Create a key.

      .. code-block:: text

         openssl req -newkey rsa:4096 -nodes -keyout KEK.key -new -x509 -sha256 -days 3650 -subj "/CN=Key Exchange Key/" -out KEK.crt

   b. Create a certificate.

      .. code-block:: text

         openssl x509 -outform DER -in KEK.crt -out KEK.cer

   c. Convert the certificate into a UEFI signature list.

      .. code-block:: text

         cert-to-efi-sig-list -g "$(< GUID.txt)" KEK.crt KEK.esl

   d. Use the private PK to sign the signature list.

      .. code-block:: text

         sign-efi-sig-list -g "$(< GUID.txt)" -k PK.key -c PK.crt KEK KEK.esl KEK.auth

#. **(Mandatory) Create a signature database (DB).**

   The DB list contains the authorized keys that are allowed to boot on the system. To modify the list, you must have a private KEK.

   Boot images will be signed with the private key that is created in this step.

   a. Create a key.

      .. code-block:: text

         openssl req -newkey rsa:4096 -nodes -keyout db.key -new -x509 -sha256 -days 3650 -subj "/CN=Signature Database key/" -out db.crt

   b. Create a certificate.

      .. code-block:: text

         openssl x509 -outform DER -in db.crt -out db.cer

   c. Convert the certificate into a UEFI signature list.

      .. code-block:: text

         cert-to-efi-sig-list -g "$(< GUID.txt)" db.crt db.esl

   d. Use the private KEK to sign the signature list.

      .. code-block:: text

         sign-efi-sig-list -g "$(< GUID.txt)" -k KEK.key -c KEK.crt db db.esl db.auth

#. **(Optional) Create a forbidden signatures database (DBX).**

   The DBX disables specific DB certificates. It can be a certificate list or a hash list.

#. **(Optional) Create a timestamp signatures database (DBT).**

   The DBT database signs signature timestamps. If the DB certificate is in the DBX and the DBX specifies the revocation time, the DB certificate can be used for signature verification only if the signature time is earlier than the revocation time.

Signing ECS Images Using Keys
-----------------------------

For Ubuntu, sign the kernel file and boot file.

**Preparations**

Install the required package.

.. code-block:: text

   apt install sbsigntool efitools uuid-runtime -y

**Sign the kernel file.**

.. code-block:: text

   mkdir ~/certs
   cd ~/certs
   sudo sbsign --key db.key --cert db.crt --output /boot/vmlinuz-$(uname -r).signed /boot/vmlinuz-$(uname -r)

   # Replace the image file.
   mv /boot/vmlinuz-$(uname -r).signed  /boot/vmlinuz-$(uname -r)

**Sign the boot file.**

.. code-block:: text

   cd ~/certs
   sudo sbsign --key db.key --cert db.crt --output /boot/efi/EFI/ubuntu/grubx64.efi.signed /boot/efi/EFI/ubuntu/grubx64.efi
   sudo sbsign --key db.key --cert db.crt --output /boot/efi/EFI/ubuntu/shimx64.efi.signed /boot/efi/EFI/ubuntu/shimx64.efi
   sudo sbsign --key db.key --cert db.crt --output /boot/efi/EFI/ubuntu/mmx64.efi.signed /boot/efi/EFI/ubuntu/mmx64.efi

   # Replace the original file.
   sudo mv /boot/efi/EFI/ubuntu/grubx64.efi.signed /boot/efi/EFI/ubuntu/grubx64.efi
   sudo mv /boot/efi/EFI/ubuntu/shimx64.efi.signed /boot/efi/EFI/ubuntu/shimx64.efi
   sudo mv /boot/efi/EFI/ubuntu/mmx64.efi.signed /boot/efi/EFI/ubuntu/mmx64.efi

**Replace the files in the BOOT directory.**

.. code-block:: text

   cp /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/BOOT/BOOTX64.EFI
   cp /boot/efi/EFI/ubuntu/grubx64.efi /boot/efi/EFI/BOOT/grubx64.efi
   cp /boot/efi/EFI/ubuntu/mmx64.efi /boot/efi/EFI/BOOT/mmx64.efi

Obtaining a Secure Boot Certificate
-----------------------------------

Contact the image provider to obtain a secure boot certificate.

Transcoding the Secure Boot Certificate
---------------------------------------

-  Platform Key (PK) transcoding

   .. code-block:: text

      __platform_key=$(cat PK.cer | base64 -w 0)

-  Key Exchange Key (KEK) transcoding

   .. code-block:: text

      __key_exchange_key=$(cat KEK.cer | base64 -w 0)

-  Signature Database (DB) transcoding

   .. code-block:: text

      __signature_database=$(cat db.cer | base64 -w 0)

-  Forbidden Signatures Database (DBX) transcoding

   .. code-block:: text

      __forbidden_signatures_database=$(cat dbx.cer | base64 -w 0)

-  Timestamp Signatures Database (DBT) transcoding

   .. code-block:: text

      __timestamp_signatures_database=$(cat dbt.cer | base64 -w 0)

.. caution::

   -  **PK.cer** is the platform key (PK) certificate.
   -  **KEK.cer** is the Key Exchange Key (KEK) certificate.
   -  **db.cer** is the Signature Database (DB) certificate.
   -  **dbx.cer** is the Forbidden Signatures Database (DBX) certificate.
   -  **dbt.cer** is the Timestamp Signatures Database (DBT) certificate.

Creating a Private Image
------------------------

You can create a private image using IMS. For details, see `Introduction <https://docs.otc.t-systems.com/image-management-service/umn/creating_a_private_image/introduction.html>`__.

Updating Secure Boot Image Metadata
-----------------------------------

You can call the following API to update the image metadata:

`Updating an Image <https://docs.otc.t-systems.com/image-management-service/api-ref/ims_apis/image/updating_an_image.html>`__

.. code-block::

   hw_firmware_type=uefi
   __support_secure_boot=true
   __platform_key=${__platform_key}
   __key_exchange_key=${__key_exchange_key}
   __signature_database=${__signature_database}
   __forbidden_signatures_database=${__forbidden_signatures_database}
   __timestamp_signatures_database=${__timestamp_signatures_database}

Enabling Secure Boot for an Image
---------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and project.
#. Choose **Computing** > **Image Management Service** to access the IMS console.
#. Click the **Private Images** tab to show the image list.
#. Locate the row containing the target image and click **Modify** in the **Operation** column.
#. In the displayed dialog box, select the UEFI boot mode.
#. After secure boot is enabled, specify the key databases.
#. Click **OK**.


Configuring Secure Boot for an ECS
----------------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. Click **Create ECS**.

#. Set **Trusted Settings** based on service requirements.

   -  To enable secure boot, select **Secure boot**.
   -  To disable secure boot, deselect **Secure boot**.

   For details about how to configure basic, network, and advanced settings when creating an ECS, see :ref:`Overview <en-us_topic_0163572588>`.

#. Click **OK**.

Follow-up Operations
--------------------

-  (Windows) Check whether UEFI secure boot is enabled.

   #. Open the msinfo32 tool.

   #. Check the **Secure Boot State** field.

      If the value of **Secure Boot State** is **Supported**, UEFI secure boot is enabled.

      |image3|

-  (Linux) Check whether UEFI secure boot is enabled.

   #. Run the following command on the ECS:

      .. code-block:: text

         mokutil --sb

   #. View the command output.

      -  If UEFI secure boot is enabled, the command output contains **SecureBoot enabled**.
      -  If UEFI secure boot is not enabled, the command output contains **SecureBoot disabled** or **Failed to read SecureBoot**.

      |image4|

.. |image1| image:: /_static/images/en-us_image_0000002188678994.png
.. |image2| image:: /_static/images/en-us_image_0000002188678994.png
.. |image3| image:: /_static/images/en-us_image_0000001926866309.png
.. |image4| image:: /_static/images/en-us_image_0000002571311690.png
