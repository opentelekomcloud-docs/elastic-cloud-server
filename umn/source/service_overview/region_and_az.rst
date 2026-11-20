:original_name: en-us_topic_0186645877.html

.. _en-us_topic_0186645877:

Region and AZ
=============

Concept
-------

A region and availability zone (AZ) identify the location of a data center. You can create resources in a specific region and AZ.

-  A region is a geographic area where cloud resources are deployed. Each region is fully isolated to maximize fault tolerance and stability. The region that is selected during resource creation cannot be changed after the resource is created.
-  An AZ is a physically isolated area within a region. Each AZ has independent power and network infrastructure. A failure in one AZ does not affect other AZs. A region can contain multiple AZs. AZs are physically isolated from each other but interconnected through a private network, ensuring fault isolation while providing low-cost, low-latency network connectivity.

:ref:`Figure 1 <en-us_topic_0186645877__en-us_topic_0184026189_fig8747114281212>` shows the relationship between regions and AZs.

.. _en-us_topic_0186645877__en-us_topic_0184026189_fig8747114281212:

.. figure:: /_static/images/en-us_image_0184026531.png
   :alt: **Figure 1** Regions and AZs

   **Figure 1** Regions and AZs

Selecting a Region
------------------

For lower network latency and quick resource access, select the region nearest to your target users.

Selecting an AZ
---------------

When determining whether to deploy resources in the same AZ, consider your requirements for disaster recovery (DR) and network latency.

-  For high DR capability, deploy resources in different AZs within the same region.
-  For lower network latency, deploy resources in the same AZ.

Regions and Endpoints
---------------------

Before you use an API to call resources, specify its region and endpoint. For more details, see `Regions and Endpoints <https://docs.otc.t-systems.com/regions-and-endpoints/index.html>`__.
