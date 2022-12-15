:original_name: en-us_topic_0214940106.html

.. _en-us_topic_0214940106:

Why Does the Disk Attachment of a Linux ECS Fail After I Modify the ECS Specifications?
=======================================================================================

Scenarios
---------

After you modify specifications of a Linux ECS, disk attachment may fail. Therefore, you need to check the disk attachment after you modify the specifications.

Procedure
---------

#. Log in to the ECS as user **root**.

#. .. _en-us_topic_0214940106__en-us_topic_0120890833_li218141135312:

   Run the following command to view the disks attached before specifications modification:

   **fdisk -l** **\| grep 'Disk /dev/'**

   .. _en-us_topic_0214940106__en-us_topic_0120890833_fig10595124010458:

   .. figure:: /_static/images/en-us_image_0214947581.png
      :alt: **Figure 1** Viewing disks attached before specifications modification

      **Figure 1** Viewing disks attached before specifications modification

   As shown in :ref:`Figure 1 <en-us_topic_0214940106__en-us_topic_0120890833_fig10595124010458>`, the ECS has three disks attached: **/dev/vda**, **/dev/vdb**, and **/dev/vdc**.

#. .. _en-us_topic_0214940106__en-us_topic_0120890833_li161843557534:

   Run the following command to view disks attached after specifications modification:

   **df -h\| grep '/dev/'**

   .. _en-us_topic_0214940106__en-us_topic_0120890833_fig692535712437:

   .. figure:: /_static/images/en-us_image_0214947582.png
      :alt: **Figure 2** Viewing disks attached after specifications modification

      **Figure 2** Viewing disks attached after specifications modification

   As shown in :ref:`Figure 2 <en-us_topic_0214940106__en-us_topic_0120890833_fig692535712437>`, only one disk **/dev/vda** is attached to the ECS.

#. Check whether the number of disks obtained in step :ref:`3 <en-us_topic_0214940106__en-us_topic_0120890833_li161843557534>` is the same as that obtained in step :ref:`2 <en-us_topic_0214940106__en-us_topic_0120890833_li218141135312>`.

   -  If the numbers are the same, the disk attachment is successful. No further action is required.
   -  If the numbers are different, the disk attachment failed. In this case, go to step :ref:`5 <en-us_topic_0214940106__en-us_topic_0120890833_li1478325211557>`.

#. .. _en-us_topic_0214940106__en-us_topic_0120890833_li1478325211557:

   Run the **mount** command to attach the affected disks.

   For example, run the following command:

   **mount /dev/vbd1 /mnt/vbd1**

   In the preceding command, **/dev/vbd1** is the disk to be attached, and **/mnt/vbd1** is the path for disk attachment.

   .. important::

      Ensure that **/mnt/vbd1** is empty. Otherwise, the attachment will fail.

#. Run the following commands to check whether the numbers of disks before and after specifications modifications are the same:

   **fdisk -l** **\| grep 'Disk /dev/'**

   **df -h\| grep '/dev/'**

   -  If the numbers are the same, no further action is required.
   -  If the numbers are different, contact customer service.

   .. _en-us_topic_0214940106__en-us_topic_0120890833_fig722411124917:

   .. figure:: /_static/images/en-us_image_0214947583.png
      :alt: **Figure 3** Checking the number of disks attached

      **Figure 3** Checking the number of disks attached

   As shown in :ref:`Figure 3 <en-us_topic_0214940106__en-us_topic_0120890833_fig722411124917>`, the numbers of disks before and after specifications modifications are the same. The disks are **/dev/vda**, **/dev/vdb**, and **/dev/vdc**.
