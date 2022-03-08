Overview
========

Scenarios
---------

A tag identifies an ECS. Adding tags to an ECS facilitates ECS identification and management.

You can add a tag to an ECS during the ECS creation or after the ECS creation (**Tags** tab on the page providing details about the ECS). Up to 10 tags can be added to an ECS.

|image1|

Tags added during ECS creation will also be added to the created EIP and EVS disks (including the system disk and data disks) of the ECS. If the ECS uses an existing EIP, the tags will not be added to the EIP.

After creating the ECS, you can view the tags on the pages providing details about the ECS, EIP, and EVS disks.

Basics of Tags
--------------

Tags are used to identify cloud resources. When you have many cloud resources of the same type, you can use tags to classify cloud resources by dimension (for example, use, owner, or environment).

| **Figure 1** Example tags
| |image2|

`Figure 1 <#EN-US_TOPIC_0092499768__en-us_topic_0157874334_fig81911042564>`__ shows how tags work. In this example, you assign two tags to each cloud resource. Each tag contains a key and a value that you define. The key of one tag is **Owner**, and the key of another tag is **Use**. Each tag has a value.

You can quickly search for and filter specific cloud resources based on the tags added to them. For example, you can define a set of tags for cloud resources in an account to track the owner and usage of each cloud resource, making resource management easier.

Tag Naming Rules
----------------

-  Each tag consists of a key-value pair.
-  Each ECS supports adding up to 10 tags.
-  For each resource, a tag key must be unique and can have only one tag value.
-  A tag consists of a tag key and a tag value. `Table 1 <#EN-US_TOPIC_0092499768__table197401426182516>`__ lists the tag key and value requirements.
   

.. _EN-US_TOPIC_0092499768__table197401426182516:

   .. table:: **Table 1** Tag key and value requirements

      +---------------------------------------+---------------------------------------+---------------------------------------+
      | Parameter                             | Requirement                           | Example Value                         |
      +=======================================+=======================================+=======================================+
      | Key                                   | -  Cannot be left blank.              | Organization                          |
      |                                       | -  The key value must be unique for   |                                       |
      |                                       |    an ECS.                            |                                       |
      |                                       | -  Can contain a maximum of 36        |                                       |
      |                                       |    characters.                        |                                       |
      |                                       | -  Can only consist of digits,        |                                       |
      |                                       |    letters, hyphens (-), and          |                                       |
      |                                       |    underscores (_).                   |                                       |
      +---------------------------------------+---------------------------------------+---------------------------------------+
      | Value                                 | -  Can contain a maximum of 43        | Apache                                |
      |                                       |    characters.                        |                                       |
      |                                       | -  Can only consist of digits,        |                                       |
      |                                       |    letters, hyphens (-), and          |                                       |
      |                                       |    underscores (_).                   |                                       |
      +---------------------------------------+---------------------------------------+---------------------------------------+


.. |image1| image:: /_static/images/note_3.0-en-us.png
.. |image2| image:: /_static/images/en-us_image_0157904965.png
   :class: imgResize

