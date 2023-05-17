:original_name: en-us_topic_0170316409.html

.. _en-us_topic_0170316409:

Introduction
============

This section describes fine-grained permissions management for your ECSs. If your account does not need individual IAM users, then you may skip over this section.

A policy is a set of permissions defined in JSON format. By default, new IAM users do not have permissions assigned. You need to add a user to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

You can grant users permissions by using roles and policies. Roles are provided by IAM to define service-based permissions depending on user's job responsibilities. Policies define API-based permissions for operations on specific resources under certain conditions, allowing for more fine-grained, secure access control of cloud resources.

For more information about system policies supported by ECS, see "ECS Permissions Management" in *Elastic Cloud Server User Guide*.

.. note::

   Policy-based authorization is useful if you want to allow or deny the access to an API.

An account has all the permissions required to call all APIs, but IAM users must be assigned the required permissions. The permissions required for calling an API are determined by the actions supported by the API. Only users who have been granted permissions allowing the actions can call the API successfully. For example, if an IAM user wants to query ECSs using an API, the user must have been granted permissions that allow the **ecs:servers:list** action.

Supported Actions
-----------------

Operations supported by policies are specific to APIs. The following are common concepts related to policies:

-  Permission: A statement in a policy that allows or denies certain operations.
-  API: REST APIs that can be called by a user who has been granted specific permissions.
-  Action: Specific operations that are allowed or denied.
-  Dependent actions: When assigning an action to users, you also need to assign dependent permissions for that action to take effect.
-  IAM projects or enterprise project: Scope of users a permission is granted to. Policies that contain actions for both IAM and enterprise projects can be used and take effect for both IAM and Enterprise Management. Policies that only contain actions for IAM projects can be used and only take effect for IAM.

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
-  :ref:`Floating IP Address Management <en-us_topic_0103072349>`
-  :ref:`ECS Group Management <en-us_topic_0103071520>`
-  :ref:`ECS Management Through Console <en-us_topic_0184192952>`
-  :ref:`AZ Management <en-us_topic_0103071519>`
-  :ref:`Tag Management <en-us_topic_0103071521>`
