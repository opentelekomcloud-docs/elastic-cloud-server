Deleting NICs from an ECS in a Batch
====================================

Function
--------

This API is used to uninstall and delete one or multiple NICs from an ECS.

Constraints
-----------

The primary NIC of an ECS has routing rules configured and cannot be deleted.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/nics/delete

`Table 1 <#enustopic0020212665table42885739>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212665table42885739:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0020212665table35856517>`__ describes the request parameters. 

.. _ENUSTOPIC0020212665table35856517:

.. table:: **Table 2** Request parameters

   +-----------+-----------+------------------+-----------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                         |
   +===========+===========+==================+=====================================================================================================+
   | nics      | Yes       | Array of objects | Specifies the NICs to be deleted. For details, see `Table 3 <#enustopic0020212665table43212049>`__. |
   +-----------+-----------+------------------+-----------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212665table43212049:

.. table:: **Table 3** **nics** field description

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                  |
   +=================+=================+=================+==============================================================================================+
   | id              | Yes             | String          | Specifies the port ID of the NIC.                                                            |
   |                 |                 |                 |                                                                                              |
   |                 |                 |                 | .. note::                                                                                    |
   |                 |                 |                 |                                                                                              |
   |                 |                 |                 |    When the ID is the same as the ECS primary NIC ID, the system will return error code 403. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+

Response
--------

See `Responses (Task) <../../common_parameters/task_request_result/responses_task.html>`__.

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/nics/delete

.. code-block::

   {
       "nics": [
            {
               "id": "d32019d3-bc6e-4319-9c1d-6722fc136a23"
           }
       ]
   }

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


