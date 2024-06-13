:original_name: en-us_topic_0170265914.html

.. _en-us_topic_0170265914:

ECS Custom Policies
===================

Custom policies can be created to supplement the system-defined policies of ECS. For the actions that can be added to custom policies, see "Permissions Policies and Supported Actions" in "Elastic Cloud Server API Reference".

You can create custom policies in either of the following ways:

-  Visual editor: Select cloud services, actions, resources, and request conditions. This does not require knowledge of policy syntax.
-  JSON: Edit JSON policies from scratch or based on an existing policy.

For details, see `Creating a Custom Policy <https://docs.otc.t-systems.com/identity-access-management/umn/user_guide/permissions/creating_a_custom_policy.html#iam-01-0016>`__. The following provides examples of common ECS custom policies.

Example Custom Policies
-----------------------

-  Example 1: Only allowing users to start, stop, and restart ECSs in batches

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "ecs:cloudServerFlavors:get",
                      "ecs:cloudServers:reboot",
                      "ecs:cloudServers:start",
                      "ecs:cloudServers:get",
                      "ecs:cloudServers:list",
                      "ecs:cloudServers:stop"
                  ]
              }
          ]
      }

-  Example 2: Only allowing users to stop and delete ECSs in batches

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "ecs:cloudServers:get",
                      "ecs:cloudServers:delete",
                      "ecs:cloudServers:list",
                      "ecs:cloudServers:stop"
                  ]
              }
          ]
      }

-  Example 3: Only allowing VNC login

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "ecs:cloudServerFlavors:get",
                      "ecs:cloudServers:vnc",
                       "ecs:cloudServers:get",
                      "ecs:cloudServers:list"
                   ]
              }
          ]
      }

-  Example 4: Denying ECS deletion

   A policy with only "Deny" permissions must be used in conjunction with other policies to take effect. If the permissions assigned to a user contain both "Allow" and "Deny", the "Deny" permissions take precedence over the "Allow" permissions.

   The following method can be used if you need to assign permissions of the **ECSFullAccess** policy to a user but you want to prevent the user from deleting ECSs. Create a custom policy for denying ECS deletion, and attach both policies to the group to which the user belongs. Then, the user can perform all operations on ECSs except deleting ECSs. The following is an example of a deny policy:

   .. code-block::

      {
            "Version": "1.1",
            "Statement": [
                  {
                "Effect": "Deny",
                        "Action": [
                              "ecs:cloudServers:delete"
                        ]
                  }
            ]
      }
