Why Does the Disk Attachment of a Linux ECS Fail After I Modify the ECS Specifications?
=======================================================================================

Scenarios
---------

After you modify specifications of a Linux ECS, disk attachment may fail. Therefore, you need to check the disk attachment after you modify the specifications.

Procedure
---------

#. Log in to the ECS as user **root**.

#. Run the following command to view the disks attached before specifications modification:

   **fdisk -l** **\| grep 'Disk /dev/'**

   | **Figure 1** Viewing disks attached before specifications modification
   | |image1|

   As shown in `Figure 1 <#EN-US_TOPIC_0214940106__en-us_topic_0120890833_fig10595124010458>`__, the ECS has three disks attached: **/dev/vda**, **/dev/vdb**, and **/dev/vdc**.

#. Run the following command to view disks attached after specifications modification:

   **df -h\| grep '/dev/'**

   | **Figure 2** Viewing disks attached after specifications modification
   | |image2|

   As shown in `Figure 2 <#EN-US_TOPIC_0214940106__en-us_topic_0120890833_fig692535712437>`__, only one disk **/dev/vda** is attached to the ECS.

#. Check whether the number of disks obtained in step `3 <#EN-US_TOPIC_0214940106__en-us_topic_0120890833_li161843557534>`__ is the same as that obtained in step `2 <#EN-US_TOPIC_0214940106__en-us_topic_0120890833_li218141135312>`__.

   -  If the numbers are the same, the disk attachment is successful. No further action is required.
   -  If the numbers are different, the disk attachment failed. In this case, go to step `5 <#EN-US_TOPIC_0214940106__en-us_topic_0120890833_li1478325211557>`__.

#. Run the **mount** command to attach the affected disks.

   For example, run the following command:

   **mount /dev/vbd1 /mnt/vbd1**

   In the preceding command, **/dev/vbd1** is the disk to be attached, and **/mnt/vbd1** is the path for disk attachment.

   |image3|

   Ensure that **/mnt/vbd1** is empty. Otherwise, the attachment will fail.

#. Run the following commands to check whether the numbers of disks before and after specifications modification are the same:

   **fdisk -l** **\| grep 'Disk /dev/'**

   **df -h\| grep '/dev/'**

   -  If the numbers are the same, no further action is required.
   -  If the numbers are different, contact customer service.

   | **Figure 3** Checking the number of disks attached
   | |image4|

   As shown in `Figure 3 <#EN-US_TOPIC_0214940106__en-us_topic_0120890833_fig722411124917>`__, the numbers of disks before and after specifications modification are the same. The disks are **/dev/vda**, **/dev/vdb**, and **/dev/vdc**.



.. |image1| image:: /_static/images/en-us_image_0214947581.png
   :class: imgResize

.. |image2| image:: /_static/images/en-us_image_0214947582.png
   :class: imgResize

.. |image3| image:: /_static/images/notice_3.0-en-us.png
.. |image4| image:: /_static/images/en-us_image_0214947583.png
   :class: imgResize

