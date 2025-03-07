:original_name: en-us_topic_0116266207.html

.. _en-us_topic_0116266207:

Viewing Traces
==============

Scenarios
---------

After you enable CTS and the management tracker is created, CTS starts recording operations on cloud resources. Cloud Trace Service (CTS) stores operation records (traces) generated in the last seven days.

Viewing Real-Time Traces in the Trace List
------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.

#. Choose **Trace List** in the navigation pane on the left.

#. Set filters to search for your desired traces, as shown in :ref:`Figure 1 <en-us_topic_0116266207__en-us_topic_0179639644_fig139361441134311>`. The following filters are available.

   .. _en-us_topic_0116266207__en-us_topic_0179639644_fig139361441134311:

   .. figure:: /_static/images/en-us_image_0000001744598325.png
      :alt: **Figure 1** Filters

      **Figure 1** Filters

   -  **Trace Type**, **Trace Source**, **Resource Type**, and **Search By**: Select a filter from the drop-down list.

      -  If you select **Resource ID** for **Search By**, specify a resource ID.
      -  If you select **Trace name** for **Search By**, specify a trace name.
      -  If you select **Resource name** for **Search By**, specify a resource name.

   -  **Operator**: Select a user.
   -  **Trace Status**: Select **All trace statuses**, **Normal**, **Warning**, or **Incident**.
   -  Time range: Select **Last 1 hour**, **Last 1 day**, or **Last 1 week**, or specify a custom time range within the last seven days.

#. Click **Query**.

#. On the **Trace List** page, you can also export and refresh the trace list.

   -  Click **Export** to export all traces in the query result as a CSV file. The file can contain up to 5,000 records.
   -  Click |image2| to view the latest information about traces.

#. Click |image3| on the left of a trace to expand its details.

   |image4|

#. Click **View Trace** in the **Operation** column. The trace details are displayed.

   |image5|

#. For details about key fields in the trace structure, see `Trace Structure <https://docs.otc.t-systems.com/cloud-trace-service/umn/user_guide/trace_references/trace_structure.html#cts-03-0010>`__ and `Example Traces <https://docs.otc.t-systems.com/cloud-trace-service/umn/user_guide/trace_references/example_traces.html>`__ in the *CTS User Guide*.

.. |image1| image:: /_static/images/en-us_image_0000001696838310.png
.. |image2| image:: /_static/images/en-us_image_0000001696678850.png
.. |image3| image:: /_static/images/en-us_image_0000001744678489.jpg
.. |image4| image:: /_static/images/en-us_image_0000001942942816.png
.. |image5| image:: /_static/images/en-us_image_0000001758618249.png
