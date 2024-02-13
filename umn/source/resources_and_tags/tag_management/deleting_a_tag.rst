:original_name: en-us_topic_0183019671.html

.. _en-us_topic_0183019671:

Deleting a Tag
==============

If you no longer need a tag, delete it in any of the following ways:

-  :ref:`Deleting a Tag on the ECS Details Page <en-us_topic_0183019671__section8763326153815>`
-  :ref:`Deleting a Tag on the TMS Console <en-us_topic_0183019671__section167319315388>`
-  :ref:`Batch Deleting Tags on the TMS Console <en-us_topic_0183019671__section13142241209>`

.. _en-us_topic_0183019671__section8763326153815:

Deleting a Tag on the ECS Details Page
--------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, choose **Elastic Cloud Server**.

#. In the ECS list, click the name of the target ECS.

   The ECS details page is displayed.

#. Click the **Tags** tab. Locate the row containing the tag to be deleted and click **Delete** in the **Operation** column. In the **Delete Tag** dialog box, click **Yes**.

.. _en-us_topic_0183019671__section167319315388:

Deleting a Tag on the TMS Console
---------------------------------

#. Log in to the management console.

#. Under **Management & Deployment**, choose **Tag Management Service**.

#. In the upper right corner of the page, click the username and select **Tag Management** from the drop-down list.

#. On the **Resource Tags** page, set the search criteria for ECSs and click **Search**.

#. In the **Search Result** area, click **Edit** to make the resource tag list editable.

   If the key of a tag you want to delete is not contained in the list, click |image2| and select the tag key from the drop-down list. It is a good practice to select at most 10 keys to display.

#. Locate the row containing the target ECS and click |image3|.

#. (Optional) Click |image4| in the upper right of the **Search Result** area.

   The resource list is refreshed and the refresh time is updated.

.. _en-us_topic_0183019671__section13142241209:

Batch Deleting Tags on the TMS Console
--------------------------------------

.. important::

   Exercise caution when deleting tags in a batch. After you delete the tags, they will be removed from all the associated ECSs and cannot be recovered.

#. Log in to the management console.

#. Under **Management & Deployment**, choose **Tag Management Service**.

#. On the **Resource Tags** page, set the search criteria for ECSs and click **Search**.

#. Select the target ECSs.

#. Click **Manage Tag** in the upper left corner of the list.

#. In the displayed **Manage Tag** dialog box, click **Delete** in the **Operation** column. Click **OK**.

#. (Optional) Click |image5| in the upper right of the **Search Result** area.

   The resource list is refreshed and the refresh time is updated.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
.. |image2| image:: /_static/images/en-us_image_0210875481.png
.. |image3| image:: /_static/images/en-us_image_0210875482.png
.. |image4| image:: /_static/images/en-us_image_0210875483.png
.. |image5| image:: /_static/images/en-us_image_0210875483.png
