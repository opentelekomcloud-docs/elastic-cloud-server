:original_name: en-us_topic_0170316409.html

.. _en-us_topic_0170316409:

Introduction
============

You can use Identity and Access Management (IAM) for fine-grained permissions management of your ECSs. If your account does not need individual IAM users, you can skip this section.

New IAM users do not have any permissions assigned by default. You need to first add them to one or more groups and attach policies or roles to these groups. The users then inherit permissions from the groups and can perform specified operations on cloud services based on the permissions they have been assigned.

You can grant users permissions by using roles and policies. Roles are provided by IAM to define service-based permissions that match users' job responsibilities. Policies define API-based permissions for operations on specific resources under certain conditions, allowing for more fine-grained, secure access control of cloud resources.

For more information about system-defined policies supported by ECS, see "Permissions Management" in the *Elastic Cloud Server User Guide*.

.. note::

   If you want to allow or deny the access to an API, use policy-based authorization.

Each account has all the permissions required to call all APIs, but IAM users must be assigned the required permissions. The permissions required for calling an API are determined by the actions supported by the API. Only users who have been granted permissions allowing the actions can call the API successfully. For example, if an IAM user wants to query ECSs using an API, the user must have been granted permissions that allow the **ecs:servers:list** action.

Supported Actions
-----------------

ECS provides system-defined policies that can be directly used in IAM. You can also create custom policies to supplement system-defined policies for more refined access control. Operations supported by policies are specific to APIs. The following are common concepts related to policies:

-  Permissions: statements in a policy that allow or deny certain operations
-  APIs: REST APIs that can be called by a user who has been granted specific permissions
-  Actions: specific operations that are allowed or denied
-  Dependencies: actions which a specific action depends on. When allowing an action for a user, you also need to allow any existing action dependencies for that user.
-  IAM projects/Enterprise projects: the authorization scope of a custom policy. A custom policy can be applied to IAM projects or enterprise projects or both. Policies that contain actions for both IAM and enterprise projects can be used and applied for both IAM and Enterprise Management. Policies that contain actions only for IAM projects can be used and applied to IAM only.

.. note::

   Y: supported; x: not supported

ECS supports the following actions that can be defined in custom policies:

-  :ref:`Lifecycle Management <en-us_topic_0103071510>`
-  :ref:`ECS Status Management <en-us_topic_0103071511>`
-  :ref:`Batch Operations <en-us_topic_0184167662>`
-  :ref:`Network Management <en-us_topic_0103072350>`
-  :ref:`Image Management <en-us_topic_0103072348>`
-  :ref:`Security Group Management <en-us_topic_0103072347>`
-  :ref:`Specifications Query <en-us_topic_0103071522>`
-  :ref:`NIC Management <en-us_topic_0103071513>`
-  :ref:`Disk Management <en-us_topic_0103071514>`
-  :ref:`Metadata Management <en-us_topic_0103071516>`
-  :ref:`Tenant Quota Management <en-us_topic_0103071517>`
-  :ref:`SSH Key Management <en-us_topic_0103071515>`
-  :ref:`Password Management <en-us_topic_0161341998>`
-  :ref:`Floating IP Address Management <en-us_topic_0103072349>`
-  :ref:`ECS Group Management <en-us_topic_0103071520>`
-  :ref:`ECS Management Through Console <en-us_topic_0184192952>`
-  :ref:`AZ Management <en-us_topic_0103071519>`
-  :ref:`Tag Management <en-us_topic_0103071521>`
-  :ref:`FPGA Logical File Management <en-us_topic_0132778339>`
