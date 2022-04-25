:original_name: en-us_topic_0030932500.html

.. _en-us_topic_0030932500:

Why Are Characters Entered Through VNC Still Incorrect After the Keyboard Language Is Switched?
===============================================================================================

During ECS login using VNC, changing the remote login keyboard language ensures only that characters entered in the VNC window for an ECS are correctly mapped. It does not change the output language of the ECS OS. If characters are not entered correctly, you must log in to the ECS and configure its keyboard output language.

-  For Linux ECSs, perform the following:

Run the following command to load the keyboard mapping file:

**loadkeys keymapfile**

The *keymapfile* parameter indicates the name of the file containing the mappings between the keys and displayed characters.

For example, if the name of a German keyboard mapping file is **de**, run the **loadkeys de** command.

-  For Windows ECSs, switch the input method or open the soft keyboard to enter characters. To open the soft keyboard, perform the following:

#. Click the **Option Menu** icon.
#. Select **Soft Keyboard**.
#. Select a keyboard layout.
