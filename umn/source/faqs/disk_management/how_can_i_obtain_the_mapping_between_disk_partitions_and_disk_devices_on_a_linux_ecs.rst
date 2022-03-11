How Can I Obtain the Mapping Between Disk Partitions and Disk Devices on a Linux ECS?
=====================================================================================

For a Linux ECS, its disk partitions correspond to disk devices. This section uses a Linux ECS running Red Hat Enterprise Linux 7 as an example to describe how to obtain the mapping between disk partitions and disk devices.

#. Log in to the Linux ECS as user **root**.

#. Right-click in the blank area of the desktop and choose **Open Terminal** from the shortcut menu.\ **Figure 1** open terminal
   |image1|

#. Run the following command to view disk partitions and disk devices:

   **fdisk -l**

   | **Figure 2** Viewing disk partitions and disk devices
   | |image2|

   `Table 1 <#EN-US_TOPIC_0087901488__table18572291102543>`__ lists the mapping between disk partitions and disk devices.

   

.. _EN-US_TOPIC_0087901488__table18572291102543:

   .. table:: **Table 1** Mapping between disk partitions and disk devices

      ============== ===========
      Disk Partition Disk Device
      ============== ===========
      xvda           xvda
      xvdb           xvdb
      xvdc           xvdc
      xvdd           xvdd
      xvde           xvde
      xvdf           xvdf
      xvdg           xvdg
      xvdh           xvdh
      xvdi           xvdi
      xvdj           xvdj
      xvdk           xvdk
      xvdl           xvdl
      xvdm           xvdm
      xvdn           xvdn
      xvdo           xvdo
      xvdp           xvdp
      xvdq           xvdq
      xvdr           xvdr
      xvds           xvds
      xvdt           xvdt
      xvdu           xvdu
      xvdv           xvdv
      xvdw           xvdw
      xvdx           xvdx
      ============== ===========



.. |image1| image:: /_static/images/en-us_image_0087903699.png
   :class: imgResize

.. |image2| image:: /_static/images/en-us_image_0087903704.png
   :class: imgResize

