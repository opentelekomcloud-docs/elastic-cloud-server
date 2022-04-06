.. _en-us_topic_0263806053:

How Can I Use FTP to Transfer Files from a Local Windows Computer to a Windows or Linux ECS?
============================================================================================



.. _en-us_topic_0263806053__section145801229121516:

Scenarios
---------

You want to use FTP to transfer files from a local Windows computer to an ECS.



.. _en-us_topic_0263806053__section03701453154:

Prerequisites
-------------

You have enabled FTP on the target ECS. If you have not enabled FTP, check the following links to know how to set up an FTP site:



.. _en-us_topic_0263806053__section17803152819304:

Procedure
---------

#. `Download FileZilla <https://filezilla-project.org/>`__ and install it on the local Windows computer.

#. On the local Windows computer, open FileZilla, enter the information about the target ECS, and click **Quickconnect**.

   -  **Host**: EIP bound to the ECS
   -  **Username**: username set when the FTP site was set up
   -  **Password**: password of the username
   -  **Port**: FTP access port, which is port 21 by default

   

.. _en-us_topic_0263806053__fig1437792312541:

   .. figure:: /_static/images/en-us_image_0263806339.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 1** Setting connection parameters

#. Drag files from the local computer on the left to the target ECS on the right to transfer them.
