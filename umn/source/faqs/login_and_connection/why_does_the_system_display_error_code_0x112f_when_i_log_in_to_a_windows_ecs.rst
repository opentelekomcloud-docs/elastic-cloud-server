Why Does the System Display Error Code 0x112f When I Log In to a Windows ECS?
=============================================================================

Symptom
-------

When you log in to a Windows ECS, the system displays error code 0x112f.

| **Figure 1** Error message (code: 0x112f)
| |image1|

Possible Causes
---------------

The ECS memory is insufficient.

Solution
--------

-  Method 1 (recommended)

   Modify the ECS specifications to increase the vCPUs and memory size. For instructions about how to modify ECS specifications, see `General Operations for Modifying Specifications <../../instances/modifying_ecs_vcpu_and_memory_specifications/general_operations_for_modifying_specifications.html>`__.

-  Method 2

   Enable virtual memory on the ECS to obtain its idle memory.

   For instructions about how to enable virtual memory, see `How Can I Enable Virtual Memory on a Windows ECS? <../../faqs/disk_management/how_can_i_enable_virtual_memory_on_a_windows_ecs.html>`__

   |image2|

   This method will deteriorate the disk I/O performance. Therefore, use this method only when necessary.



.. |image1| image:: /_static/images/en-us_image_0120795776.jpg

.. |image2| image:: /_static/images/note_3.0-en-us.png
