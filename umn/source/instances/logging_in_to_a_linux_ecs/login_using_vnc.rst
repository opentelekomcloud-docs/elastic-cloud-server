Login Using VNC
===============

Scenarios
---------

This section describes how to use VNC provided on the management console to log in to an ECS. This function applies to emergency O&M. In other scenarios, you are advised to log in to ECSs using SSH or MSTSC.

For instructions about how to copy and paste data on VNC pages after the ECS login, see `Follow-up Procedure <#follow-up-procedure>`__.

.. note::

   Before using remote login (VNC) provided on the management console to log in to a Linux ECS authenticated using a key pair, log in to the ECS `using an SSH key <../../instances/logging_in_to_a_linux_ecs/login_using_an_ssh_key.html>`__ and set a login password.

Constraints
-----------

-  The remote login function is implemented using customized ports. Therefore, before attempting to log in remotely, ensure that the port to be used is not blocked by the firewall. For example, if the remote login link is xxx:8002, ensure that port 8002 is not blocked by the firewall.
-  If the client OS uses a local proxy and the firewall port cannot be configured on the local proxy, disable the proxy mode and then try logging in remotely.

Login Notes
-----------

#. When you log in to the ECS using VNC, four types of keyboards will be used, as described in `Table 1 <#enustopic0093263550enustopic0027268511enustopic0039525621table10692372181721>`__. 

.. _ENUSTOPIC0093263550enustopic0027268511enustopic0039525621table10692372181721:

   .. table:: **Table 1** Keyboard types

      +---------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Keyboard Type                         | Description                                                                                                                                                                                                                                                                                 | Keyboard Language                                                                                                                                                                                                                                                                      |
      +=======================================+=============================================================================================================================================================================================================================================================================================+========================================================================================================================================================================================================================================================================================+
      | Physical keyboard                     | Used by the terminal and allows terminal data input.                                                                                                                                                                                                                                        | Selected by users locally.                                                                                                                                                                                                                                                             |
      +---------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Input method keyboard on the terminal | Used for logging in to the management console from a terminal, such as a computer. The keyboard input method of the terminal must comply with the physical keyboard language type. In this way, the entered data can be correctly transferred from the physical keyboard to the VNC client. | Selected by users locally.                                                                                                                                                                                                                                                             |
      +---------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | VNC keyboard                          | Used for VNC logins. The VNC keyboard input method must comply with the physical keyboard language type. In this way, the entered data can be correctly transferred from the VNC client to the ECS OS.                                                                                      | Can be configured through the management console.                                                                                                                                                                                                                                      |
      |                                       |                                                                                                                                                                                                                                                                                             |                                                                                                                                                                                                                                                                                        |
      |                                       | .. note::                                                                                                                                                                                                                                                                                   | For instructions about how to select a VNC keyboard language, see `Logging In to an ECS Using an English Keyboard <#logging-in-to-an-ecs-using-an-english-keyboard>`__ and `Logging In to an ECS Using a Non-English Keyboard <#logging-in-to-an-ecs-using-a-non-english-keyboard>`__. |
      |                                       |                                                                                                                                                                                                                                                                                             |                                                                                                                                                                                                                                                                                        |
      |                                       |    The English keyboard is used by default. The system also supports other keyboard languages.                                                                                                                                                                                              |                                                                                                                                                                                                                                                                                        |
      +---------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ECS OS keyboard                       | Input method keyboard configured in the ECS OS. Ensure that this input method complies with the physical keyboard language type for correct response to the entered data transferred from the VNC client.                                                                                   | Configured by users locally.                                                                                                                                                                                                                                                           |
      |                                       |                                                                                                                                                                                                                                                                                             |                                                                                                                                                                                                                                                                                        |
      |                                       | .. note::                                                                                                                                                                                                                                                                                   | For instructions about how to change an ECS OS keyboard language, see `Changing the OS Keyboard Language <#changing-the-os-keyboard-language>`__.                                                                                                                                      |
      |                                       |                                                                                                                                                                                                                                                                                             |                                                                                                                                                                                                                                                                                        |
      |                                       |    -  The default OS keyboard language of an ECS created using a public image is English. For additional information, see `Public Images Introduction <https://docs.otc.t-systems.com/en-us/ims/index.html>`__.                                                                             |                                                                                                                                                                                                                                                                                        |
      |                                       |    -  The OS keyboard language of an ECS created using a private image is customized.                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                        |
      +---------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. When you log in to the ECS using VNC, ensure that your configured keyboard language is correct.

   The entered data is as expected only if the input method keyboard on the terminal, the VNC keyboard, and the ECS OS keyboard languages are the same as the physical keyboard language. For details about language configuration in the four types of keyboards, see `Table 2 <#enustopic0093263550enustopic0027268511enustopic0039525621table31240733181814>`__. 

