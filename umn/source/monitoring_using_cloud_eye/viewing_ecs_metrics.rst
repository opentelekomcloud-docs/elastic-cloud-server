:original_name: en-us_topic_0027371530.html

.. _en-us_topic_0027371530:

Viewing ECS Metrics
===================

Scenarios
---------

The cloud platform provides Cloud Eye, which monitors the running statuses of your ECSs. You can obtain the monitoring metrics of each ECS on the management console.

There a short time delay between transmission and display of monitoring data. The status of an ECS displayed on Cloud Eye is the status obtained 5 to 10 minutes before. If an ECS is just created, wait for 5 to 10 minutes to view the real-time monitoring data.

Prerequisites
-------------

-  The ECS is running properly.

   Cloud Eye does not display the monitoring data for a stopped, faulty, or deleted ECS. After such an ECS restarts or recovers, the monitoring data is available in Cloud Eye.

   .. note::

      Cloud Eye discontinues monitoring ECSs that remain in **Stopped** or **Faulty** state for 24 hours and removes them from the monitoring list. However, the alarm rules for such ECSs are not automatically deleted.

-  Alarm rules have been configured in Cloud Eye for the target ECS.

   The monitoring data is unavailable for the ECSs without alarm rules configured in Cloud Eye. For details, see :ref:`Setting Alarm Rules <en-us_topic_0027371531>`.

-  The target ECS has been properly running for at least 10 minutes.

   The monitoring data and graphics are available for a new ECS after the ECS runs for at least 10 minutes.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the search box above the upper right corner of the ECS list, enter the ECS name, IP address, or ID for search.

#. Click the name of the target ECS. The page providing details about the ECS is displayed.

#. Click the **Monitoring** tab to view the monitoring data.

#. In the ECS monitoring area, select a duration to view the monitoring data.

   You can view the monitoring data of the ECS in the last 1 hour, last 3 hours, last 12 hours, last 1 day, or last 7 days.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
