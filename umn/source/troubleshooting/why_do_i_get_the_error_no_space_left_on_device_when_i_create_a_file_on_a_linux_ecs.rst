:original_name: en-us_topic_0000001547370984.html

.. _en-us_topic_0000001547370984:

Why Do I Get the Error "No space left on device" When I Create a File on a Linux ECS?
=====================================================================================

Symptom
-------

When you create a file on a Linux ECS, the error message "No space left on device" is displayed.

Possible Causes
---------------

-  The block usage on the disk reaches 100%.
-  The inode usage on the disk reaches 100%.
-  Certain disk space is not freed up because there are unreleased file handles.
-  The value of **fs.inotify.max_user_watches** has been reached.

100% Block Usage
----------------

Run the following command to view the disk space usage:

**df -h**

If information similar to the following is displayed, the blocks have been used up.

Solution: Expand the capacity of the disk.

|image1|

100% Inode Usage
----------------

Run the following command to view the inode usage:

**df -i**

If information similar to the following is displayed, the inodes have been used up.

Solution: Expand the capacity of the disk.

|image2|

Space Occupied by Deleted Files
-------------------------------

#. Run the **df -h** command to check whether the block usage reaches 100%.

#. Run the **df -i** command to check whether the inode usage is relatively low, for example **1%**, as shown in the following figure.

#. Run the **du -sh** command to view the total disk space used by files. You may notice that there is a significant difference between the usage space and available space.

   |image3|

Solution

#. Run the following command to list deleted files whose handles are still held open by processes:

   **lsof \|grep delete**

   |image4|

#. Run the following command to stop these processes one at a time:

   **kill -9** *Process ID*

   |image5|

inotify Watch Limit Reached
---------------------------

If inotify watches are used up, "No space left on device" will be displayed.

|image6|

Solution

#. Run the following command to edit the **/etc/sysctl.conf** file:

   **vi /etc/sysctl.conf**

#. Add the following content to the file:

   .. code-block::

      fs.inotify.max_user_watches = 524288

#. Run the following command for the modification to take effect:

   **sysctl -p**

   inotify is used to monitor file system events. By default, a maximum of 8192 files can be watched for each real user ID. You can run the following command to obtain the current limit:

   **cat /proc/sys/fs/inotify/max_user_watches**

   |image7|

   If the limit is too low to watch all files, increase the limit.

.. |image1| image:: /_static/images/en-us_image_0191603932.png
.. |image2| image:: /_static/images/en-us_image_0191603933.png
.. |image3| image:: /_static/images/en-us_image_0191603934.png
.. |image4| image:: /_static/images/en-us_image_0191603935.png
.. |image5| image:: /_static/images/en-us_image_0191603936.png
.. |image6| image:: /_static/images/en-us_image_0191603937.png
.. |image7| image:: /_static/images/en-us_image_0191603938.png
