:original_name: en-us_topic_0163572591.html

.. _en-us_topic_0163572591:

Step 3: Configure Advanced Settings
===================================

Advanced Settings
-----------------

#. Set **ECS Name**.

   The name can be customized but can contain only letters, digits, underscores (_), hyphens (-), and periods (.).

   If you want to create multiple ECSs at a time, the system automatically sequences these ECSs.

   **Allow duplicate name**: allows ECS names to be duplicate. If you select **Allow duplicate name** and create multiple ECSs in a batch, the created ECSs will have the same name.

   The **ECS Name** set in this step will be the initial host name in the ECS OS.

   .. note::

      Consecutive periods (.) or hyphens (-) will be replaced with the first character to prevent unknown issues.

#. (Optional) Specify the description of the ECS.

#. Set **Login Mode**.

   **Key pair**: allows you to use a key pair for login authentication. You can select an existing key pair, or click **Create Key Pair** and create a desired one.

   .. note::

      If you use an existing key pair, make sure that you have saved the key file locally. Otherwise, logging in to the ECS will fail.

#. Set **ECS Group (Optional)**.

   An ECS group applies the anti-affinity policy to the ECSs in it so that the ECSs are automatically allocated to different hosts. This configuration is optional. For instructions about how to create an ECS group, see :ref:`Managing ECS Groups <en-us_topic_0032980085>`.

   .. note::

      An existing ECS attached with a local disk cannot be added to an ECS group. To use ECS group functions, select an ECS group when creating an ECS.

#. To use functions listed in **Advanced Options**, select **Configure now**. Otherwise, do not select it.

   -  User Data Injection

      You can specify the user data. The user data will be automatically passed to the ECS when the ECS starts for the first time. This configuration is optional.

      -  **As text**: allows you to enter the user data in the text box.
      -  **As file**: enables the text to automatically inject a script file or other files into a specified directory on an ECS when you create the ECS.

      For example, if you activate user **root** permission by passing a script file to an ECS, you can log in to the ECS as user **root**.

      For detailed operations, see :ref:`Passing User Data to ECSs <en-us_topic_0032380449>`.

   -  Tag

      This configuration is optional. You can tag an ECS to facilitate identification and management. You can add up to 10 tags to an ECS.

      .. note::

         Tags added during ECS creation will also be added to the created EIP and EVS disks (including the system disk and data disks) of the ECS. If the ECS uses an existing EIP, the tags will not be added to the EIP.

         After creating the ECS, you can view the tags on the pages providing details about the ECS, EIP, and EVS disks.

      For details, see :ref:`Overview <en-us_topic_0092499768>`.

   -  Agency

      This configuration is optional. When your ECS resources need to be shared with other accounts, or your ECS is delegated to professional personnel or team for management, the tenant administrator creates an agency in IAM and grants the ECS management permissions to the personnel or team. The delegated account can log in to the cloud system and switch to your account to manage resources. You do not need to share security credentials (such as passwords) with other accounts, ensuring the security of your account.

      If you have created an agency in IAM, you can select the agency from the drop-down list and obtain specified operation permissions. For instructions about how to create an agency, see *Identity and Access Management User Guide*.

#. Click **Next: Confirm**.
