:original_name: en-us_topic_0264235943.html

.. _en-us_topic_0264235943:

Why Does the System Display Error Code 122.112.\ *.* When I Log In to a Windows ECS?
====================================================================================

Symptom
-------

The system displays error 122.112... when you use RDC to locally access an ECS running Windows Server 2012. The ECS is frequently disconnected and the Windows login process is unexpectedly interrupted.

Possible Causes
---------------

#. System resources are insufficient or unavailable.
#. The services cannot be started.

Solution
--------

#. Check system logs.

   a. Log in to the ECS using VNC.

   b. Click |image1| to start the service manager and choose **Administrative Tools** > **Event Viewer** > **Windows Logs** > **System** > **Filter Current Logs**.


      .. figure:: /_static/images/en-us_image_0000001122000869.png
         :alt: **Figure 1** Event viewer

         **Figure 1** Event viewer

   c. In the **Event Level** pane, select event levels.


      .. figure:: /_static/images/en-us_image_0000001121886141.png
         :alt: **Figure 2** Filtering logs

         **Figure 2** Filtering logs

   d. Search for login logs.

#. Check the usage of host resources.

   a. Choose **Start** > **Task Manager** > **Performance**.
   b. Check usage of CPU and memory.

#. Check whether the purchased Windows ECS is with 1 vCPU and 1 GB of memory.

   If it is, change the flavor or stop unnecessary processes.

.. |image1| image:: /_static/images/en-us_image_0000001122204571.png
