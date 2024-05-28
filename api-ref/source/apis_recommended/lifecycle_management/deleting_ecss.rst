:original_name: en-us_topic_0020212679.html

.. _en-us_topic_0020212679:

Deleting ECSs
=============

Function
--------

This API is used to delete ECSs based on a specified ECS ID list.

This API is an asynchronous API. After the deletion request is successfully delivered, a job ID is returned. This does not mean the deletion is complete. You need to call the API by referring to :ref:`Querying Task Execution Status <en-us_topic_0022225398>` to query the job status. The SUCCESS status indicates that the deletion is successful.

You can delete a single ECS or multiple ECSs in a batch. A maximum of 1,000 ECSs can be deleted in a batch.

URI
---

POST /v1/{project_id}/cloudservers/delete

:ref:`Table 1 <en-us_topic_0020212679__table52652517>` describes the parameters in the URI.

.. _en-us_topic_0020212679__table52652517:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0020212679__table8361976>` describes the request parameters.

.. _en-us_topic_0020212679__table8361976:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                                               |
   +=================+=================+==================+===========================================================================================================================================================================================================================================+
   | servers         | Yes             | Array of objects | Specifies the ECSs to be deleted. For details, see :ref:`Table 3 <en-us_topic_0020212679__table32603030>`.                                                                                                                                |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | delete_publicip | No              | Boolean          | Specifies whether to delete the EIP bound to the ECS when deleting the ECS. If you do not want to delete the EIP, the system only unbinds the EIP from the ECS and reserves the EIP.                                                      |
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
   |                 |                 |                  |    -  If **delete_on_termination** is **true** and **delete_public** is **null,** the EIP is released when the ECS is deleted.                                                                                                            |
   |                 |                 |                  |    -  If **delete_on_termination** is **false** and **delete_public** is **null**, the EIP is only unbound from the ECS and will not be released when the ECS is deleted.                                                                 |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | delete_volume   | No              | Boolean          | Specifies whether to delete the data disks attached to an ECS when deleting the ECS. If you set the parameter value to **false**, the system only detaches the disks from the ECS and reserves the disks. The default value is **false**. |
   |                 |                 |                  |                                                                                                                                                                                                                                           |
   |                 |                 |                  | -  **true**: indicates to delete the data disks attached to the ECS when deleting the ECS.                                                                                                                                                |
   |                 |                 |                  | -  **false**: indicates only to detach the data disks attached to the ECS when deleting the ECS.                                                                                                                                          |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212679__table32603030:

.. table:: **Table 3** **servers** field description

   ========= ========= ====== ==========================================
   Parameter Mandatory Type   Description
   ========= ========= ====== ==========================================
   id        Yes       String Specifies the ID of the ECS to be deleted.
   ========= ========= ====== ==========================================

Response
--------

See :ref:`Responses (Task) <en-us_topic_0022067714>`.

Example Request
---------------

Delete the ECS whose ID is **616fb98f-46ca-475e-917e-2563e5a8cd19**, unbind the EIP, and detach data disks.

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/cloudservers/delete

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
       "job_id": "ff80808288d415d80189901d8eb81cbb"
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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
