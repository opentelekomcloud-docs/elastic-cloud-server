.. _en-us_topic_0264235946:

Why Am I Seeing an Error Message That Says Identity of Remote Computer Cannot be Verified When I Log In to a Windows ECS?
=========================================================================================================================

Symptom
-------

An error message is displayed indicating that the identity of the remote computer cannot be verified. You are required to enter the password and log in again.

.. _en-us_topic_0264235946__en-us_topic_0173592522_en-us_topic_0120795668_fig1256612592310:

.. figure:: /_static/images/en-us_image_0288997421.png
   :alt: **Figure 1** Protocol error


   **Figure 1** Protocol error

Possible Causes
---------------

Security software installed on the ECS prevents logins from unknown IP addresses.

Solution
--------

-  Uninstall the security software.
-  Open the security software and enable the default login mode.
