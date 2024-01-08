:original_name: en-us_topic_0170232209.html

.. _en-us_topic_0170232209:

Permissions Management
======================

If you need to assign different permissions to employees in your enterprise to access your ECS resources, IAM is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you secure access to your resources.

With IAM, you can use your account to create IAM users, and assign permissions to the users to control their access to specific resources. For example, some software developers in your enterprise need to use ECS resources but should not be allowed to delete the resources or perform any other high-risk operations. In this scenario, you can create IAM users for the software developers and grant them only the permissions required for using ECS resources.

If your account does not need individual IAM users for permissions management, skip this section.

IAM is a free service. You pay only for the resources in your account. For more information about IAM, see `IAM Service Overview <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__.

ECS Permissions
---------------

By default, new IAM users do not have permissions assigned. You need to add a user to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

ECS is a project-level service deployed and accessed in specific physical regions. To assign ECS permissions to a user group, specify the scope as region-specific projects and select projects for the permissions to take effect. If you select **All projects**, the permissions will take effect for user groups in all region-specific projects. When accessing ECS, the users need to switch to a region where they have got permissions to use this service.

You can grant users permissions by using roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. This mechanism provides only a limited number of service-level roles for authorization. When using roles to grant permissions, you need to also assign other roles on which the permissions depend to take effect. However, roles are not an ideal choice for fine-grained authorization and secure access control.

-  Policies: A fine-grained authorization strategy that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization, meeting requirements for secure access control. For example, you can grant ECS users only the permissions for managing a certain type of ECSs.

   Most policies define permissions based on APIs. For the API actions supported by ECS, see "Permissions Policies and Supported Actions" in *Elastic Cloud Server API Reference*.

:ref:`Table 1 <en-us_topic_0170232209__table481412518317>` lists all the system policies supported by ECS.

.. _en-us_topic_0170232209__table481412518317:

.. table:: **Table 1** System-defined policies supported by ECS

   +----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | Policy Name          | Description                                                                                                                                                                              | Type                  | Policy Content                                                                              |
   +======================+==========================================================================================================================================================================================+=======================+=============================================================================================+
   | ECS FullAccess       | Administrator permissions for ECS. Users granted these permissions can perform all operations on ECSs, including creating, deleting, and viewing ECSs, and modifying ECS specifications. | System-defined policy | :ref:`ECS FullAccess Policy Content <en-us_topic_0170232209__section05771626112719>`        |
   +----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | ECS CommonOperations | Common user permissions for ECS. Users granted these permissions can start, stop, restart, and query ECSs.                                                                               | System-defined policy | :ref:`ECS CommonOperations Policy Content <en-us_topic_0170232209__section82501145192816>`  |
   +----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | ECS ReadOnlyAccess   | Read-only permissions for ECS. Users granted these permissions can only view ECS data.                                                                                                   | System-defined policy | :ref:`ECS ReadOnlyAccess Policy Content <en-us_topic_0170232209__section1575124622817>`     |
   +----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | Server Administrator | Full permissions for ECS. This role must be used together with the **Tenant Guest** role in the same project.                                                                            | System role           | :ref:`Server Administrator Policy Content <en-us_topic_0170232209__section134911715123413>` |
   |                      |                                                                                                                                                                                          |                       |                                                                                             |
   |                      | If a user needs to create, delete, or change resources of other services, the user must also be granted administrator permissions of the corresponding services in the same project.     |                       |                                                                                             |
   |                      |                                                                                                                                                                                          |                       |                                                                                             |
   |                      | For example, if a user needs to create a new VPC when creating an ECS, the user must also be granted permissions with the **VPC Administrator** role.                                    |                       |                                                                                             |
   +----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+

:ref:`Table 2 <en-us_topic_0170232209__table470371811355>` lists the common operations supported by each system-defined policy of ECS. Select the policies as required.

.. _en-us_topic_0170232209__table470371811355:

.. table:: **Table 2** Common operations supported by each system-defined policy

   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Operation                                               | ECS FullAccess | ECS CommonOperations | ECS ReadOnlyAccess                      |
   +=========================================================+================+======================+=========================================+
   | Creating an ECS                                         | Supported      | Not supported        | Not supported                           |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Remotely logging in to an ECS on the management console | Supported      | Supported            | Not supported (VNC login not supported) |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Querying an ECS list                                    | Supported      | Supported            | Supported                               |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Querying ECS details                                    | Supported      | Supported            | Supported                               |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Modifying ECS details                                   | Supported      | Not supported        | Not supported                           |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Starting an ECS                                         | Supported      | Supported            | Not supported                           |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Stopping an ECS                                         | Supported      | Supported            | Not supported                           |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Restarting an ECS                                       | Supported      | Supported            | Not supported                           |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Deleting an ECS                                         | Supported      | Not supported        | Not supported                           |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Reinstalling an ECS OS                                  | Supported      | Not supported        | Not supported                           |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Changing an ECS OS                                      | Supported      | Not supported        | Not supported                           |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Attaching a disk to an ECS                              | Supported      | Not supported        | Not supported                           |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Detaching a disk from an ECS                            | Supported      | Not supported        | Not supported                           |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Querying a disk list                                    | Supported      | Supported            | Supported                               |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Attaching a NIC to an ECS                               | Supported      | Not supported        | Not supported                           |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Detaching a NIC from an ECS                             | Supported      | Not supported        | Not supported                           |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Querying a NIC list                                     | Supported      | Supported            | Supported                               |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Adding tags to an ECS                                   | Supported      | Supported            | Not supported                           |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Modifying ECS specifications                            | Supported      | Not supported        | Not supported                           |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Querying the ECS flavor list                            | Supported      | Supported            | Supported                               |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+
   | Querying ECS groups                                     | Supported      | Supported            | Supported                               |
   +---------------------------------------------------------+----------------+----------------------+-----------------------------------------+

Helpful Links
-------------

-  `IAM Service Overview <https://docs.otc.t-systems.com/identity-access-management/umn/service_overview/what_is_iam.html>`__
-  :ref:`Creating a User and Granting ECS Permissions <en-us_topic_0170265913>`
-  Permissions Policies and Supported Actions in *Elastic Cloud Server API Reference*

