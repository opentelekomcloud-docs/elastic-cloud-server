:original_name: en-us_topic_0065817693.html

.. _en-us_topic_0065817693:

Querying ECS Operations by Request ID
=====================================

Function
--------

This API is used to query a request of an ECS.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/os-instance-actions/{request_id}

GET /v2/{project_id}/servers/{server_id}/os-instance-actions/{request_id}

:ref:`Table 1 <en-us_topic_0065817693__en-us_topic_0057973179_table55945983>` describes the parameters in the URI.

.. _en-us_topic_0065817693__en-us_topic_0057973179_table55945983:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   request_id Yes       Specifies the request ID.
   ========== ========= =========================

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0065817693__en-us_topic_0057973153_table55529076>` describes the response parameters.

.. _en-us_topic_0065817693__en-us_topic_0057973153_table55529076:

.. table:: **Table 2** Response parameters

   +----------------+--------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type   | Description                                                                                                                                  |
   +================+========+==============================================================================================================================================+
   | instanceAction | Object | Specifies an operation performed on the ECS. For details, see :ref:`Table 3 <en-us_topic_0065817693__en-us_topic_0057973179_table42003011>`. |
   +----------------+--------+----------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817693__en-us_topic_0057973179_table42003011:

.. table:: **Table 3** **instanceAction** field description

   +---------------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type             | Description                                                                                                       |
   +===============+===========+==================+===================================================================================================================+
   | action        | Yes       | String           | Specifies the action name.                                                                                        |
   +---------------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | instance_uuid | Yes       | String           | Specifies the ECS ID in UUID format.                                                                              |
   +---------------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | message       | Yes       | String           | Specifies the result status of the action.                                                                        |
   +---------------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | project_id    | Yes       | String           | Specifies the project ID.                                                                                         |
   +---------------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | request_id    | Yes       | String           | Specifies the request ID.                                                                                         |
   +---------------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | start_time    | Yes       | String           | Specifies the time when the action was started.                                                                   |
   +---------------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | user_id       | Yes       | String           | Specifies the user ID.                                                                                            |
   +---------------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | events        | Yes       | Array of objects | Describes events. For details, see :ref:`Table 4 <en-us_topic_0065817693__en-us_topic_0057973179_table12745176>`. |
   +---------------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817693__en-us_topic_0057973179_table12745176:

.. table:: **Table 4** **events** field description

   +-------------+-----------+--------+--------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                      |
   +=============+===========+========+==================================================+
   | event       | Yes       | String | Specifies the action name.                       |
   +-------------+-----------+--------+--------------------------------------------------+
   | result      | Yes       | String | Specifies the execution result.                  |
   +-------------+-----------+--------+--------------------------------------------------+
   | traceback   | Yes       | String | Specifies the error message.                     |
   +-------------+-----------+--------+--------------------------------------------------+
   | start_time  | Yes       | String | Specifies the time when the event was started.   |
   +-------------+-----------+--------+--------------------------------------------------+
   | finish_time | Yes       | String | Specifies the time when the event was completed. |
   +-------------+-----------+--------+--------------------------------------------------+

Example Request
---------------

Query a request on a specified ECS.

.. code-block:: text

   GET https://{endpoint}/v2/89655fe61c4c4a08b9f3e7f9095441b8/servers/e723eb40-f56e-40f9-8c8c-caa517fe06ba/os-instance-actions/req-5a429946-c9cc-45cc-b5bd-68864209e5c
   GET https://{endpoint}/v2.1/89655fe61c4c4a08b9f3e7f9095441b8/servers/e723eb40-f56e-40f9-8c8c-caa517fe06ba/os-instance-actions/req-5a429946-c9cc-45cc-b5bd-68864209e5c

Example Response
----------------

.. code-block::

   {
       "instanceAction": {
           "instance_uuid": "e723eb40-f56e-40f9-8c8c-caa517fe06ba",
           "user_id": "752be40780484291a9cc7ae50fff3e6d",
           "start_time": "2014-12-11T02:17:49.000000",
           "request_id": "req-5a429946-c9cc-45cc-b5bd-68864209e5cc",
           "action": "create",
           "message": null,
           "project_id": "89655fe61c4c4a08b9f3e7f9095441b8",
           "events": [
               {
                   "finish_time": "2014-12-11T02:17:58.000000",
                   "start_time": "2014-12-11T02:17:50.000000",
                   "traceback": null,
                   "event": "compute_build_and_run_instance",
                   "result": "Success"
               }
           ]
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
