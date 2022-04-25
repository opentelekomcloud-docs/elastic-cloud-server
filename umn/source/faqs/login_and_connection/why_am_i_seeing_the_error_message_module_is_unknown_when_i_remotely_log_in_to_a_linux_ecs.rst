:original_name: en-us_topic_0240708482.html

.. _en-us_topic_0240708482:

Why Am I Seeing the Error Message "Module is unknown" When I Remotely Log In to a Linux ECS?
============================================================================================

Symptom
-------

When you attempt to remotely log in to a Linux ECS, the system displays the error message "Module is unknown".

.. _en-us_topic_0240708482__fig17499319191716:

.. figure:: /_static/images/en-us_image_0240710552.png
   :alt: Click to enlarge
   :figclass: imgResize


   **Figure 1** Module is unknown

.. note::

   -  To resolve this issue, restart the ECS and enter the rescue mode.
   -  Restarting the ECS may interrupt services. Exercise caution when performing this operation.

Root Cause
----------

The file in the **/etc/pam.d/** directory was modified by mistake.

Solution
--------

#. Enter the single-user mode.

   The following uses CentOS 7 as an example:

   a. Restart the ECS and click **Remote Login**.

   b. Click **Ctrl+Alt+Del** in the upper part of the remote login panel to restart the ECS.

   c. Press the up arrow key to prevent automatic system startup. When the kernels are displayed, press **e** to enter the editing mode.

      .. _en-us_topic_0240708482__fig1087511256811:

      .. figure:: /_static/images/en-us_image_0240711431.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 2** Entering the kernel editing mode

      .. note::

         The grub file is encrypted by Euler images by default. Before entering the edit mode, you need to contact customer service to obtain username and password.

   d. Locate the row containing **linux16** and delete the parameters you do not require.

   e. Change **ro** to **rw** for mounting the root partition with read-write permissions.

   f. Add **rd.break** and press **Ctrl+X**.

      .. _en-us_topic_0240708482__fig1654418212503:

      .. figure:: /_static/images/en-us_image_0260575520.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 3** Before the modification

      .. _en-us_topic_0240708482__fig1954412105016:

      .. figure:: /_static/images/en-us_image_0260575521.png
         :alt: Click to enlarge
         :figclass: imgResize
      

         **Figure 4** After the modification

   g. Run the following command to go to the **/sysroot** directory:

      **# chroot /sysroot**

#. Run the following command to view the system log for error files:

   **grep Module /var/log/messages**

   .. _en-us_topic_0240708482__fig31081356162719:

   .. figure:: /_static/images/en-us_image_0240710554.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 5** System log

#. Comment out or modify the error line in the error files displayed in the system log.

   **vi /etc/pam.d/login**

   .. _en-us_topic_0240708482__fig11081756172711:

   .. figure:: /_static/images/en-us_image_0240710555.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 6** Modifying the error information

#. Restart the ECS and try to log in to it again.

   .. note::

      -  To view the modification records and check whether the modification is caused by misoperations, run the following command:

         **vi /root/.bash_history**

         Search for the keyword **vi** or **login**.

      -  Do not modify the files in the **/etc/pam.d/** directory. Run the following command for details about pam:

         **man pam.d**