.. _en-us_topic_0170232209__section05771626112719:

ECS FullAccess Policy Content
-----------------------------

.. code-block::

   {
           "Version": "1.1",
           "Statement": [
                   {
                           "Effect": "Allow",
                           "Action": [
                                   "ecs:*:*",
                                   "evs:*:get",
                                   "evs:*:list",
                                   "evs:volumes:create",
                                   "evs:volumes:delete",
                                   "evs:volumes:attach",
                                   "evs:volumes:detach",
                                   "evs:volumes:manage",
                                   "evs:volumes:update",
                                   "evs:volumes:use",
                                   "evs:volumes:uploadImage",
                                   "evs:snapshots:create",
                                   "vpc:*:get",
                                   "vpc:*:list",
                                   "vpc:networks:create",
                                   "vpc:networks:update",
                                   "vpc:subnets:update",
                                   "vpc:subnets:create",
                                   "vpc:ports:*",
                                   "vpc:routers:get",
                                   "vpc:routers:update",
                                   "vpc:securityGroups:*",
                                   "vpc:securityGroupRules:*",
                                   "vpc:floatingIps:*",
                                   "vpc:publicIps:*",
                                   "ims:images:create",
                                   "ims:images:delete",
                                   "ims:images:get",
                                   "ims:images:list",
                                   "ims:images:update",
                                   "ims:images:upload"
                           ]
                   }
           ]
   }

.. _en-us_topic_0170232209__section82501145192816:

ECS CommonOperations Policy Content
-----------------------------------

