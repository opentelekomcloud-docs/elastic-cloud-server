:original_name: en-us_topic_0101604498.html

.. _en-us_topic_0101604498:

How Can I Install a GUI on an ECS Running CentOS 7?
===================================================

Scenarios
---------

You want to install a GUI on an ECS running CentOS 7 series.

Constraints
-----------

-  Before installing a GUI on an ECS, ensure that the idle memory is greater than or equal to 2 GB. Otherwise, the GUI installation may fail or the ECS cannot be started after the installation.

Procedure
---------

#. Run the following command to install the GUI desktop component:

   **# yum groupinstall "Server with GUI"**

   .. note::

      If the following message is displayed after the installation is complete:

      Failed : python -urllibs3.noarch 0:1.10.2-7.e17

      Run the following command:

      **mv /usr/lib/python2.7/site-packages/urllib3/packages/ssl_match_hostname /usr/lib/python2.7/site-packages/urllib3/packages/ssl_match_hostname.bak**

      **yum install python-urllib3 -y**

#. After the installation is complete, run the following command to set the default startup level to **graphical.target**:

   **# systemctl set-default graphical.target**

#. Run the following command to start **tgraphical.target**:

   **# systemctl start graphical.target**

#. Restart the ECS.

#. Log in to the ECS using VNC provided on the management console. Set the language, time zone, username, and password as prompted.
