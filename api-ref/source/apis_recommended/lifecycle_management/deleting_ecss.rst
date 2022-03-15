Deleting ECSs
=============

Function
--------

This API is used to delete ECSs based on a specified ECS ID list.

You can delete a single ECS or multiple ECSs in a batch. A maximum of 1000 ECSs can be deleted in a batch.

URI
---

POST /v1/{project_id}/cloudservers/delete

`Table 1 <#enustopic0020212679table52652517>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212679table52652517:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0020212679table8361976>`__ describes the request parameters. 

.. _ENUSTOPIC0020212679table8361976:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                                               |
   +=================+=================+==================+===========================================================================================================================================================================================================================================+
   | servers         | Yes             | Array of objects | Specifies the ECSs to be deleted. For details, see `Table 3 <#enustopic0020212679table32603030>`__.                                                                                                                                       |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | delete_publicip | No              | Boolean          | Specifies whether to delete the EIP bound to the ECS when deleting the ECS. If you do not want to delete the EIP, the system only unbinds the EIP from the ECS and reserves the IP address.                                               |
   |                 |                 |                  |                                                                                                                                                                                                                                           |
   |                 |                 |                  | The value can be **true** or **false**.                                                                                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                                                                                                                           |
   |                 |                 |                  | -  **true**: When an ECS is deleted, the EIP bound to the ECS is also released regardless of whether **delete_on_termination** of the EIP is **true** or **false**.                                                                       |
   |                 |                 |                  | -  **false**: When an ECS is deleted, the EIP is only unbound from the ECS and will not be released regardless of whether **delete_on_termination** of the EIP is **true** or **false**.                                                  |
   |                 |                 |                  |                                                                                                                                                                                                                                           |
   |                 |                 |                  | .. note::                                                                                                                                                                                                                                 |
   |                 |                 |                  |                                                                                                                                                                                                                                           |
   |                 |                 |                  |    If **delete_publicip** is not specified, the **delete_on_termination** value of the EIP decides whether the EIP is released when the ECS is deleted.                                                                                   |
   |                 |                 |                  |                                                                                                                                                                                                                                           |
   |                 |                 |                  |    -  If **delete_on_termination** is **true** and **delete_public** is **null**, the EIP is released when the ECS is deleted.                                                                                                            |
   |                 |                 |                  |    -  If **delete_on_termination** is **false** and **delete_public** is **null**, the EIP is only unbound from the ECS and will not be released when the ECS is deleted.                                                                 |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | delete_volume   | No              | Boolean          | Specifies whether to delete the data disks attached to an ECS when deleting the ECS. If you set the parameter value to **false**, the system only detaches the disks from the ECS and reserves the disks. The default value is **false**. |
   |                 |                 |                  |                                                                                                                                                                                                                                           |
   |                 |                 |                  | -  **true**: indicates to delete the data disks attached to the ECS when deleting the ECS.                                                                                                                                                |
   |                 |                 |                  | -  **false**: indicates only to detach the data disks attached to the ECS when deleting the ECS.                                                                                                                                          |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212679table32603030:

.. table:: **Table 3** **servers** field description

   ========= ========= ====== ==========================================
   Parameter Mandatory Type   Description
   ========= ========= ====== ==========================================
   id        Yes       String Specifies the ID of the ECS to be deleted.
   ========= ========= ====== ==========================================

Response
--------

See `Responses (Task) <../../common_parameters/task_request_result/responses_task.html>`__.

Example Request
---------------

Example request

.. code-block::

   POST https://{endpoint}/v1/{project_id}/cloudservers/delete

.. code-block::

   {
       "servers": [
           {
               "id": "616fb98f-46ca-475e-917e-2563e5a8cd19"
           }
       ], 
       "delete_publicip": false, 
       "delete_volume": false
      }

Example Response
----------------

.. code-block::

   {
       "job_id": "70a599e0-31e7-49b7-b260-868f441e862b"
   }

Or

.. code-block::

   {
       "error": {
           "message": "request body is illegal.", 
           "code": "Ecs.0005"
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


