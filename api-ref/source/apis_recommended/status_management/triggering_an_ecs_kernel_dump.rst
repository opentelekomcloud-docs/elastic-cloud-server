:original_name: en-us_topic_0000002455291649.html

.. _en-us_topic_0000002455291649:

Triggering an ECS Kernel Dump
=============================

Function
--------

This API is used to trigger an ECS kernel dump.

Constraints
-----------

-  Only ECSs in the following states can be dumped: ACTIVE, PAUSED, RESCUED, RESIZED, and ERROR.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/actions/trigger-crash-dump

:ref:`Table 1 <en-us_topic_0000002455291649__en-us_topic_0000002262327508_ecs_02_1705_mmccppss_table566015531780>` describes the parameters in the URI.

.. _en-us_topic_0000002455291649__en-us_topic_0000002262327508_ecs_02_1705_mmccppss_table566015531780:

.. table:: **Table 1** Path parameters

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================================+
   | project_id            | Yes                   | **Definition**                                                                                                                                      |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | Specifies the project ID.                                                                                                                           |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | **Constraints**                                                                                                                                     |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | N/A                                                                                                                                                 |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | **Range**                                                                                                                                           |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | N/A                                                                                                                                                 |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | **Default Value**                                                                                                                                   |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | N/A                                                                                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | server_id             | Yes                   | **Definition**                                                                                                                                      |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | Specifies the ECS ID.                                                                                                                               |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | You can obtain the ECS ID from the console or by following the instructions provided in "Listing ECSs" in the *Elastic Cloud Server API Reference*. |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | **Constraints**                                                                                                                                     |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | N/A                                                                                                                                                 |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | **Range**                                                                                                                                           |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | N/A                                                                                                                                                 |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | **Default Value**                                                                                                                                   |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | N/A                                                                                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

None

Example Request
---------------

Trigger an ECS kernel dump.

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/actions/trigger-crash-dump

Example Response
----------------

.. code-block::

   {}

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
