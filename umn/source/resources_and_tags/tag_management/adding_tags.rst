Adding Tags
===========

Tags are used to identify cloud resources, such as ECSs, images, and disks. If you have multiple types of cloud resources which are associated with each other, you can add tags to the resources to classify and manage them easily. For more details, see `Overview <../../resources_and_tags/tag_management/overview.html>`__.

You can add tags to ECSs in any of the following ways:

-  `Adding Tags When Creating an ECS <#adding-tags-when-creating-an-ecs>`__
-  `Adding Tags on the Page Providing Details About an ECS <#adding-tags-on-the-page-providing-details-about-an-ecs>`__
-  `Adding Tags on the TMS Console <#adding-tags-on-the-tms-console>`__

For details about how to use predefined tags, see `Using Predefined Tags <#using-predefined-tags>`__.

Adding Tags When Creating an ECS
--------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. Click **Create ECS**.

#. Configure ECS parameters.

   Select **Configure now** for **Advanced Options**. Then, add a tag key and tag value. For the tag key and tag value requirements, see `Table 1 <../../resources_and_tags/tag_management/overview.html#enustopic0092499768table197401426182516>`__.

   .. note::

      -  For details about other parameters, see "Purchasing an ECS with Customized Configurations".

Adding Tags on the Page Providing Details About an ECS
------------------------------------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. On the **Elastic Cloud Server** page, click the name of the target ECS.

   The page providing details about the ECS is displayed.

#. Click the **Tags** tab and then **Add Tag**. In the displayed dialog box, enter the tag key and tag value. For the tag key and tag value requirements, see `Table 1 <../../resources_and_tags/tag_management/overview.html#enustopic0092499768table197401426182516>`__.

   You can change the tag value after the tag is added.

Adding Tags on the TMS Console
------------------------------

.. note::

   This method is suitable for adding tags with the same tag key to multiple resources.

#. Log in to the management console.

#. Under **Management & Deployment**, click **Tag Management Service**.

#. On the displayed **Resource Tags** page, select the region where the resource is located, select **ECS** for **Resource Type**, and click **Search**.

   All ECSs matching the search criteria are displayed.

#. In the **Search Result** area, click **Create Key**. In the displayed dialog box, enter a key (for example **project**) and click **OK**.

   After the tag is created, the tag key is added to the resource list. If the key is not displayed in the resource list, click |image3| and select the created key from the drop-down list.

   By default, the value of the tag key is **Not tagged**. You need to set a value for the tag of each resource to associate the tag with the resource.

#. Click **Edit** to make the resource list editable.

#. Locate the row containing the target ECS, click |image4|, and enter a value (for example **A**).

   After a value is set for a tag key, the number of tags is incremented by 1. Repeat the preceding steps to add tag values for other ECSs.

Using Predefined Tags
---------------------

If you want to add the same tag to multiple ECSs or other resources, you can create a predefined tag on the TMS console and then select the tag for the ECSs or resources. This frees you from having to repeatedly enter tag keys and values. To do so, perform the following operations:

#. Log in to the management console.
#. Under **Management & Deployment**, click **Tag Management Service**.
#. In the navigation pane on the left, choose **Predefined Tags**. In the right pane, click **Create Tag** enter a key (for example **project**) and a value (for example **A**) in the displayed dialog box.
#. Choose **Service List** > **Computing** > **Elastic Cloud Server**, and select the predefined tag by following the procedure for adding a tag.



.. |image1| image:: /_static/images/en-us_image_0210779229.png

.. |image2| image:: /_static/images/en-us_image_0210779229.png

.. |image3| image:: /_static/images/en-us_image_0210875481.png
   :class: imgResize

.. |image4| image:: /_static/images/en-us_image_0210875480.png

