:original_name: en-us_topic_0065817692.html

.. _en-us_topic_0065817692:

Querying Operations on an ECS
=============================

Function
--------

This API is used to query all historical operations on an ECS.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/os-instance-actions?limit={limit}&marker={marker}

GET /v2/{project_id}/servers/{server_id}/os-instance-actions?limit={limit}&marker={marker}

:ref:`Table 1 <en-us_topic_0065817692__en-us_topic_0057973177_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0065817692__en-us_topic_0057973177_table32475667:

.. table:: **Table 1** Path parameters

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

.. note::

   Pagination query is supported in microversion 2.58 and later. The query results are displayed by the creation time (**created_at**) of the records in descending order. If the creation time is not provided, the results are displayed by object ID in descending order. The number of records displayed on each page is **limit**. If the value of **limit** exceeds the maximum number configured in Nova, the maximum number configured in Nova is returned.

.. table:: **Table 2** Query parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                 |
   +=======================+=======================+=============================================================================================================================================================+
   | limit                 | No                    | Specifies the upper limit on the number of returned results.                                                                                                |
   |                       |                       |                                                                                                                                                             |
   |                       |                       | This parameter is supported in microversion 2.58 and later.                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker                | No                    | Specifies the marker that points to the server action. The query starts from the next piece of data indexed by this parameter. The value is **request_id**. |
   |                       |                       |                                                                                                                                                             |
   |                       |                       | This parameter is supported in microversion 2.58 and later.                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 3 <en-us_topic_0065817692__en-us_topic_0057973153_table55529076>` describes the response parameters.

.. _en-us_topic_0065817692__en-us_topic_0057973153_table55529076:

.. table:: **Table 3** Response parameters

   +-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Description                                                                                                                               |
   +=================+=================+===========================================================================================================================================+
   | instanceActions | Array of Object | Specifies operations performed on the ECS. For details, see :ref:`Table 4 <en-us_topic_0065817692__en-us_topic_0057973177_table2407422>`. |
   +-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817692__en-us_topic_0057973177_table2407422:

.. table:: **Table 4** **instanceActions** field description

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================================================================================================================================================================================+
   | action          | Yes             | String          | Specifies the action.                                                                                                                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                 | Value range:                                                                                                                                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                 | create, delete, evacuate, restore, stop, start, reboot, rebuild, revertResize, confirmResize, detach_volume, attach_volume, attach_interface, detach_interface, lock, unlock, resize, migrate, pause, unpause, rescue, unrescue, changePassword, shelve, unshelve, live-migration, trigger_crash_dump, extend_volume |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_uuid   | Yes             | String          | Specifies the ECS ID in UUID format.                                                                                                                                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message         | Yes             | String          | Specifies the result status of the operation.                                                                                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id      | Yes             | String          | Specifies the project ID.                                                                                                                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | request_id      | Yes             | String          | Specifies the request ID.                                                                                                                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time      | Yes             | String          | Specifies the time when the action was started.                                                                                                                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_id         | Yes             | String          | Specifies the user ID.                                                                                                                                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Query all historical operations on a specified ECS.

.. code-block:: text

   GET https://{endpoint}/v2/89655fe61c4c4a08b9f3e7f9095441b8/servers/e723eb40-f56e-40f9-8c8c-caa517fe06ba/os-instance-actions
   GET https://{endpoint}/v2.1/89655fe61c4c4a08b9f3e7f9095441b8/servers/e723eb40-f56e-40f9-8c8c-caa517fe06ba/os-instance-actions

Example Response
----------------

.. code-block::

   {
       "instanceActions": [
           {
               "instance_uuid": "e723eb40-f56e-40f9-8c8c-caa517fe06ba",
               "user_id": "752be40780484291a9cc7ae50fff3e6d",
               "start_time": "2014-12-16T10:58:14.000000",
               "request_id": "req-ee56c2b5-d33b-4749-ae83-09281dbbb716",
               "action": "resize",
               "message": "Error",
               "project_id": "89655fe61c4c4a08b9f3e7f9095441b8"
           },
           {
               "instance_uuid": "e723eb40-f56e-40f9-8c8c-caa517fe06ba",
               "user_id": "752be40780484291a9cc7ae50fff3e6d",
               "start_time": "2014-12-16T10:57:56.000000",
               "request_id": "req-23cfd57f-c58a-45cd-86a6-eab3e38f3753",
               "action": "resize",
               "message": "Error",
               "project_id": "89655fe61c4c4a08b9f3e7f9095441b8"
           },
       ]
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
