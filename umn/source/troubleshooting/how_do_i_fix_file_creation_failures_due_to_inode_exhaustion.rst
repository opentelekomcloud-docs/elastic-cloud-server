:original_name: en-us_topic_0000001597810477.html

.. _en-us_topic_0000001597810477:

How Do I Fix File Creation Failures Due to Inode Exhaustion?
============================================================

Symptom
-------

When you create a file or directory, you get the error message "No space left on device", "Cannot create directory", or "Couldn't create temporary archive name."

Possible Causes
---------------

In Linux, both of the following use the disk space:

-  Data
-  Inode

.. note::

   An inode (index node) stores metadata of a file system object, such as a file, directory, device file, socket, and pipe in the file system, but does not contain the object's data and filename.

Constraints
-----------

The procedures described in this section involve disk initialization. Back up data in advance.

Solution
--------

#. Run the following command to check the available space on the disk:

   **# df -h**

   .. _en-us_topic_0000001597810477__en-us_topic_0176850943_fig20632111816415:

   .. figure:: /_static/images/en-us_image_0183478729.png
      :alt: **Figure 1** Checking the available disk space

      **Figure 1** Checking the available disk space

   As shown in :ref:`Figure 1 <en-us_topic_0000001597810477__en-us_topic_0176850943_fig20632111816415>`, the disk still has enough available space.

#. Run the following command to check the available inodes on the disk:

   **# df -i**

   If the value of **Use%** in the command output is **100%**, inodes are used up. Perform the following operations to free up inodes:

   a. Archive files in all directories.

      **# tar czvf /tmp/backup.tar.gz /home/data**

   b. Delete unnecessary files to release inodes.
