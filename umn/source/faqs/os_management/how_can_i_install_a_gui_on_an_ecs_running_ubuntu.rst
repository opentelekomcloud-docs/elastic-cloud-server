:original_name: en-us_topic_0155136016.html

.. _en-us_topic_0155136016:

How Can I Install a GUI on an ECS Running Ubuntu?
=================================================

Scenarios
---------

To provide a pure system, the ECSs running Ubuntu do not have a GUI installed by default. You can install a GUI on such ECSs as needed.

For GPU-accelerated ECSs, after installing a GUI, you need to configure X Server and x11vnc to make sure that:

-  The graphics system and VNC server are automatically started upon the ECS startup.
-  Applications can invoke GPUs properly after a remote login using VNC.

You can perform the following steps to install a GUI on an Ubuntu ECS:

-  :ref:`Installing a GUI <en-us_topic_0155136016__section171371109342>`
-  :ref:`(Optional) Configuring X Server, x11vnc, and ligthdm <en-us_topic_0155136016__section017703513556>`: required only for GPU-accelerated ECSs.
-  :ref:`(Optional) Verifying Drivers on GPU-accelerated ECSs <en-us_topic_0155136016__section238717615398>`: required only for GPU-accelerated ECSs.

Constraints
-----------

-  This document applies to ECSs running Ubuntu 16.04, 18.04, and 20.04.
-  The Ubuntu ECS must have an EIP bound or have an intranet image source configured.
-  Before installing a GUI on an ECS, ensure that the idle memory is greater than or equal to 2 GB. Otherwise, the GUI installation may fail or the ECS cannot be started after the installation.
-  GPU-accelerated ECSs must have a correct GPU driver installed. For details, see :ref:`GPU Driver <en-us_topic_0234802636>`.

.. _en-us_topic_0155136016__section171371109342:

Installing a GUI
----------------

#. Log in to the ECS and install a GUI desktop environment.

   a. Run the following command to update the software library:

      **apt-get update**

   b. Run the following command to install the Ubuntu GUI desktop component:

      -  For Ubuntu 16.04, run the following command:

         **apt-get install -y scite xorg xubuntu-desktop**

      -  For Ubuntu 18.04 and 20.04, run the following command:

         **apt-get install -y ubuntu-desktop**

#. Run the following command to edit the **root/.profile** file:

   **vim /root/.profile**

   Change **mesg n \|\| true** at the end of the file to **tty -s && mesg n \|\| true**. The modified file content is as follows:

   .. code-block::

      # ~/.profile: executed by Bourne-compatible login shells.

      if [ "$BASH" ]; then
        if [ -f ~/.bashrc ]; then
          . ~/.bashrc
        fi
      fi
      tty -s && mesg n || true

#. press **Esc** to exit editing mode.

#. Run the following command to save and exit the configuration file:

   **:wq**

#. .. _en-us_topic_0155136016__li2361413175614:

   (Mandatory for Ubuntu 20.04) Add a member account.

   After GUI desktop component is installed on the ECS, you cannot log in to the Ubuntu 20.04 OS as user root **user**. Therefore, you need to add a member account for logging in to the GUI desktop.

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

#. Run the reboot command to restart the ECS.

#. Log in to the ECS using VNC provided on the management console and log in to the GUI desktop using the member account created in :ref:`5 <en-us_topic_0155136016__li2361413175614>` or the **root** account.

   -  For Ubuntu 20.04 OS, you need to use the member account to log in to the GUI desktop.
   -  For GPU-accelerated ECSs, you also need to :ref:`configure X Server, x11vnc, and ligthdm <en-us_topic_0155136016__section017703513556>`.

.. _en-us_topic_0155136016__section017703513556:

(Optional) Configuring X Server, x11vnc, and ligthdm
----------------------------------------------------

For GPU-accelerated ECSs, you need to configure X Server, x11vnc, and ligthdm when installing a GUI.

#. Remotely log in to the ECS.

#. .. _en-us_topic_0155136016__li168059010570:

   Query the BusID of the GPU.

   **lspci \| grep -i nvidia**


   .. figure:: /_static/images/en-us_image_0000001305249202.png
      :alt: **Figure 1** GPU's BusID

      **Figure 1** GPU's BusID

