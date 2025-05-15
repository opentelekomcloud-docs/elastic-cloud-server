:original_name: en-us_topic_0102008259.html

.. _en-us_topic_0102008259:

Why Does a Forcibly-Stopped Linux ECS Fail to Be Restarted?
===========================================================

Symptom
-------

When you try to restart a forcibly-stopped Linux ECS, the ECS failed to be restarted, as shown in :ref:`Figure 1 <en-us_topic_0102008259__fig164879554218>`.

.. _en-us_topic_0102008259__fig164879554218:

.. figure:: /_static/images/en-us_image_0102010422.png
   :alt: **Figure 1** Restart failure

   **Figure 1** Restart failure

Possible Causes
---------------

As shown in :ref:`Figure 1 <en-us_topic_0102008259__fig164879554218>`, the ECS cannot be restarted because the file system was damaged. Forcibly stopping or restarting an ECS is highly risky because this operation may cause inconsistent metadata in the file system, leading to the file system damage.

Solution
--------

Use the disk repair tool (fsck) delivered with the Linux OS to rectify the fault.

The following procedure considers the affected disk partition as **/dev/xvdb1**, which is the partition shown in :ref:`Figure 1 <en-us_topic_0102008259__fig164879554218>`.

#. Enter the password of user **root** as prompted.

#. Run the following command to check whether the affected disk partition has been mounted:

   **mount \| grep xvdb1**

   -  If yes, go to step :ref:`3 <en-us_topic_0102008259__li459302613371>`.
   -  If no, go to step :ref:`4 <en-us_topic_0102008259__li7183774275>`.

#. .. _en-us_topic_0102008259__li459302613371:

   Run the following command to unmount the affected disk partition:

   **umount /dev/xvdb1**

#. .. _en-us_topic_0102008259__li7183774275:

   Run the following command to rectify the file system of the affected disk partition:

   **fsck -y /dev/xvdb1**

#. Run the following command to restart the ECS:

   **reboot**

   .. note::

      If the fault persists, contact customer service for technical support.
