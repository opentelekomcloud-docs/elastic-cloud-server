:original_name: en-us_topic_0092499768.html

.. _en-us_topic_0092499768:

Overview
========

What Is a Tag?
--------------

A tag identifies an ECS. You can add tags to ECSs to help identify and manage them easily.

You can add tags during or after the ECS creation.

After the tags are added, you can view them on the ECS, EIP, and EVS disk details pages.

.. note::

   Tags added during the ECS creation will also be added to the EIP and EVS disks (including the system disk and data disks) of the ECS. If the ECS uses an existing EIP, the tags will not be added to that EIP.

Tag Application Scenarios
-------------------------

Tags are used to identify cloud resources. When you have many cloud resources of the same type, you can use tags to classify cloud resources by dimension (for example, usage, owner, or environment) to make resource search and batch operations easier.

:ref:`Figure 1 <en-us_topic_0092499768__en-us_topic_0157874334_fig81911042564>` shows how to group and manage resources by tag. In this example, each cloud resource is assigned two tags: owner and usage. You can quickly search for and filter specific cloud resources by tag.

For example, you can quickly filter out the cloud resources owned by team A by the owner tag, and then manage these resources.

.. _en-us_topic_0092499768__en-us_topic_0157874334_fig81911042564:

.. figure:: /_static/images/en-us_image_0000001761368056.png
   :alt: **Figure 1** Tag example

   **Figure 1** Tag example

Tag Setting Rules
-----------------

-  A maximum of 10 tags can be added to each ECS.

-  Each tag consists of a key-value pair.

-  For each resource, a tag key must be unique and can have only one tag value.

-  A tag consists of a tag key and a tag value. :ref:`Table 1 <en-us_topic_0092499768__table197401426182516>` lists the tag key and value requirements.

   .. _en-us_topic_0092499768__table197401426182516:

   .. table:: **Table 1** Tag key and value requirements

      +-----------------------+------------------------------------------------------------------------+-----------------------+
      | Parameter             | Requirement                                                            | Example Value         |
      +=======================+========================================================================+=======================+
      | Key                   | -  Cannot be left blank.                                               | Organization          |
      |                       | -  The key value must be unique for an ECS.                            |                       |
      |                       | -  Can contain a maximum of 36 characters.                             |                       |
      |                       | -  Can only contain digits, letters, hyphens (-), and underscores (_). |                       |
      +-----------------------+------------------------------------------------------------------------+-----------------------+
      | Value                 | -  Can contain a maximum of 43 characters.                             | Apache                |
      |                       | -  Can only contain digits, letters, hyphens (-), and underscores (_). |                       |
      +-----------------------+------------------------------------------------------------------------+-----------------------+
