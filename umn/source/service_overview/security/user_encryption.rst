User Encryption
===============

User encryption allows you to use the encryption feature provided on the public cloud platform to encrypt ECS resources, improving data security. User encryption includes image encryption and EVS disk encryption.

Image Encryption
----------------

Image encryption supports encrypting private images. When creating an ECS, if you select an encrypted image, the system disk of the created ECS is automatically encrypted, improving data security.

Use either of the following methods to create an encrypted image:

-  Use an external image file.
-  Use an existing encrypted ECS.

For more information about image encryption, see *Image Management Service User Guide*.

EVS Disk Encryption
-------------------

EVS disk encryption supports system disk encryption and data disk encryption.

-  When creating an ECS, if you select an encrypted image, the system disk of the created ECS automatically has encryption enabled, and the encryption mode complies with the image encryption mode.
-  When creating an ECS, you can encrypt its system disk.
-  When creating an ECS, you can encrypt added data disks.

For more information about EVS disk encryption, see *Elastic Volume Service User Guide*.

Impact on AS
------------

If you use an encrypted ECS to create an Auto Scaling (AS) configuration, the encryption mode of the created AS configuration complies with the ECS encryption mode.

About Keys
----------

The key used for encryption relies on the Key Management Service (KMS). KMS uses a data encryption key (DEK) to encrypt data and a customer master key (CMK) to encrypt the DEK.

| **Figure 1** Data encryption process
| |image1|

`Table 1 <#EN-US_TOPIC_0046912051__table58453122162120>`__ describes the keys involved in the data encryption process.



.. _EN-US_TOPIC_0046912051__table58453122162120:

.. table:: **Table 1** Keys

   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Name                                  | Description                           | Function                              |
   +=======================================+=======================================+=======================================+
   | DEK                                   | An encryption key that is used for    | Encrypts specific data.               |
   |                                       | encrypting data.                      |                                       |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | CMK                                   | An encryption key created using KMS   | Supports CMK disabling and scheduled  |
   |                                       | for encrypting DEKs.                  | deletion.                             |
   |                                       |                                       |                                       |
   |                                       | A CMK can encrypt multiple DEKs.      |                                       |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Default CMK                           | A master key automatically generated  | -  Supports viewing details of the    |
   |                                       | by the system when you use KMS for    |    default CMK on the KMS console.    |
   |                                       | encryption for the first time.        | -  Does not support CMK disabling or  |
   |                                       |                                       |    scheduled deletion.                |
   |                                       | The name extension of a default CMK   |                                       |
   |                                       | is **/default**, for example,         |                                       |
   |                                       | **evs/default**.                      |                                       |
   +---------------------------------------+---------------------------------------+---------------------------------------+

|image2|

After disabling a CMK or scheduling the deletion of a CMK takes effect, the EVS disk encrypted using this CMK can still be used until the disk is detached from and then attached to an ECS again. During this process, the disk fails to be attached to the ECS because the CMK cannot be obtained. Therefore, the EVS disk becomes unavailable.

For details about KMS, see *Key Management Service User Guide*.


.. |image1| image:: /_static/images/en-us_image_0174076025.png
   :class: vsd

.. |image2| image:: /_static/images/note_3.0-en-us.png
