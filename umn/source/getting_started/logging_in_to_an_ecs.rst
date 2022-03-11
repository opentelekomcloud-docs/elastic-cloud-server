Logging In to an ECS
====================

Logging In to a Windows ECS
---------------------------

You can log in to a Windows ECS using either VNC or MSTSC provided on the management console.

| **Figure 1** Windows ECS login modes
| |image1|

#. Obtain the password.

   Use the password obtaining function provided by the management console to decrypt the key file to obtain a password.

   For details, see `Obtaining the Password for Logging In to a Windows ECS <passwords_and_key_pairs/obtaining_the_password_for_logging_in_to_a_windows_ecs>`__.

#. Select a login method and log in to the ECS.

   -  Management console (VNC)

      For details, see `Login Using VNC <instances/logging_in_to_a_windows_ecs/login_using_vnc>`__.

   -  Remote desktop connection (MSTSC)

      For details, see `Login Using MSTSC <instances/logging_in_to_a_windows_ecs/login_using_mstsc>`__.

Logging In to a Linux ECS
-------------------------

You can log in to a Linux ECS using either VNC or SSH key provided on the management console.

| **Figure 2** Linux ECS login modes
| |image2|

#. Select a login method and log in to the ECS.

   -  VNC

      For details, see `Login Using VNC <instances/logging_in_to_a_linux_ecs/login_using_vnc>`__.

   -  SSH key

      When you log in to the ECS using the SSH key, bind an EIP to the ECS.

      For details, see `Login Using an SSH Key <instances/logging_in_to_a_linux_ecs/login_using_an_ssh_key>`__.

Follow-up Procedure
-------------------

-  If you have added a data disk during ECS creation, you must initialize the data disk after logging in to the ECS.

   For details, see `Scenarios and Disk Partitions <getting_started/initializing_evs_data_disks/scenarios_and_disk_partitions>`__.

-  Certain ECSs require the installation of a driver after you log in to them. For details about available ECS types as well as their functions and usage, see "Notes" in `ECS Types <service_overview/instances/ecs_types>`__.


.. |image1| image:: /_static/images/en-us_image_0201719710.png
   :class: imgResize

.. |image2| image:: /_static/images/en-us_image_0201719715.png
   :class: vsd

