:original_name: en-us_topic_0263796591.html

.. _en-us_topic_0263796591:

How Can I Use SCP to Transfer Files Between a Local Linux Computer and a Linux ECS?
===================================================================================

Scenarios
---------

You want to use SCP to transfer files between a local Linux computer and a Linux ECS.

Procedure
---------

Log in to the management console. On the **Elastic Cloud Server** page, obtain the EIP bound to the target ECS in the **IP Address** column.

-  **Uploading files**

   Run the following command on the local Linux computer to upload files to the Linux ECS:

   **scp** *Path in which the files are stored on the local computer Username@EIP:Path in which the files are to be stored on the Linux ECS*

   For example, to transfer the **/home/test.txt** file on the local computer to the **/home** directory on the ECS whose EIP is 139.x.x.x, run the following command:

   **scp /home/test.txt root@139.x.x.x:/home**

   Enter the login password as prompted.


   .. figure:: /_static/images/en-us_image_0263796649.png
      :alt: **Figure 1** Setting file uploading

      **Figure 1** Setting file uploading

-  **Downloading files**

   Run the following command on the local Linux computer to download files from the Linux ECS:

   **scp** *Username@EIP:Path in which the files are stored on the Linux ECS Path in which the files are to be stored on the local computer*

   For example, to download the **/home/test.txt** file on the ECS whose EIP is 139.x.x.x to the **/home** directory on the local computer, run the following command:

   **scp root@139.x.x.x:/home/test.txt /home/**

   Enter the login password as prompted.


   .. figure:: /_static/images/en-us_image_0263796651.png
      :alt: **Figure 2** Setting file downloading

      **Figure 2** Setting file downloading
