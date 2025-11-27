:original_name: en-us_topic_0163572591.html

.. _en-us_topic_0163572591:

Step 3: Configure Advanced Settings
===================================

Advanced Settings
-----------------

#. Set **ECS Name**.

   You can customize the ECS name. Only letters, digits, underscores (_), hyphens (-), and periods (.) are allowed.

   If you want to create multiple ECSs all at one time, the system automatically sequences these ECSs.

   **Allow duplicate name**: allows duplicate ECS names. If you select **Allow duplicate name** and create multiple ECSs in a batch, the created ECSs will have the same name.

   The **ECS Name** set in this step will be the initial hostname in the ECS OS.

   .. note::

      The naming rules of hostnames comply with `RFC 952 <https://tools.ietf.org/html/rfc952>`__ and `RFC 1123 <https://tools.ietf.org/html/rfc1123>`__.

      When you set the ECS name and hostname, you are advised to use letters (a-z), digits (0-9), and hyphens (-) to prevent unknown issues. In the ECS:

      -  Periods (.), hyphens (-), and underscores (_) at the beginning of the name will be ignored.
      -  For periods (.) that are not at the beginning of the name, they and any content following them will be ignored.

#. (Optional) Enter the ECS description.

#. Set **Login Mode**.

   **Key pair**: allows you to use a key pair for login authentication. You can select an existing key pair, or click **Create Key Pair** and create a desired one.

   .. note::

      If you use an existing key pair, make sure that you have saved the key file locally. Otherwise, logging in to the ECS will fail.

#. Set **Cloud Backup and Recovery**.

   Cloud Backup and Recovery (CBR) provides backup protection for EVS disks and ECSs, and uses backups to restore the EVS disks and ECSs. After you set **Cloud Backup and Recovery**, the system associates the ECS with the cloud backup vault and applies the selected backup policy to periodically back up the ECS.

   The following options are provided:

   -  Create new

      a. Enter the name of the cloud backup vault. The name consists of 1 to 64 characters. Only letters, digits, underscores (_), and hyphens (-) are allowed. For example, **vault-f61e**. The default naming rule is **vault\_**\ *xxxx*.
      b. Enter the vault capacity, which is required for backing up the ECS. The vault capacity cannot be smaller than that of the ECS to be backed up. The value range is from the total capacity of the ECS to 10,485,760 in the unit of GiB.
      c. Select a backup policy from the drop-down list, or log in to the CBR console and configure a desired one.

   -  Use existing

      a. Select an existing cloud backup vault from the drop-down list.
      b. Select a backup policy from the drop-down list, or log in to the CBR console and configure a desired one.

   -  Do not use

      Skip this configuration if CBR is not required. If you need to enable CBR after creating an ECS, log in to the CBR console, locate the target vault, and associate it with the ECS.

#. Set **ECS Group (Optional)**.

   An ECS group applies the anti-affinity policy to the ECSs in it so that the ECSs are automatically allocated to different hosts. This configuration is optional. For details, see :ref:`Managing ECS Groups <en-us_topic_0032980085>`.

   .. note::

      An existing ECS attached with a local disk cannot be added to an ECS group. To use ECS group functions, select an ECS group when creating an ECS.

#. To use functions listed in **Advanced Options**, select **Configure now**. Otherwise, do not select it.

   -  User Data

      You can specify the user data. The user data will be automatically passed to the ECS when the ECS starts for the first time. This configuration is optional.

      -  **As text**: allows you to enter the user data in the text box.
      -  **As file**: enables the text to automatically inject a script file or other files into a specified directory on an ECS when you create the ECS.

      For example, if you activate user **root** permission by passing a script file to an ECS, you can log in to the ECS as user **root**.

      For details about how to inject user data, see :ref:`Injecting User Data <en-us_topic_0032380449>`.

   -  Tag

      This configuration is optional. You can tag an ECS to identify and manage your ECS resources easily. A maximum of 10 tags can be added to an ECS.

      .. note::

         Tags added during ECS creation will also be added to the created EIP and EVS disks (including the system disk and data disks) of the ECS. If the ECS uses an existing EIP, the tags will not be added to the EIP.

         After creating the ECS, you can view the tags on the pages providing details about the ECS, EIP, and EVS disks.

      For details about tag operations, see :ref:`Overview <en-us_topic_0092499768>`.

   -  Agency

      This configuration is optional. When your ECS resources need to be shared with other accounts, or your ECS is delegated to professional personnel or team for management, the tenant administrator creates an agency in IAM and grants the ECS management permissions to the personnel or team. The delegated account can log in to the cloud system and switch to your account to manage resources. You do not need to share security credentials (such as passwords) with other accounts, ensuring the security of your account.

      If you have created an agency in IAM, you can select the agency from the drop-down list and obtain specified operation permissions. For instructions about how to create an agency, see *Identity and Access Management User Guide*.

#. Click **Next: Confirm**.
