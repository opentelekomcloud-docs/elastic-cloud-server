:original_name: en-us_topic_0058747426.html

.. _en-us_topic_0058747426:

How Can I Check Whether the Network Communication Is Normal Between Two ECSs Equipped with an InfiniBand NIC Driver?
====================================================================================================================

For high-performance H2 ECSs equipped with an InfiniBand NIC driver (InfiniBand ECSs for short), perform the following operations to check whether the driver installation is successful and whether the network communication between the ECSs is normal.

.. note::

   During the check, if your ECS has no command tool installed, such as ibstat, obtain the tool from the installation package for the InfiniBand NIC driver and install the tool.

#. Check whether the NICs of the InfiniBand ECSs are functional.

   a. Log in to the ECS.

   b. Run the following command to check whether the NIC is functional:

      **ibstat**

      -  If it is functional, go to :ref:`2 <en-us_topic_0058747426__li2420713023281>`.
      -  If it is not functional, contact customer service for technical support.

#. .. _en-us_topic_0058747426__li2420713023281:

   Check whether the network communication between two InfiniBand ECSs is normal.

   a. Log in to one InfiniBand ECS and run the following command:

      **ib_write_bw -x 0 --pkey_index 0**

   b. Log in to the other InfiniBand ECS and run the following command:

      **ib_write_bw -x 0 --pkey_index 0**\ *ip_addr*

      In the preceding command, *ip_addr* is the NIC IP address of the first InfiniBand ECS.

   c. Check whether the terminal display is correct.

      .. _en-us_topic_0058747426__fig13564645028:

      .. figure:: /_static/images/en-us_image_0058747512.jpg
         :alt: **Figure 1** Normal network communication

         **Figure 1** Normal network communication

      -  If the terminal display is shown in :ref:`Figure 1 <en-us_topic_0058747426__fig13564645028>`, the network communication between the two InfiniBand ECSs is normal.
      -  If the InfiniBand network is inaccessible, contact customer service for technical support.