.. code-block::

   {
           "Version": "1.1",
           "Statement": [
                   {
                           "Effect": "Allow",
                           "Action": [
                                   "ecs:*:get*",
                                   "ecs:*:list*",
                                   "ecs:*:start",
                                   "ecs:*:stop",
                                   "ecs:*:reboot",
                                   "ecs:blockDevice:use",
                                   "ecs:cloudServerFpgaImages:relate",
                                   "ecs:cloudServerFpgaImages:register",
                                   "ecs:cloudServerFpgaImages:delete",
                                   "ecs:cloudServerFpgaImags:unrelate",
                                   "ecs:cloudServers:setAutoRecovery",
                                   "ecs:cloudServerPasswords:reset",
                                   "ecs:cloudServerPorts:modify",
                                   "ecs:cloudServers:vnc",
                                   "ecs:diskConfigs:use",
                                   "ecs:securityGroups:use",
                                   "ecs:serverGroups:manage",
                                   "ecs:serverFloatingIps:use",
                                   "ecs:serverKeypairs:*",
                                   "ecs:serverPasswords:manage",
                                   "ecs:servers:createConsole",
                                   "ecs:servers:createImage",
                                   "ecs:servers:setMetadata",
                                   "ecs:servers:setTags",
                                   "ecs:serverVolumes:use",
                                   "evs:*:get*",
                                   "evs:*:list*",
                                   "evs:snapshots:create",
                                   "evs:volumes:uploadImage",
                                   "evs:volumes:delete",
                                   "evs:volumes:update",
                                   "evs:volumes:attach",
                                   "evs:volumes:detach",
                                   "evs:volumes:manage",
                                   "evs:volumes:use",
                                   "vpc:*:get*",
                                   "vpc:*:list*",
                                   "vpc:floatingIps:create",
                                   "vpc:floatingIps:update",
                                   "vpc:floatingIps:delete",
                                   "vpc:publicIps:update",
                                   "vpc:publicIps:delete",
                                   "ims:images:create",
                                   "ims:images:delete",
                                   "ims:images:get",
                                   "ims:images:list",
                                   "ims:images:update",
                                   "ims:images:upload"
                           ]
                   }
           ]
   }

.. _en-us_topic_0170232209__section1575124622817:

ECS ReadOnlyAccess Policy Content
---------------------------------

.. code-block::

   {
           "Version": "1.1",
           "Statement": [
                   {
                           "Effect": "Allow",
                           "Action": [
                                   "ecs:*:get*",
                                   "ecs:*:list*",
                                   "ecs:serverGroups:manage",
                                   "ecs:serverVolumes:use",
                                   "evs:*:get*",
                                   "evs:*:list*",
                                   "vpc:*:get*",
                                   "vpc:*:list*",
                                   "ims:*:get*",
                                   "ims:*:list*"
                           ]
                   }
           ]
   }

.. _en-us_topic_0170232209__section134911715123413:

Server Administrator Policy Content
-----------------------------------

.. code-block::

   {
       "Version": "1.1",
       "Statement": [
           {
               "Action": [
                   "ecs:*:*",
                   "evs:*:get",
                   "evs:*:list",
                   "evs:volumes:create",
                   "evs:volumes:delete",
                   "evs:volumes:attach",
                   "evs:volumes:detach",
                   "evs:volumes:manage",
                   "evs:volumes:update",
                   "evs:volumes:uploadImage",
                   "evs:snapshots:create",
                   "vpc:*:get",
                   "vpc:*:list",
                   "vpc:networks:create",
                   "vpc:networks:update",
                   "vpc:subnets:update",
                   "vpc:subnets:create",
                   "vpc:routers:get",
                   "vpc:routers:update",
                   "vpc:ports:*",
                   "vpc:privateIps:*",
                   "vpc:securityGroups:*",
                   "vpc:securityGroupRules:*",
                   "vpc:floatingIps:*",
                   "vpc:publicIps:*",
                   "vpc:bandwidths:*",
                   "vpc:firewalls:*",
                   "ims:images:create",
                   "ims:images:delete",
                   "ims:images:get",
                   "ims:images:list",
                   "ims:images:update",
                   "ims:images:upload"
               ],
               "Effect": "Allow"
           }
       ]
   }