.. _ENUSTOPIC0093263550enustopic0027268511enustopic0039525621table31240733181814:

   .. table:: **Table 2** Language configuration in the four types of keyboards

      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      | Physical Keyboard | Input Method Keyboard on the Terminal | VNC Keyboard | ECS OS Keyboard | Supported or Not |
      +===================+=======================================+==============+=================+==================+
      | English           | English                               | English      | English         | Yes              |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      |                   |                                       |              | German          | No               |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      |                   |                                       | German       | English         | No               |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      |                   |                                       |              | German          | No               |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      |                   | German                                | English      | English         | No               |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      |                   |                                       |              | German          | No               |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      |                   |                                       | German       | English         | No               |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      |                   |                                       |              | German          | No               |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      | German            | English                               | English      | English         | No               |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      |                   |                                       |              | German          | No               |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      |                   |                                       | German       | English         | No               |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      |                   |                                       |              | German          | No               |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      |                   | German                                | English      | English         | No               |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      |                   |                                       |              | German          | No               |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      |                   |                                       | German       | English         | No               |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+
      |                   |                                       |              | German          | Yes              |
      +-------------------+---------------------------------------+--------------+-----------------+------------------+

#. If the password used when you create the ECS is entered using the English keyboard, you must use the English keyboard to enter the password when logging in to the ECS later.

Logging In to an ECS Using an English Keyboard
----------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the search box above the upper right corner of the ECS list, enter the ECS name and click |image2| for search.

#. Locate the row containing the ECS and click **Remote Login** in the **Operation** column.

#. In the displayed **Configure Keyboard Layout for Remote Login** dialog box, select the English keyboard.

   .. figure:: /_static/images/en-us_image_0030874270.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 1** Keyboard layout configuration

#. Click **Remote Login**.

#. (Optional) If you have changed the system language, in the dialog box that is displayed, click **Start Remote Login**.

   .. figure:: /_static/images/en-us_image_0030874271.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 2** Remote Login

#. (Optional) When the system displays "Press CTRL+ALT+DELETE to log on", click **Send CtrlAltDel** in the upper part of the remote login page to log in to the ECS.

   .. figure:: /_static/images/en-us_image_0201100229.png
      :alt: **Figure 3** Send CtrlAltDel
   

      **Figure 3** Send CtrlAltDel

#. (Optional) If you need your cursor to be displayed on the remote login page, click **Local Cursor**.

   .. figure:: /_static/images/en-us_image_0093469181.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 4** Local Cursor

#. Enter the ECS password as prompted.

Logging In to an ECS Using a Non-English Keyboard
-------------------------------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the search box above the upper right corner of the ECS list, enter the ECS name, IP address, or ID, and click |image4| for search.

#. Locate the row containing the ECS and click **Remote Login** in the **Operation** column.

#. In the displayed **Configure Keyboard Layout for Remote Login** dialog box, select the English keyboard.

   .. figure:: /_static/images/en-us_image_0030874270.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 5** Keyboard layout configuration

7.  Click **Remote Login**.