#. Generate the X Server configuration.

   **nvidia-xconfig --enable-all-gpus --separate-x-screens**

#. Configure the GPU's BusID in "Section Device" in the generated **/etc/X11/xorg.conf**.

   a. Edit **/etc/X11/xorg.conf**.

      **vi /etc/X11/xorg.conf**

   b. Press **i** to enter editing mode.

   c. Add the GPU's BusID in "Section "Device".


      .. figure:: /_static/images/en-us_image_0000001358242793.png
         :alt: **Figure 2** Adding the GPU's BusID

         **Figure 2** Adding the GPU's BusID

      .. note::

         The BusID queried in step :ref:`2 <en-us_topic_0155136016__li168059010570>` is a hexadecimal number. You need to convert it to a decimal number before adding it to "Section Device" in **/etc/X11/xorg.conf**.

         #. For example, the queried BusID is **00.0d.0** (a hexadecimal number) and needs to be converted to **PCI:00:13:0** (a decimal number).

   d. press **Esc** to exit editing mode.

   e. Run the following command to save and exit the configuration file:

      **:wq**

#. Install x11vnc.

   **apt-get -y install x11vnc**

#. Install ligthdm.

   **apt-get -y install lightdm**

#. Select **ligthdm** as the default display manager.


   .. figure:: /_static/images/en-us_image_0000001358295221.png
      :alt: **Figure 3** Selecting a display manager

      **Figure 3** Selecting a display manager

#. Configure the GUI desktop environment to automatically start upon ECS startup.

   **systemctl set-default graphical.target**

#. (Optional) Configure the x11vnc to automatically start upon ECS startup.

   a. Add the **/lib/systemd/system/myservice.service** file.

      **vi /lib/systemd/system/myservice.service**

   b. Press **i** to enter editing mode.

   c. Add the following content to the file:

      .. code-block::

         [Unit]
         Description=My Service
         After=network.target lightdm.service

         [Service]
         Type=oneshot
         ExecStart=/usr/bin/x11vnc -forever -loop -noxdamage -repeat -rfbport 5902 -shared -bg -auth guess -o /var/log/vnc.log

         [Install]
         WantedBy=multi-user.target
         Alias=myservice.service

   d. press **Esc** to exit editing mode.

   e. Run the following command to save and exit the configuration file:

      **:wq**

#. Load configuration files.

   **systemctl daemon-reload**

   **systemctl enable myservice.service**

#. Run the reboot command to restart the ECS.

.. _en-us_topic_0155136016__section238717615398:

(Optional) Verifying Drivers on GPU-accelerated ECSs
----------------------------------------------------

After installing a GUI on a GPU-accelerated ECS, perform the following operations to check whether the driver is working properly:

#. Log in to the management console.

#. Configure a security group for the ECS.

   a. On the ECS list, click the name of an ECS for which you want to configure the security group rule. On the ECS details page, click **Security Groups**.

   b. Expand the security group and in the upper right corner of the security group rule list, click **Modify Security Group Rule**.

   c. On the **Inbound Rules** page, click **Add Rule**.

   d. In the **Add Inbound Rule** dialog box, follow the prompts to add the following security group rule:

      Allow inbound access through TCP port *5902*. The port number is determined by the **rfbport** parameter in step **Step 9.c.**

#. Log in to the ECS using VNC.

   The following uses TightVNC as an example.


   .. figure:: /_static/images/en-us_image_0000001305796210.png
      :alt: **Figure 4** TightVNC client

      **Figure 4** TightVNC client

#. Right-click on the blank area and choose **Open in Terminal** from the shortcut menu.

#. Run the following command on the terminal. If the graphics card information is displayed as follows, the driver is working properly.

   **nvidia-settings**


   .. figure:: /_static/images/en-us_image_0000001358439905.png
      :alt: **Figure 5** Graphics card information

      **Figure 5** Graphics card information

   .. note::

      If a GPU-accelerated ECS has a GRID driver installed, you need to configure a license to use the GPU rendering capability. For details, see :ref:`Installing a GRID Driver on a GPU-accelerated ECS <en-us_topic_0149610914>`.
