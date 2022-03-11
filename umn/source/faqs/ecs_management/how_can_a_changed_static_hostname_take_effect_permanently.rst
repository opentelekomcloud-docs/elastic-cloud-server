How Can a Changed Static Hostname Take Effect Permanently?
==========================================================

Symptom
-------

The static hostname of a Linux ECS is user defined and injected using Cloud-Init during the ECS creation. Although the hostname can be changed by running the **hostname** command, the changed hostname is restored after the ECS is restarted.

Changing the Hostname on the ECS
--------------------------------

To make the hostname changed by running the **hostname** command take effect even after the ECS is stopped or restarted, save the changed hostname into configuration files.

The changed hostname is assumed to be **new_hostname**.

#. Modify the **/etc/hostname** configuration file.

   a. Run the following command to edit the configuration file:

      **sudo vim /etc/hostname**

   b. Change the hostname to the new one.

   c. Run the following command to save and exit the configuration file:

      **:wq**

#. Modify the **/etc/sysconfig/network** configuration file.

   a. Run the following command to edit the configuration file:

      **sudo vim /etc/sysconfig/network**

   b. Change the **HOSTNAME** value to the new hostname.

      **HOSTNAME=**\ *Changed hostname*

      |image1|

      If there is no **HOSTNAME** in the configuration file, manually add this parameter and set it to the changed hostname.

      An example is provided as follows:

      **HOSTNAME=new_hostname**

   c. Run the following command to save and exit the configuration file:

      **:wq**

#. Modify the **/etc/cloud/cloud.cfg** configuration file.

   a. Run the following command to edit the configuration file:

      **sudo vim /etc/cloud/cloud.cfg**

   b. Use either of the following methods to modify the configuration file:

      -  Method 1: Change the **preserve_hostname** parameter value or add the **preserve_hostname** parameter to the configuration file.

         If **preserve_hostname: false** is already available in the **/etc/cloud/cloud.cfg** configuration file, change it to **preserve_hostname: true**. If **preserve_hostname** is unavailable in the **/etc/cloud/cloud.cfg** configuration file, add **preserve_hostname: true** before **cloud_init_modules**.

         If you use method 1, the changed hostname still takes effect after the ECS is stopped or restarted. However, if the ECS is used to create a private image and the image is used to create a new ECS, the hostname of the new ECS is the hostname (**new_hostname**) used by the private image, and user-defined hostnames cannot be injected using Cloud-Init.

      -  Method 2 (recommended): Delete or comment out **- update_hostname**.

         If you use method 2, the changed hostname still takes effect after the ECS is stopped or restarted. If the ECS is used to create a private image and the image is used to create a new ECS, the changed hostname permanently takes effect, and user-defined hostnames (such as **new_new_hostname**) can be injected using Cloud-Init.

#. Run the following command to restart the ECS:

   **sudo reboot**

#. Run the following command to check whether the hostname has been changed:

   **sudo hostname**

   If the changed hostname is displayed in the command output, the hostname has been changed and the new name permanently takes effect.



.. |image1| image:: /_static/images/note_3.0-en-us.png