8.  (Optional) If you have changed the system language, in the dialog box that is displayed, click **Start Remote Login**.

    .. figure:: /_static/images/en-us_image_0030874271.png
       :alt: Click to enlarge
       :figclass: imgResize
    

       **Figure 6** Remote Login

9.  (Optional) When the system displays "Press CTRL+ALT+DELETE to log on", click **Send CtrlAltDel** in the upper part of the remote login page to log in to the ECS.

    .. figure:: /_static/images/en-us_image_0201103161.png
       :alt: **Figure 7** Send CtrlAltDel
    

       **Figure 7** Send CtrlAltDel

10. (Optional) If you need your cursor to be displayed on the remote login page, click **Local Cursor**.

    .. figure:: /_static/images/en-us_image_0093469181.png
       :alt: Click to enlarge
       :figclass: imgResize
    

       **Figure 8** Local Cursor

11. Enter the ECS password as prompted.

    -  When logging in to the ECS using VNC for the first time, use the English keyboard to enter the password. After you have logged in to the ECS, see `Changing the OS Keyboard Language <#changing-the-os-keyboard-language>`__ to change the keyboard language of the ECS OS. You can then select the keyboard language and enter the password the next time you log in.
    -  If you have changed the keyboard language of the ECS OS, ensure that the keyboard language in use, the keyboard language selected in step `6 <#enustopic0093263550enustopic0027268511li17715715111459>`__, and the changed OS keyboard language are all the same.

Changing the OS Keyboard Language
---------------------------------

If the ECS is running Linux, run the following command:

**loadkeys** *keymapfile*

The *keymapfile* parameter indicates the name of the file containing the mappings between the keys and displayed characters.

For example, if the name of a German keyboard mapping file is **de**, run the **loadkeys de** command.

Configuration Example
---------------------

**Scenarios**

If you attempt to log in to an ECS created using a public image for the first time, the languages of the four types of keyboards before the configuration are as follows (**Before configuration** row in `Table 3 <#enustopic0093263550enustopic0027268511enustopic0039525621table18256759113132>`__):

-  Physical keyboard: German
-  Input method keyboard on the terminal: English
-  VNC keyboard: English
-  ECS OS keyboard: English

In this case, you must change the languages of the other three types of keyboards to the same language as the physical keyboard for expected data entering. For details, see the **Solution 1** row in `Table 3 <#enustopic0093263550enustopic0027268511enustopic0039525621table18256759113132>`__.



.. _ENUSTOPIC0093263550enustopic0027268511enustopic0039525621table18256759113132:

.. table:: **Table 3** Languages in the four types of keyboards

   +----------------------+-------------------+---------------------------------------+--------------+-----------------+
   | -                    | Physical Keyboard | Input Method Keyboard on the Terminal | VNC Keyboard | ECS OS Keyboard |
   +======================+===================+=======================================+==============+=================+
   | Before configuration | German            | English                               | English      | English         |
   +----------------------+-------------------+---------------------------------------+--------------+-----------------+
   | Solution 1           | German            | German                                | German       | German          |
   +----------------------+-------------------+---------------------------------------+--------------+-----------------+
   | Solution 2           | English           | English                               | English      | English         |
   +----------------------+-------------------+---------------------------------------+--------------+-----------------+

**Procedure**

#. Locally configure the language, for example, German, in the input method keyboard on the terminal.

#. Set the VNC keyboard language to English.

   .. note::

      When you log in to the ECS using VNC for the first time, the default ECS OS keyboard language is English. Therefore, you must set the VNC keyboard language to English.

#. Log in to the ECS and change the ECS OS language to German.

   For details, see `Changing the OS Keyboard Language <#changing-the-os-keyboard-language>`__.

#. Change the VNC keyboard language to German.

   For details, see `Logging In to an ECS Using a Non-English Keyboard <#logging-in-to-an-ecs-using-a-non-english-keyboard>`__.

