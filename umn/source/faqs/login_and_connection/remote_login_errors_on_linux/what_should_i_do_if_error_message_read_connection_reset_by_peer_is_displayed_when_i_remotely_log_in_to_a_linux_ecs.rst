:original_name: en-us_topic_0240714337.html

.. _en-us_topic_0240714337:

What Should I Do If Error Message "read: Connection reset by peer" Is Displayed When I Remotely Log In to a Linux ECS?
======================================================================================================================

Symptom
-------

When I attempted to remotely log in to a Linux ECS, the system displayed error message "read: Connection reset by peer".


.. figure:: /_static/images/en-us_image_0240714761.png
   :alt: **Figure 1** read: Connection reset by peer

   **Figure 1** read: Connection reset by peer

Possible Causes
---------------

-  The remote login port is not permitted in the security group.
-  The firewall is enabled on the ECS, but the remote login port is blocked by the firewall.

Solution
--------

Perform the following operations for troubleshooting:

-  **Check security group rules.**

   -  Inbound: Add the remote login port. The default port 22 is used as an example.

   -  Outbound: Outbound rules allow network traffic to be out of specified ports.

-  **Add a port to the ECS firewall exception.**

   The following uses Ubuntu as an example:

   #. Run the following command to view the firewall status:

      **sudo ufw status**

      The following information is displayed:

      .. code-block::

         Status: active

   #. Add a port to the firewall exception, taking the default port 22 as an example.

      **ufw allow 22**

      **Rule added**

      **Rule added (v6)**

   #. Run following command to check the firewall status again:

      **sudo ufw status**

      .. code-block::

         Status: active
         To                         Action      From
         --                         ------      ----
         22                         ALLOW       Anywhere
         22 (v6)                    ALLOW       Anywhere (v6)

      Try to remotely log in to the ECS again.
