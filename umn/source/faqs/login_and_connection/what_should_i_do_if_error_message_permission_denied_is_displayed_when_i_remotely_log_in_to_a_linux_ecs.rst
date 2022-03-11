What Should I Do If Error Message "Permission denied" Is Displayed When I Remotely Log In to a Linux ECS?
=========================================================================================================

Symptom
-------

When I attempted to remotely log in to a Linux ECS, the system displayed error Message "Permission denied".

| **Figure 1** Permission denied
| |image1| |image2|

-  To resolve this issue, you are required to restart the ECS and enter the rescue mode.
-  Restarting the ECS may interrupt services. Exercise caution when performing this operation.

Root Cause
----------

The **nofile** parameter in **/etc/security/limits.conf** is used to set the maximum number of files that can be opened in the system. If the value is greater than the **fs.nr_open** value (**1048576** by default) set in **PermissionDenied.png**, a login verification error will occur, leading to "Permission denied".

Solution
--------

#. Enter the single-user mode.The following uses CentOS 7 as an example:

   a. Restart the ECS and click **Remote Login**.

   b. Click **Ctrl+Alt+Del** in the upper part of the remote login panel to restart the ECS.

   c. Press the up arrow key to prevent automatic system startup. When the kernels are displayed, press **e** to enter the editing mode.\ **Figure 2** Entering the kernel editing mode
      |image3| |image4|

      The grub file is encrypted by Euler images by default. Before entering the edit mode, you need to contact customer service to obtain username and password.

   d. Locate the row containing **linux16** and delete the parameters you do not require.

   e. Change **ro** to **rw** for mounting the root partition with read-write permissions.

   f. Add **rd.break** and press **Ctrl+X**.\ **Figure 3** Before the modification
      |image5| **Figure 4** After the modification
      |image6|

   g. Run the following command to go to the **/sysroot** directory:

      **# chroot /sysroot**

2. Run the following command to view the **fs.nr_open** value:

   **sysctl fs.nr_open**

3. Change the **nofile** value in **/etc/security/limits.conf** so that the value is smaller than the **fs.nr_open** value obtained in `2 <#EN-US_TOPIC_0240708483__li12380124143314>`__.\ **vi /etc/security/limits.conf**\ |image7|

   **limits.conf** is the **pam_limits.so** configuration file of Linux Pluggable Authentication Module (PAM). For more details, run the following command:

   **man limits.conf**

4. Restart the ECS and try to log in to it again.



.. |image1| image:: /_static/images/en-us_image_0240710556.png

.. |image2| image:: /_static/images/note_3.0-en-us.png
.. |image3| image:: /_static/images/en-us_image_0240711431.png
   :class: imgResize

.. |image4| image:: /_static/images/note_3.0-en-us.png
.. |image5| image:: /_static/images/en-us_image_0260575520.png
   :class: imgResize

.. |image6| image:: /_static/images/en-us_image_0260575521.png
   :class: imgResize

.. |image7| image:: /_static/images/note_3.0-en-us.png
