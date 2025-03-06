:original_name: en-us_topic_0240708483.html

.. _en-us_topic_0240708483:

What Should I Do If Error Message "Permission denied" Is Displayed When I Remotely Log In to a Linux ECS?
=========================================================================================================

Symptom
-------

When I attempted to remotely log in to a Linux ECS, the system displayed error Message "Permission denied".


.. figure:: /_static/images/en-us_image_0240710556.png
   :alt: **Figure 1** Permission denied

   **Figure 1** Permission denied

.. note::

   -  To resolve this issue, you are required to restart the ECS and enter the rescue mode.
   -  Restarting the ECS may interrupt services. Exercise caution when performing this operation.

Root Cause
----------

The **nofile** parameter in **/etc/security/limits.conf** is used to set the maximum number of files that can be opened in the system. If the value is greater than the **fs.nr_open** value (**1048576** by default) set in **PermissionDenied.png**, a login verification error will occur, leading to "Permission denied".

Solution
--------

#. Enter the single-user mode.

   The following uses CentOS 7 as an example:

   a. Restart the ECS and click **Remote Login**.

   b. Click **Ctrl+Alt+Del** in the upper part of the remote login panel to restart the ECS.

   c. Press the up arrow key to prevent automatic system startup. When the kernels are displayed, press **e** to enter the editing mode.


      .. figure:: /_static/images/en-us_image_0240711431.png
         :alt: **Figure 2** Entering the kernel editing mode

         **Figure 2** Entering the kernel editing mode

      .. note::

         The grub file is encrypted by Euler images by default. Before entering the edit mode, you need to contact customer service to obtain username and password.

   d. Locate the row containing **linux16** and delete the parameters you do not require.

   e. Change **ro** to **rw** for mounting the root partition with read-write permissions.

   f. Add **rd.break** and press **Ctrl+X**.


      .. figure:: /_static/images/en-us_image_0260575520.png
         :alt: **Figure 3** Before the modification

         **Figure 3** Before the modification


      .. figure:: /_static/images/en-us_image_0260575521.png
         :alt: **Figure 4** After the modification

         **Figure 4** After the modification

   g. Run the following command to go to the **/sysroot** directory:

      **# chroot /sysroot**

2. .. _en-us_topic_0240708483__li12380124143314:

   Run the following command to view the **fs.nr_open** value:

   **sysctl fs.nr_open**

3. Change the **nofile** value in **/etc/security/limits.conf** so that the value is smaller than the **fs.nr_open** value obtained in :ref:`2 <en-us_topic_0240708483__li12380124143314>`.

   **vi /etc/security/limits.conf**

   .. note::

      **limits.conf** is the **pam_limits.so** configuration file of Linux Pluggable Authentication Module (PAM). For more details, run the following command:

      **man limits.conf**

4. Restart the ECS and try to log in to it again.
