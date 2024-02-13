:original_name: en-us_topic_0047272493.html

.. _en-us_topic_0047272493:

Can All Users Use the Encryption Feature?
=========================================

The permissions of users in a user group to use the encryption feature are as follows:

-  The user who has security administrator permissions can grant KMS access permissions to EVS for using the encryption feature.
-  When a common user who does not have security administrator permissions attempts to use the encryption feature, the condition varies depending on whether the user is the first one in the user group to use this feature.

   -  If the common user is the first one in the user group to use the encryption feature, the common user must request a user who has security administrator permissions to grant the common user permissions. Then, the common user can use the encryption feature.
   -  If the common user is not the first one in the user group to use the encryption feature, the user directly has the permissions to use the encryption feature.

The following section uses a user group as an example to describe how to grant KMS access permissions to EVS for using the encryption feature.

For example, a user group shown in :ref:`Figure 1 <en-us_topic_0047272493__fig10921739155249>` consists of four users, user 1 to user 4. User 1 has security administrator permissions. Users 2, 3, and 4 are common users who do not have security administrator permissions.

.. _en-us_topic_0047272493__fig10921739155249:

.. figure:: /_static/images/en-us_image_0047273062.png
   :alt: **Figure 1** User group

   **Figure 1** User group

Scenario 1: User 1 Uses the Encryption Feature
----------------------------------------------

In this user group, if user 1 uses the encryption feature for the first time, the procedure is as follows:

#. User 1 creates Xrole to grant KMS access permissions to EVS.

   After user 1 grants permissions, the system automatically creates key **evs/default** for encrypting EVS disks.

   .. note::

      When user 1 uses the encryption feature for the first time, the user must grant the KMS access permissions to EVS. Then, all the users in the user group can use the encryption feature by default.

#. User 1 selects a key.

   One of the following keys can be used:

   -  Default key **evs/default**
   -  Custom key, which was created before using the EVS disk encryption feature
   -  Newly created key (For instructions about how to create a key, see "Creating a Key Pair" in *Key Management Service User Guide*.)

After user 1 uses the encryption feature, all other users in the user group can use this feature, without requiring to contact user 1 for permissions granting.

Scenario 2: Common User Uses the Encryption Feature
---------------------------------------------------

In this user group, when user 3 uses the encryption feature for the first time:

#. The system displays a message indicating that the user has no permissions.
#. User 3 asks user 1 to create Xrole to grant KMS access permissions to EVS.

After user 1 grants the permissions, user 3 and all other users in the user group can use the encryption feature by default.
