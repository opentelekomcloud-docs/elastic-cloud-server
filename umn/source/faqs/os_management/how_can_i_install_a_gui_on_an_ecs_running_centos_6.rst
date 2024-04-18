:original_name: en-us_topic_0116634723.html

.. _en-us_topic_0116634723:

How Can I Install a GUI on an ECS Running CentOS 6?
===================================================

Scenarios
---------

To provide a pure system, the ECSs running CentOS 6 do not have a GUI installed by default. You can install a GUI on such ECSs as needed.

Constraints
-----------

-  Before installing a GUI on an ECS, ensure that the idle memory is greater than or equal to 2 GB. Otherwise, the GUI installation may fail or the ECS cannot be started after the installation.

Procedure
---------

#. Run the following command to obtain the installation component provided by the OS:

   **# yum groupinstall "Desktop"**

2. Run the following command to set the default startup level to **5** (GUI):

   **# sed -i 's/id:3:initdefault:/id:5:initdefault:/' /etc/inittab**

3. Run the following command:

   **# startx**
