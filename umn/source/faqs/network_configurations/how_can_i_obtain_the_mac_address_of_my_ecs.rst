How Can I Obtain the MAC Address of My ECS?
===========================================

This section describes how to obtain the MAC address of an ECS.

|image1|

The MAC address of an ECS cannot be changed.

Linux (CentOS 6)
----------------

#. Log in to the Linux ECS.

#. Run the following command to view the MAC address of the ECS:

   **ifconfig**

   | **Figure 1** Obtaining the MAC address
   | |image2|

Linux (CentOS 7)
----------------

#. Log in to the Linux ECS.

#. Run the following command to view the MAC address of the ECS:

   **ifconfig**

   | **Figure 2** Obtaining the NIC information
   | |image3|

#. Run the following command to view the MAC address of NIC **eth0**:

   **ifconfig eth0 \|egrep "ether"**

   | **Figure 3** Obtaining the MAC address of eth0
   | |image4|

#. Obtain the returned MAC address.

   **ifconfig eth0 \|egrep "ether" \|awk '{print $2}'**

   | **Figure 4** Obtaining the MAC address of eth0
   | |image5|

Windows
-------

#. Press **Win+R** to start the **Run** text box.

#. Enter **cmd** and click **OK**.

#. Run the following command to view the MAC address of the ECS:

   **ipconfig /all**

   |image6|



.. |image1| image:: /_static/images/note_3.0-en-us.png
.. |image2| image:: /_static/images/en-us_image_0121682272.png
   :class: imgResize

.. |image3| image:: /_static/images/en-us_image_0268824628.png
   :class: imgResize

.. |image4| image:: /_static/images/en-us_image_0268825353.png
   :class: imgResize

.. |image5| image:: /_static/images/en-us_image_0268826092.png
   :class: imgResize

.. |image6| image:: /_static/images/en-us_image_0188029785.png
   :class: imgResize

