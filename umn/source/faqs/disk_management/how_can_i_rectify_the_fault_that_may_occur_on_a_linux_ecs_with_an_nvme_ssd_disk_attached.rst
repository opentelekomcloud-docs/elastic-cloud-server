:original_name: en-us_topic_0087622835.html

.. _en-us_topic_0087622835:

How Can I Rectify the Fault That May Occur on a Linux ECS with an NVMe SSD Disk Attached?
=========================================================================================

Symptom
-------

When a Linux ECS with an NVMe SSD disk attached, such as a P1 ECS, becomes faulty, you must contact the administrator to remotely create the ECS again for reconstruction.

If automatic NVMe SSD disk attachment upon ECS startup is enabled in **/etc/fstab** on the faulty ECS, the system disk recovers after the ECS is created. However, the attached NVMe SSD disk does not have a file system, and automatic NVMe SSD disk attachment upon ECS startup fails to take effect. As a result, the ECS enters the emergency mode, as shown in :ref:`Figure 1 <en-us_topic_0087622835__fig13243412145029>`.

.. _en-us_topic_0087622835__fig13243412145029:

.. figure:: /_static/images/en-us_image_0087630201.jpg
   :alt: **Figure 1** Emergency mode

   **Figure 1** Emergency mode

To ensure that the new ECS is functional, you must manually delete the attachment information in **/etc/fstab**.

.. note::

   If the NVMe SSD disk is faulty, data on it will be lost. The operations provided in this section are only used to restore automatic NVMe SSD disk attachment to an ECS, but not restoring the data on the disk.

Solution
--------

#. Log in to the ECS.

#. Enter the password of user **root** to log in to the ECS.


   .. figure:: /_static/images/en-us_image_0087631679.jpg
      :alt: **Figure 2** Logging in to the ECS

      **Figure 2** Logging in to the ECS

#. Run the following command to edit the **/etc/fstab** file:

   **vi /etc/fstab**

#. Delete the attaching information of the NVMe SSD disk and save the file.


   .. figure:: /_static/images/en-us_image_0087632786.jpg
      :alt: **Figure 3** Deleting the automatic attaching information

      **Figure 3** Deleting the automatic attaching information

#. Run the following command to restart the ECS:

   **reboot**

#. Verify that the ECS recovers and can be logged in.


   .. figure:: /_static/images/en-us_image_0087632787.jpg
      :alt: **Figure 4** Logging in to the ECS

      **Figure 4** Logging in to the ECS
