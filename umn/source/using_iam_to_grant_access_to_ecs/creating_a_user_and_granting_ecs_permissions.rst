:original_name: en-us_topic_0170265913.html

.. _en-us_topic_0170265913:

Creating a User and Granting ECS Permissions
============================================

Use `IAM <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__ to implement fine-grained permissions control over your ECSs. With IAM, you can:

-  Create IAM users for personnel based on your enterprise's organizational structure. Each IAM user has their own identity credentials for accessing ECS resources.
-  Grant only the permissions required for users to perform a specific task.
-  Delegate access to other accounts or cloud services for efficient O&M.

If your account does not require individual IAM users, you can skip this section.

This section describes the procedure for granting permissions (see :ref:`Process Flow <en-us_topic_0170265913__section197617372174>`).

Prerequisites
-------------

Before assigning permissions to user groups, you should learn about system-defined policies supported by ECS and select the policies based on service requirements.

For details about system-defined policies supported by ECS, see :ref:`Permissions Management <en-us_topic_0170232209>`.

.. _en-us_topic_0170265913__section197617372174:

Process Flow
------------


.. figure:: /_static/images/en-us_image_0170266394.jpg
   :alt: **Figure 1** Process for granting ECS permissions

   **Figure 1** Process for granting ECS permissions

#. .. _en-us_topic_0170265913__li8447183891715:

   `Create a user group and assign permissions <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0030.html>`__.

   Create a user group on the IAM console and assign the **ECS ReadOnlyAccess** permissions to the group.

#. `Create a user and add the user to the user group <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0031.html>`__.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <en-us_topic_0170265913__li8447183891715>`.

#. `Log in to the management console as the created user <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0032.html>`__.

   In the authorized region, perform the following operations:

   -  Choose **Compute** > **Elastic Cloud Server** in the service list. On the ECS console, click **Create ECS**. If the creation attempt failed, the **ECSReadOnlyAccess** policy has already taken effect.
   -  Choose any service other than ECS in the service list. If a message appears indicating that you have insufficient permissions to access the service, the **ECSReadOnlyAccess** policy has already taken effect.
