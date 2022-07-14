:original_name: en-us_topic_0022472988.html

.. _en-us_topic_0022472988:

Detaching an EVS Disk from an ECS
=================================

Function
--------

This API is used to detach an EVS disk from an ECS.

URI
---

DELETE /v1/{project_id}/cloudservers/{server_id}/detachvolume/{volume_id}?delete_flag=0

:ref:`Table 1 <en-us_topic_0022472988__table2814978410562>` describes the parameters in the URI.

.. _en-us_topic_0022472988__table2814978410562:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+---------------------------------------------------+
   | Parameter             | Mandatory             | Description                                       |
   +=======================+=======================+===================================================+
   | project_id            | Yes                   | Specifies the project ID.                         |
   +-----------------------+-----------------------+---------------------------------------------------+
   | server_id             | Yes                   | Specifies the ECS ID.                             |
   +-----------------------+-----------------------+---------------------------------------------------+
   | volume_id             | Yes                   | Specifies the disk ID.                            |
   +-----------------------+-----------------------+---------------------------------------------------+
   | delete_flag           | No                    | Indicates whether to forcibly detach a data disk. |
   |                       |                       |                                                   |
   |                       |                       | -  If yes, set it to **1**.                       |
   |                       |                       | -  If no, set it to **0**.                        |
   |                       |                       |                                                   |
   |                       |                       | It is set to **0** by default.                    |
   +-----------------------+-----------------------+---------------------------------------------------+

Request
-------

None

Response
--------

See :ref:`Responses (Task) <en-us_topic_0022067714>`.

Example Request
---------------

.. code-block:: text

   DELETE https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/detachvolume/{volume_id}

Example Response
----------------

.. code-block::

   {
       "job_id": "70a599e0-31e7-49b7-b260-868f441e862b"
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
