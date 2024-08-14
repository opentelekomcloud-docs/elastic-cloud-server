:original_name: en-us_topic_0000001630328828.html

.. _en-us_topic_0000001630328828:

Searching for ECSs
==================

Scenarios
---------

After purchasing an ECS, you can use the search function on the management console to search for ECSs in the current region. You can search for ECSs by name, ID, AZ, status, flavor name, image ID, EIP, private IP address, creation time, VPC ID, enterprise project, or resource tag.

.. note::

   Searching by enterprise project is only available for enterprise users.

Search Syntax
-------------

A variety of ECS search types are available. For details, see :ref:`Table 1 <en-us_topic_0000001630328828__table145381755194911>`.

.. note::

   -  For certain properties, if you enter complete values, the system can automatically identity the property type and search for them.
   -  The following properties only support exact search and you need to enter complete values: ID, image ID, EIP, VPC ID, and enterprise project.
   -  The private IP address must be in the following CIDR blocks: 10.0.0.0/8-24, 172.16.0.0/12-24, and 192.168.0.0/16-24.
   -  You can search by tag key-value pair. You can add one or more tags. If keys are different, the tags are automatically joined with AND. If the keys are the same but the values are different, the tags are also automatically joined with AND.
   -  You cannot use both the private IP address and EIP for a combination of search.

.. _en-us_topic_0000001630328828__table145381755194911:

.. table:: **Table 1** Search syntax

   +-----------------------------+-------------------------------+-------------------------------------+------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Search Type                 | Supported Property            | Format                              | Example                                        | Description                                                                                                                                                   |
   +=============================+===============================+=====================================+================================================+===============================================================================================================================================================+
   | Property value              | ID                            | Complete property value             | ID: 4a79dfec-f0d8-4181-9bef-495b8b7220e1       | When you search by keyword, enter a complete property value instead of selecting a property. The system can automatically match the property type for search. |
   |                             |                               |                                     |                                                |                                                                                                                                                               |
   | Automatic property matching | Flavor name                   |                                     | Flavor Name: s2.xlarge.4                       |                                                                                                                                                               |
   |                             |                               |                                     |                                                |                                                                                                                                                               |
   |                             | EIP                           |                                     | Private IP Address: 192.168.99.231             |                                                                                                                                                               |
   |                             |                               |                                     |                                                |                                                                                                                                                               |
   |                             | Private IP address            |                                     |                                                |                                                                                                                                                               |
   +-----------------------------+-------------------------------+-------------------------------------+------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Property value              | Name                          | Incomplete property value           | Name: ecs-c                                    | Select a property, and enter or choose the corresponding property value.                                                                                      |
   |                             |                               |                                     |                                                |                                                                                                                                                               |
   | Fuzzy search                | Private IP address            |                                     | Flavor name: s7n                               |                                                                                                                                                               |
   |                             |                               |                                     |                                                |                                                                                                                                                               |
   |                             | Flavor name                   |                                     | Private IP address: 192.168.0                  |                                                                                                                                                               |
   +-----------------------------+-------------------------------+-------------------------------------+------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Single property             | All properties on the console | Property: Value                     | Private IP Address: 192.168.99.231             | Select a property, and enter or choose the corresponding property value.                                                                                      |
   |                             |                               |                                     |                                                |                                                                                                                                                               |
   |                             |                               |                                     |                                                | The following properties only support exact search and you need to enter complete values for them: ID, EIP, image ID, and VPC ID.                             |
   +-----------------------------+-------------------------------+-------------------------------------+------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Multiple properties         | All properties on the console | Property 1: Value Property 2: Value | Private IP Address: 192.168.99.231 Name: ecs-c | You can search by multiple properties and the properties are in AND relationship.                                                                             |
   |                             |                               |                                     |                                                |                                                                                                                                                               |
   |                             |                               |                                     |                                                | The following properties only support exact search and you need to enter complete values for them: ID, EIP, image ID, and VPC ID.                             |
   +-----------------------------+-------------------------------+-------------------------------------+------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

Procedure
---------

#. Log in to the management console.

#. Under **Computing**, click **Elastic Cloud Server**.

   The ECS console is displayed.

#. In the search box, specify search criteria.

   You can use either of the following methods:

   -  Directly enter a property value for search.
   -  Select a property first and specify the property value for search.

      a. Click the search box and select a property.


         .. figure:: /_static/images/en-us_image_0000001787680536.png
            :alt: **Figure 1** Selecting a property

            **Figure 1** Selecting a property

      b. Specify a property value and press **Enter** to search.

Example 1: Searching by Property Value
--------------------------------------

After you enter a complete property value, the system automatically identifies the property type and search for it.

-  Searching by a single value

   Enter a complete ECS ID and press **Enter** to search.

-  Searching by multiple values

   Enter multiple complete flavor names and press **Enter** to search.

Example 2: Searching by a Single Property
-----------------------------------------

Select a property, and enter or choose the corresponding property value.

The following properties only support exact search and you need to enter complete values for them: ID, EIP, image ID, and VPC ID.

-  Fuzzy search by private IP address

   #. Select **Private IP Address** in the search box.
   #. Enter a private IP address and press **Enter** to search. Private IP addresses can be used for fuzzy search. For example, you can enter **192.168.0** to search for all ECSs that use the 192.168.0 IP address.

-  Exact search by ID

   #. Select **ID** in the search box.
   #. Enter a complete ECS ID and press **Enter** to search.

Example 3: Searching by Multiple Properties
-------------------------------------------

You can search by multiple properties and the properties are in AND relationship.

The following properties only support exact search and you need to enter complete values for them: ID, EIP, image ID, and VPC ID.

In this example, use **Name** and **Private IP Address** for a combination of search.

#. Select **Name** and enter an ECS name in the search box for fuzzy search.
#. Select **Private IP Address** and enter a private IP address for fuzzy search.

Example 4: Searching by Tags
----------------------------

You can search by tag key-value pair.

You can add one or more tags. If keys are different, the tags are automatically joined with AND.

If the keys are the same but the values are different, the tags are also automatically joined with AND.

-  Searching by a single tag

   In the search box, select **Tag** and then a key-value pair, and click **OK**.

-  Searching by multiple tags

   In the search box, select multiple tag key-value pairs for search.

   If you search by multiple tags, the tags are in the AND relationship.