To set the languages on the four types of keyboards to all be the same, perform `1 <#enustopic0093263550enustopic0027268511enustopic0039525621li55865773114331>`__ to `4 <#enustopic0093263550enustopic0027268511enustopic0039525621li62706781115148>`__.

.. note::

   During the configuration, if English characters cannot be entered using the current physical keyboard, use the English soft keyboard to modify the configuration described in the **Solution 2** row of `Table 3 <#enustopic0093263550enustopic0027268511enustopic0039525621table18256759113132>`__. In such a case, you only need to use the English soft keyboard to enter characters.

   -  To enable the Windows English soft keyboard, choose **Start** > **Run**, enter **osk**, and press **Enter**.
   -  The method of enabling the Linux English soft keyboard varies depending on the OS version and is not described in this document.

Follow-up Procedure
-------------------

Local commands can be copied to an ECS. To do so, perform the following operations:

#. Log in to the ECS using VNC.

#. Click **Input Commands** in the upper right corner of the page.

   .. figure:: /_static/images/en-us_image_0109039483.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 9** Input Commands

#. Press **Ctrl+C** to copy data from the local computer.

#. Press **Ctrl+V** to paste the local data to the **Copy Commands** window.

#. Click **Send**.

   Send the copied data to the CLI.

.. note::

   There is a low probability that data is lost when you use Input Commands on the VNC page of a GUI-based Linux ECS. This is because the number of ECS vCPUs fails to meet GUI requirements. In such a case, it is a good practice to send a maximum of 5 characters at a time or switch from GUI to CLI (also called text interface), and then use the command input function.

Helpful Links
-------------

For FAQs about VNC-based ECS logins, see the following links:

-  `What Browser Version Is Required to Remotely Log In to an ECS? <../../faqs/login_and_connection/what_browser_version_is_required_to_remotely_log_in_to_an_ecs.html>`__
-  `What Should I Do If I Cannot Use the German Keyboard to Enter Characters When I Log In to a Linux ECS Using VNC? <../../faqs/login_and_connection/what_should_i_do_if_i_cannot_use_the_german_keyboard_to_enter_characters_when_i_log_in_to_a_linux_ecs_using_vnc.html>`__
-  `Why Cannot I Use the MAC Keyboard to Enter Lowercase Characters When I Log In to an ECS Using VNC? <../../faqs/login_and_connection/why_cannot_i_use_the_mac_keyboard_to_enter_lowercase_characters_when_i_log_in_to_an_ecs_using_vnc.html>`__
-  `What Should I Do If the Page Does not Respond After I Log In to an ECS Using VNC and Do Not Perform Any Operation for a Long Period of Time? <../../faqs/login_and_connection/what_should_i_do_if_the_page_does_not_respond_after_i_log_in_to_an_ecs_using_vnc_and_do_not_perform_any_operation_for_a_long_period_of_time.html>`__
-  `What Should I Do If I Cannot View Data After Logging In to an ECS Using VNC? <../../faqs/login_and_connection/what_should_i_do_if_i_cannot_view_data_after_logging_in_to_an_ecs_using_vnc.html>`__
-  `Why Are Characters Entered Through VNC Still Incorrect After the Keyboard Language Is Switched? <../../faqs/login_and_connection/why_are_characters_entered_through_vnc_still_incorrect_after_the_keyboard_language_is_switched.html>`__
-  `Why Does a Blank Screen Appear While the System Displays a Message Indicating Successful Authentication After I Attempted to Log In to an ECS Using VNC? <../../faqs/login_and_connection/why_does_a_blank_screen_appear_while_the_system_displays_a_message_indicating_successful_authentication_after_i_attempted_to_log_in_to_an_ecs_using_vnc.html>`__



.. |image1| image:: /_static/images/en-us_image_0210779229.png

.. |image2| image:: /_static/images/en-us_image_0128851444.png

.. |image3| image:: /_static/images/en-us_image_0210779229.png

.. |image4| image:: /_static/images/en-us_image_0128851405.png

