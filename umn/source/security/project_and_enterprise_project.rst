:original_name: en-us_topic_0206596991.html

.. _en-us_topic_0206596991:

Project and Enterprise Project
==============================

Creating a Project and Assigning Permissions
--------------------------------------------

-  **Creating a project**

   #. Log in to the management console.
   #. Under **Management & Deployment**, click **Identity and Access Management**.
   #. In the navigation pane on the left, choose **Projects**.
   #. On the **Projects** page, click **Create Project**.
   #. Select a region in which you want to create a subproject.
   #. Enter a project name.
   #. Click **OK**.

-  **Granting permissions to user groups based on projects**

   By granting permissions (consisting of resource sets and action sets) to user groups, you associate user groups with an enterprise project. Add users to user groups so that they can inherit user group permissions to precisely control the projects that users can access and the resources that they can operate on. To do so, perform the following operations:

   #. In the navigation pane on the left of the IAM console, choose **User Groups**.

   #. .. _en-us_topic_0206596991__li183611366386:

      On the **User Groups** page of the IAM console, locate the target user group and click **Authorize** in the **Operation** column.

   #. Select policies or roles from the list.

   #. Click **Next** and select **Region-specific projects**.

   #. In the displayed regional project list, select one or more projects and click **OK**.

   #. On the **Users** page, locate the target user and click **Authorize** in the **Operation** column.

   #. Select **Inherit permissions from user groups** and select the user group authorized in :ref:`2 <en-us_topic_0206596991__li183611366386>`.

   #. Click **OK**.

Creating an Enterprise Project and Assigning Permissions
--------------------------------------------------------

-  **Creating an enterprise project**

   #. Log in to the management console.

   #. Choose Management & Deployment > Enterprise Project Service.

   #. On the **Enterprise Project Management Service** page, click **Create Enterprise Project**.

   #. Enter a project name and description, and click **OK**.

      After the enterprise project is created, it is displayed in the enterprise project list.

-  **Associating user groups with an enterprise project and granting permissions**

   By adding user groups to an enterprise project and attaching policies, you associate user groups with the enterprise project. Add users to user groups so that they can inherit user group permissions to precisely control the projects that users can access and the resources that they can operate on. To do so, perform the following operations:

   #. On the **Enterprise Project Management Service** page, click the name of the target enterprise project to go to the enterprise project details page.

   #. On the **Permissions** page, click **Authorize User Group** to associate the enterprise project with a user group and assign permissions to the group.

      For details, see `Creating a User Group and Assigning Permissions <https://docs.otc.t-systems.com/en-us/usermanual/iam/en-us_topic_0046611269.html>`__.

-  **Associating resources with an enterprise project**

   You can use enterprise projects to manage cloud resources.

   -  Select enterprise projects when purchasing ECSs.

      On the page for creating ECSs, select an enterprise project from the **Enterprise Project** drop-down list to associate ECS resources with that enterprise project.

   -  Add ECSs to an enterprise project.

      On the **Enterprise Project Management** page, you can add existing ECSs to an enterprise project.

      The default enterprise project is **default**. Existing resources in your account and resources with no enterprise project designated both reside in the default enterprise project.

      For details, see `Adding Resources to an Enterprise Project <https://docs.otc.t-systems.com/enterprise-project-service/umn/enterprise_project_resource_management/adding_resources_to_an_enterprise_project.html>`__.

For more details, see `Enterprise Management User Guide <https://docs.otc.t-systems.com/en-us/usermanual/em/em_01_0001.html>`__.
