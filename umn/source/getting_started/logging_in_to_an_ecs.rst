:original_name: en-us_topic_0092494193.html

.. _en-us_topic_0092494193:

Logging In to an ECS
====================

Logging In to a Windows ECS
---------------------------

You can log in to a Windows ECS using either VNC or MSTSC provided on the management console.


.. figure:: /_static/images/en-us_image_0201719710.png
   :alt: **Figure 1** Windows ECS login modes

   **Figure 1** Windows ECS login modes

#. Obtain the password.

   Use the password obtaining function provided by the management console to decrypt the key file to obtain a password.

   For details, see :ref:`Obtaining the Password for Logging In to a Windows ECS <en-us_topic_0031107266>`.

#. Select a login method and log in to the ECS.

   -  Management console (VNC)

      For details, see :ref:`Login Using VNC <en-us_topic_0027268511>`.

   -  Remote desktop connection (MSTSC)

      For details, see :ref:`Login Using MSTSC <en-us_topic_0017955381>`.

Logging In to a Linux ECS
-------------------------

You can log in to a Linux ECS using either VNC or SSH key provided on the management console.


.. figure:: /_static/images/en-us_image_0201719715.png
   :alt: **Figure 2** Linux ECS login modes

   **Figure 2** Linux ECS login modes

#. Select a login method and log in to the ECS.

   -  VNC

      For details, see :ref:`Login Using VNC <en-us_topic_0093263550>`.

   -  SSH key

      When you log in to the ECS using the SSH key, bind an EIP to the ECS.

      For details, see :ref:`Login Using an SSH Key <en-us_topic_0017955380>`.

Follow-up Procedure
-------------------

-  If you have added a data disk during ECS creation, you must initialize the data disk after logging in to the ECS.

   For details, see :ref:`Scenarios and Disk Partitions <en-us_topic_0030831623>`.

-  Certain ECSs require the installation of a driver after you log in to them. For details about available ECS types as well as their functions and usage, see "Notes" in :ref:`ECS Types <en-us_topic_0035470096>`.
