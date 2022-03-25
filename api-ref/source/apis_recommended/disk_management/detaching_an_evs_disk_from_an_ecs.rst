Detaching an EVS Disk from an ECS
=================================

Function
--------

This API is used to detach an EVS disk from an ECS.

URI
---

DELETE /v1/{project_id}/cloudservers/{server_id}/detachvolume/{volume_id}?delete_flag=0

`Table 1 <#enustopic0022472988table2814978410562>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0022472988table2814978410562:

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

See `Responses (Task) <../../common_parameters/task_request_result/responses_task.html>`__.

Example Request
---------------

.. code-block::

   DELETE https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/detachvolume/{volume_id}

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.

