:original_name: en-us_topic_0120795668.html

.. _en-us_topic_0120795668:

Why Does the System Display Error Code 0x112f When I Log In to a Windows ECS?
=============================================================================

Symptom
-------

When you log in to a Windows ECS, the system displays error code 0x112f.


.. figure:: /_static/images/en-us_image_0120795776.jpg
   :alt: **Figure 1** Error message (code: 0x112f)

   **Figure 1** Error message (code: 0x112f)

Possible Causes
---------------

The ECS memory is insufficient.

Solution
--------

-  Method 1 (recommended)

   Modify the ECS specifications to increase the vCPUs and memory size. For instructions about how to modify ECS specifications, see :ref:`General Operations <en-us_topic_0013771092>`.

-  Method 2

   Enable virtual memory on the ECS to obtain its idle memory.

   For instructions about how to enable virtual memory, see :ref:`How Can I Enable Virtual Memory on a Windows ECS? <en-us_topic_0120795802>`

   .. note::

      This method will deteriorate the disk I/O performance. Therefore, use this method only when necessary.
