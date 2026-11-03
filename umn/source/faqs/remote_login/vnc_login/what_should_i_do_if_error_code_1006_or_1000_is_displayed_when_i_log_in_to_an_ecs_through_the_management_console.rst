:original_name: en-us_topic_0100756510.html

.. _en-us_topic_0100756510:

What Should I Do If Error Code 1006 or 1000 Is Displayed When I Log In to an ECS Through the Management Console?
================================================================================================================

Symptom
-------

When I attempted to remotely log in to an ECS using VNC, the system displayed error code 1006, as shown in :ref:`Figure 1 <en-us_topic_0100756510__fig18701165165810>`.

.. _en-us_topic_0100756510__fig18701165165810:

.. figure:: /_static/images/en-us_image_0100756875.png
   :alt: **Figure 1** Error message displayed in a VNC-based remote login

   **Figure 1** Error message displayed in a VNC-based remote login

Possible Causes
---------------

-  The ECS is abnormal.
-  Another user has logged in to the ECS.
-  No operations are performed on the ECS and it is automatically disconnected.

Troubleshooting
---------------

#. Log in to the ECS again using VNC.

   -  If the login is successful, no further action is required.
   -  If the fault persists, go to :ref:`2 <en-us_topic_0100756510__li16500827642>`.

#. .. _en-us_topic_0100756510__li16500827642:

   Check whether the ECS is normal.

   Error code 1006 is displayed if the ECS is stopped, deleted, being migrated or restarted, or encounters a connection timeout.

#. Check whether another user has logged in to the ECS.

   If yes, you can log in to the ECS only after that user logs out.
