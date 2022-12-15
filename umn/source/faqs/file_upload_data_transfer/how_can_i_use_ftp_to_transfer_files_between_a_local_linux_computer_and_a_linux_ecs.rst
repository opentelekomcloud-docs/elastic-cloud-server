:original_name: en-us_topic_0263806054.html

.. _en-us_topic_0263806054:

How Can I Use FTP to Transfer Files Between a Local Linux Computer and a Linux ECS?
===================================================================================

Scenarios
---------

You want to use FTP on a local Linux computer to transfer files between the computer and a Linux ECS.

Prerequisites
-------------

You have enabled FTP on the target ECS. If you have not enabled FTP, check the following links to know how to set up an FTP site:

-  An EIP has been bound to the ECS and access to port 21 is allowed in the inbound direction of the security group to which the ECS belongs.
-  You have enabled FTP on the target ECS. If you have not enabled FTP, check the following links to know how to set up an FTP site:

Procedure
---------

#. Install FTP on the local Linux computer.

   Take CentOS 7.6 as an example. Run the following command to install FTP:

   **yum -y install ftp**

#. Run the following command to access the ECS:

   **ftp** *EIP bound to the ECS*

   Enter the username and password as prompted for login.

   -  **Uploading files**

      Run the following command to upload local files to the ECS:

      **put** *Path in which files are stored on the local computer*

      For example, to upload the **/home/test.txt** file on the local Linux computer to the ECS, run the following command:

      **put /home/test.txt**

   -  **Downloading files**

      Run the following command to download files on the ECS to the local computer:

      **get** *Path in which the files are stored on the ECS Path in which the files are to be stored on the local computer*

      For example, to download the **test.txt** file on the ECS to the local Linux computer, run the following command:

      **get /home/test.txt**
