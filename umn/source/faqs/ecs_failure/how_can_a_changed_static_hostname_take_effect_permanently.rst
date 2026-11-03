:original_name: en-us_topic_0050735736.html

.. _en-us_topic_0050735736:

How Can a Changed Static Hostname Take Effect Permanently?
==========================================================

Symptom
-------

The static hostname of a Linux ECS is user defined and injected using Cloud-Init during the ECS creation. Although the hostname can be changed by running the **hostname** command, the changed hostname is restored after the ECS is restarted.

Changing the Hostname on the ECS
--------------------------------

To make the changed hostname still take effect even after the ECS is stopped or restarted, save the changed hostname into configuration files.

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

      .. note::

         If there is no **HOSTNAME** in the configuration file, manually add this parameter and set it to the changed hostname.

      For example:

      .. code-block::

         HOSTNAME=new_hostname

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

4. Run the following command to restart the ECS:

   **sudo reboot**

5. Run the following command to check whether the hostname has been changed:

   **sudo hostname**

   If the changed hostname is displayed in the command output, the hostname has been changed and the new name permanently takes effect.

Modifying the Mapping Between the ECS Hostname and IP Address (Modifying the hosts File)
----------------------------------------------------------------------------------------

If you want to use the changed hostname as the preferred localhost and localhost.localdomain, update the mapping between the hostname and IP address after the hostname is changed and then save the configuration to the corresponding Cloud-Init configuration file so that the new hostname takes effect permanently.

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

      .. note::

         If there is no **HOSTNAME** in the configuration file, manually add this parameter and set it to the changed hostname.

      For example:

      .. code-block::

         HOSTNAME=new_hostname

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

4. Update the mapping between the hostname and IP address in **/etc/hosts** to an entry starting with 127.0.0.1. Use **new_hostname** as your preferred **localhost** and **localhost.localdomain**.

   a. Run the following command to edit **/etc/hosts**:

      **sudo vim /etc/hosts**

   b. Modify the entry starting with 127.0.0.1 and replace **localhost** and **localhost.localdomain** with **new_hostname**.

      .. code-block::

         ::1     localhost       localhost.localdomain   localhost6      localhost6.localdomain6
         127.0.0.1       localhost       localhost.localdomain   localhost4      localhost4.localdomain4
         127.0.0.1       new_hostname    new_hostname

   c. Run the following command to save and exit the configuration file:

      **:wq**

5. Modify the **/etc/cloud/cloud.cfg** configuration file.

   a. Run the following command to edit the configuration file:

      **sudo vim /etc/cloud/cloud.cfg**

   b. Set **manage_etc_hosts** to **manage_etc_hosts: false**.

      .. code-block::

         manage_etc_hosts: false

   c. Run the following command to save and exit the configuration file:

      **:wq**

6. Run the following command to restart the ECS:

   **sudo reboot**

7. Run the following commands to check whether the changes to **hostname** and **hosts** take effect permanently:

   **sudo hostname**

   **sudo cat /etc/hosts**

   If the changed hostname (**new_hostname**) and **hosts** are displayed in the command output, the changes take effect permanently.
