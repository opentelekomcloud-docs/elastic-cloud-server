:original_name: en-us_topic_0017130261.html

.. _en-us_topic_0017130261:

Viewing ECS Details
===================

Scenarios
---------

After obtaining ECSs, you can view and manage them on the management console. This section describes how to view ECS configuration details, including its name, image, system disk, data disks, VPC, network interfaces, security groups, EIP address, and bandwidth.

To view the private IP address of an ECS, go to the ECS list page.

#. Log in to the and access the ECS list page.

   On the ECS list page, you can view the ECSs that you have created, as well as their basic information, such as the specifications, images, private IP addresses, and EIPs.

#. (Optional) Set the ECS information that can be displayed in the list and the display mode.

   a. On the right of the search box, click |image1|.
   b. In the **Custom Columns** area, select the information you want to display in the ECS list.

      .. table:: **Table 1** Setting the ECS list display

         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                      |
         +===================================+==================================================================================================================================================================================================+
         | Text Wrapping                     | Determines how long text in a cell is displayed. You can enable it to wrap table cell content, or disable it to truncate text.                                                                   |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | View Switching                    | Instance information can be displayed in either the list view or tab view.                                                                                                                       |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Data Columns                      | -  **Freeze none**: Data columns move as you scroll horizontally.                                                                                                                                |
         |                                   | -  **Freeze first**: The first column is always fixed and visible, which helps you check key information.                                                                                        |
         |                                   | -  **Freeze first two**: The first two columns are always fixed and visible, which is suitable for tables with many columns.                                                                     |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Operation Column                  | If you select **Freeze**, the **Operation** column is always fixed at the rightmost position of the table.                                                                                       |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Custom Columns                    | You can customize the columns displayed in the list by selecting or deselecting them based on service requirements. You can also drag |image2| before a column name to adjust its display order. |
         |                                   |                                                                                                                                                                                                  |
         |                                   | .. note::                                                                                                                                                                                        |
         |                                   |                                                                                                                                                                                                  |
         |                                   |    The **Name/ID** and **Operation** columns are mandatory by default and cannot be hidden. In addition, their display order cannot be adjusted, either.                                         |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Click **OK** to save the settings.

      .. note::

         -  If you switch to another region, the current settings will remain saved.

Procedure
---------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select a region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the ECS list page, view the ECSs you have created as well as their details such as the specifications, images, and IP addresses.

#. In the search box above the ECS list, select a filter (such as ECS name, ID, or private IP address), enter the corresponding information, and press **Enter** to search.

#. Click the name of the target ECS.

   The ECS details page is displayed.

#. View the ECS details.

   You can click different tabs to perform the operations described in :ref:`Changing Security Groups <en-us_topic_0093492517>`, :ref:`Attaching a Network Interface <en-us_topic_0093492518>`, :ref:`Adding Tags to an ECS <en-us_topic_0183019669>`, and :ref:`Binding an EIP <en-us_topic_0174917535>`.

.. |image1| image:: /_static/images/en-us_image_0000002741954043.png
.. |image2| image:: /_static/images/en-us_image_0000002742073995.png
.. |image3| image:: /_static/images/en-us_image_0000002188678994.png
