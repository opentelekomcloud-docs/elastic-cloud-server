:original_name: en-us_topic_0000001210472883.html

.. _en-us_topic_0000001210472883:

How Can I Install a GUI on an ECS Running Debian?
=================================================

Scenarios
---------

To provide a pure system, the ECSs running Debian do not have a GUI installed by default. You can install a GUI on such ECSs as needed.

Constraints
-----------

-  The operations described in this section apply to ECSs running Debian 8, Debian 9, or Debian 10 only.
-  Before installing a GUI on an ECS, ensure that the memory is no less than 2 GB to prevent GUI installation or ECS startup failures.

Procedure
---------

#. Log in to the ECS and run the following command to update the software library:

   **apt update**

#. Run the following command to upgrade the software library:

   **apt upgrade**

3. Run the following command to install tasksel:

   **apt install tasksel**

4. Run the following command to use tasksel to install the GNOME GUI:

   **tasksel install desktop gnome-desktop**

   The installation takes a long time. Please wait.

5. Run the following command to set the GUI as the default startup target:

   **systemctl set-default graphical.target**

6. .. _en-us_topic_0000001210472883__li162011120159:

   Create a member account.

   After GUI desktop component is installed on the ECS, you cannot log in to the Debian OS as user root **user**. Therefore, you need to add a member account for logging in to the GUI desktop.

   Run the following command to add user **user01**:

   **adduser user01**

   Set a password for **user01** as prompted.

   .. code-block::

      Adding user `user01' ...
      Adding new group `user01' (1001) ...
      Adding new user `user01' (1001) with group `user01' ...
      Creating home directory `/home/user01' ...
      Copying files from `/etc/skel' ...
      New password:
      Retype new password:
      passwd: password updated successfully

   Set information about **user01**. You can press **Enter** to skip the setting. Then the system prompts you to check whether the entered information is correct.

   Enter **Y**.

   .. code-block::

      Changing the user information for user01
      Enter the new value, or press ENTER for the default
              Full Name []:
              Room Number []:
              Work Phone []:
              Home Phone []:
              Other []:
      Is the information correct? [Y/n] Y

7. Run the reboot command to restart the ECS.

8. Log in to the ECS using VNC provided on the management console and log in to the GUI desktop using the member account added in :ref:`6 <en-us_topic_0000001210472883__li162011120159>`.
