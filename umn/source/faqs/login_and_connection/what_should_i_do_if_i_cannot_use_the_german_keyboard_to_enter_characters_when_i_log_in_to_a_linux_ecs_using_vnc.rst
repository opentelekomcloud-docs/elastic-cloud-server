:original_name: en-us_topic_0030932496.html

.. _en-us_topic_0030932496:

What Should I Do If I Cannot Use the German Keyboard to Enter Characters When I Log In to a Linux ECS Using VNC?
================================================================================================================

Changing the OS Keyboard Language
---------------------------------

Run the following command to change the OS keyboard language:

**loadkeys** *keymapfile*

*keymapfile* is the name of the file for the mapping between keys and displayed characters.

For example, if the name of a German keyboard mapping file is **de**, run the **loadkeys de** command.

For instructions about how to configure the keyboard language for a Linux ECS, see :ref:`Login Using VNC <en-us_topic_0093263550>`.

Procedure
---------

-  For all Linux ECSs, characters **â**, **ê**, **ô**, **û**, and **î** cannot be entered properly. To enter such characters, use either of the following methods:

   Method 1: Press **^+Space+Letter key**.

   Method 2: Click **^°** on the VNC page and then press the suitable key on the keyboard.

-  For all Linux ECSs, characters **²**, **³**, **{**, **[**, **]**, **}**, **\\**, **@**, **€**, **\|**, and **µ** cannot be entered properly. To enter such characters, use the following method:

   Click **AltGr** on the VNC page and then press the suitable key on the physical keyboard.

   An example is provided as follows:

   To obtain character **²**, perform the following operations:

   #. Click **AltGr** on the VNC page.

      This operation is successful if **AltGr** turns red.

   #. On a physical keyboard, press key **2**.

      The system displays special characters **²**.

   #. Click **AltGr** on the VNC page again to cancel the hold-down state.

-  For all Linux ECSs, character **~** cannot be entered properly. To enter such a character, use the following method:

   Click **AltGr** on the VNC page and then press the tilde (~) key on the keyboard twice.

-  For ECSs running CentOS 7, the following characters cannot be entered normally: ^ ´ \`

   To enter these characters, press the key on the keyboard twice and then press **Space**.

-  For ECSs running CentOS 7, when **Caps Lock** is enabled, the following characters cannot be entered normally: Ö Ä Ü

   To enter these characters, hold **Shift** and press the letter key on the keyboard.
