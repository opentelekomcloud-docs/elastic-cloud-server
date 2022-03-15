How Can I Obtain the MAC Address of My ECS?
===========================================

This section describes how to obtain the MAC address of an ECS.

.. note::

   The MAC address of an ECS cannot be changed.

Linux (CentOS 6)
----------------

#. Log in to the Linux ECS.

#. Run the following command to view the MAC address of the ECS:

   **ifconfig**

   .. figure:: /_static/images/en-us_image_0121682272.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 1** Obtaining the MAC address

Linux (CentOS 7)
----------------

#. Log in to the Linux ECS.

#. Run the following command to view the MAC address of the ECS:

   **ifconfig**

   .. figure:: /_static/images/en-us_image_0268824628.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 2** Obtaining the NIC information

#. Run the following command to view the MAC address of NIC **eth0**:

   **ifconfig eth0 \|egrep "ether"**

   .. figure:: /_static/images/en-us_image_0268825353.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 3** Obtaining the MAC address of eth0

#. Obtain the returned MAC address.

   **ifconfig eth0 \|egrep "ether" \|awk '{print $2}'**

   .. figure:: /_static/images/en-us_image_0268826092.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 4** Obtaining the MAC address of eth0

Windows
-------

#. Press **Win+R** to start the **Run** text box.

#. Enter **cmd** and click **OK**.

#. Run the following command to view the MAC address of the ECS:

   **ipconfig /all**

   |image1|



.. |image1| image:: /_static/images/en-us_image_0188029785.png
   :class: imgResize

