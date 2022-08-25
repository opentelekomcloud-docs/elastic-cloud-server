:original_name: en-us_topic_0134193004.html

.. _en-us_topic_0134193004:

Request Format
==============

Public cloud APIs follow RESTful API design rules.

Representational State Transfer (REST) allocates Uniform Resource Identifiers (URIs) to dispersed resources so that resources can be located. Applications on clients use Uniform Resource Locators (URLs) to obtain resources.

URLs are in the format of https://Endpoint/uri. :ref:`Table 1 <en-us_topic_0134193004__table64845234>` describes the parameters in a URL.

.. _en-us_topic_0134193004__table64845234:

.. table:: **Table 1** Parameter description

   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Description                                                                                                                                                                 |
   +===========+=============================================================================================================================================================================+
   | Endpoint  | Specifies the URL that is the entry point for a web service. Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__. |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | URI       | Specifies a resource path, which is an API access path and obtained from the API URI module, for example, /v2/{tenant_id}/servers.                                          |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

A project ID is required for some URLs when an API is called. Therefore, you need to obtain a project ID on the console before calling an API. To do so, perform the following operations:

#. Register yourself on the management console and log in to it.

#. Hover the mouse over the username and select **Basic Information** from the drop-down list.

#. On the **Account Info** page, click **Manage** following **Security Credentials**.

#. On the **My Credential** page, view the project ID in the project list.

   .. _en-us_topic_0134193004__fig82901053211:

   .. figure:: /_static/images/en-us_image_0173496413.png
      :alt: Click to enlarge
      :figclass: imgResize


      **Figure 1** Viewing project IDs

-  :ref:`Versions <en-us_topic_0134193005>`
-  :ref:`Microversions <en-us_topic_0134193006>`
-  :ref:`Request Example <en-us_topic_0134192984>`

.. toctree::
   :maxdepth: 1
   :hidden: 

   versions
   microversions
   request_example
