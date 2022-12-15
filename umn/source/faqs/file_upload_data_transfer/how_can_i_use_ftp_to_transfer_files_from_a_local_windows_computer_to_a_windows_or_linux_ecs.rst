:original_name: en-us_topic_0263806053.html

.. _en-us_topic_0263806053:

How Can I Use FTP to Transfer Files from a Local Windows Computer to a Windows or Linux ECS?
============================================================================================

Scenarios
---------

You want to use FTP to transfer files from a local Windows computer to an ECS.

Prerequisites
-------------

-  An EIP has been bound to the ECS and access to port 21 is allowed in the inbound direction of the security group to which the ECS belongs.
-  You have enabled FTP on the target ECS. If you have not enabled FTP, check the following links to know how to set up an FTP site:

Procedure
---------

#. `Download FileZilla <https://filezilla-project.org/>`__ and install it on the local Windows computer.

#. On the local Windows computer, open FileZilla, enter the information about the target ECS, and click **Quickconnect**.

   -  **Host**: EIP bound to the ECS
   -  **Username**: username set when the FTP site was set up
   -  **Password**: password of the username
   -  **Port**: FTP access port, which is port 21 by default


   .. figure:: /_static/images/en-us_image_0263806339.png
      :alt: **Figure 1** Setting connection parameters

      **Figure 1** Setting connection parameters

#. Drag files from the local computer on the left to the target ECS on the right to transfer them.
