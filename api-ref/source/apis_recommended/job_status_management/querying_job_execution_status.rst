:original_name: en-us_topic_0022225398.html

.. _en-us_topic_0022225398:

Querying Job Execution Status
=============================

Function
--------

This API is used to query the execution status of an asynchronous job.

After an asynchronous job is issued, for example, creating or deleting an ECS, performing operations on ECSs in a batch, or performing operations on ECS NICs, a job ID (**job_id**) will be returned, based on which you can query the execution status of the job.

For details about how to obtain **job_id**, see :ref:`Responses (Jobs) <en-us_topic_0022067714>`.

URI
---

GET /v1/{project_id}/jobs/{job_id}

:ref:`Table 1 <en-us_topic_0022225398__table6081678163249>` describes the parameters in the URI.

.. _en-us_topic_0022225398__table6081678163249:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                            |
   +=======================+=======================+========================================================================================================+
   | project_id            | Yes                   | **Definition**                                                                                         |
   |                       |                       |                                                                                                        |
   |                       |                       | Specifies the project ID.                                                                              |
   |                       |                       |                                                                                                        |
   |                       |                       | **Constraints**                                                                                        |
   |                       |                       |                                                                                                        |
   |                       |                       | N/A                                                                                                    |
   |                       |                       |                                                                                                        |
   |                       |                       | **Range**                                                                                              |
   |                       |                       |                                                                                                        |
   |                       |                       | N/A                                                                                                    |
   |                       |                       |                                                                                                        |
   |                       |                       | **Default Value**                                                                                      |
   |                       |                       |                                                                                                        |
   |                       |                       | N/A                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+
   | job_id                | Yes                   | **Definition**                                                                                         |
   |                       |                       |                                                                                                        |
   |                       |                       | Specifies the ID of an asynchronous job. It can be obtained from the response of the asynchronous job. |
   |                       |                       |                                                                                                        |
   |                       |                       | **Constraints**                                                                                        |
   |                       |                       |                                                                                                        |
   |                       |                       | N/A                                                                                                    |
   |                       |                       |                                                                                                        |
   |                       |                       | **Range**                                                                                              |
   |                       |                       |                                                                                                        |
   |                       |                       | N/A                                                                                                    |
   |                       |                       |                                                                                                        |
   |                       |                       | **Default Value**                                                                                      |
   |                       |                       |                                                                                                        |
   |                       |                       | N/A                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0022225398__table63003337163851>` describes the response parameters.

.. _en-us_topic_0022225398__table63003337163851:

.. table:: **Table 2** Response parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                            |
   +=======================+=======================+========================================================================================================================================================================================+
   | status                | String                | **Definition**                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | Specifies the job status.                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | **Range**                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | -  **SUCCESS**: The job is successfully executed.                                                                                                                                      |
   |                       |                       | -  **RUNNING**: The job is in progress.                                                                                                                                                |
   |                       |                       | -  **FAIL**: The job failed.                                                                                                                                                           |
   |                       |                       | -  **INIT**: The job is being initialized.                                                                                                                                             |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | entities              | Object                | **Definition**                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | Specifies the object of the job. The displayed information varies depending on what tasks are executed. For details, see :ref:`Table 3 <en-us_topic_0022225398__table63816992163249>`. |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | **Range**                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | -  **server_id**: ECS-related operations                                                                                                                                               |
   |                       |                       | -  **nic_id**: NIC-related operations                                                                                                                                                  |
   |                       |                       | -  If a sub-Job is available, the sub-job details are displayed.                                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_id                | String                | **Definition**                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | Specifies the ID of an asynchronous job.                                                                                                                                               |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | **Range**                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | N/A                                                                                                                                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_type              | String                | **Definition**                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | Specifies the type of an asynchronous job.                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | **Range**                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | Only some common job types are listed below. For the actual job types, see the response.                                                                                               |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | The type is the corresponding asynchronous request API. For example:                                                                                                                   |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | -  createServer: ECS creation                                                                                                                                                          |
   |                       |                       | -  createSingleServer: Single ECS creation                                                                                                                                             |
   |                       |                       | -  resizeServer: ECS resizing (specification modification)                                                                                                                             |
   |                       |                       | -  changeOS: OS change                                                                                                                                                                 |
   |                       |                       | -  reInitOs: OS reinstallation                                                                                                                                                         |
   |                       |                       | -  attachVolume: disk attachment                                                                                                                                                       |
   |                       |                       | -  detachVolume: disk detachment                                                                                                                                                       |
   |                       |                       | -  deleteVMs: ECS deletion                                                                                                                                                             |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | begin_time            | String                | **Definition**                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | Specifies the time when the job was started.                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | **Range**                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | N/A                                                                                                                                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time              | String                | **Definition**                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | Specifies the time when the job was finished.                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | **Range**                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | N/A                                                                                                                                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | **Definition**                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | Specifies the returned error code when the job execution fails.                                                                                                                        |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | **Range**                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | After the job is executed successfully, the value of this parameter is **null**.                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fail_reason           | String                | **Definition**                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | Specifies the cause of the job execution failure.                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | **Range**                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | After the job is executed successfully, the value of this parameter is **null**.                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message               | String                | **Definition**                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | Specifies the error message returned when an error occurs in the request to query a job.                                                                                               |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | **Range**                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | N/A                                                                                                                                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | code                  | String                | **Definition**                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | Specifies the error code returned when an error occurs in the request to query a job.                                                                                                  |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | For details about the error code, see :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.                                                                            |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | **Range**                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | N/A                                                                                                                                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0022225398__table63816992163249:

.. table:: **Table 3** **entities** field description

   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                   |
   +=======================+=======================+===============================================================================+
   | server_id             | String                | **Definition**                                                                |
   |                       |                       |                                                                               |
   |                       |                       | Displayed when the job is ECS-related.                                        |
   |                       |                       |                                                                               |
   |                       |                       | **Range**                                                                     |
   |                       |                       |                                                                               |
   |                       |                       | N/A                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | nic_id                | String                | **Definition**                                                                |
   |                       |                       |                                                                               |
   |                       |                       | If the job is a NIC-related operation, the value is **nic_id**.               |
   |                       |                       |                                                                               |
   |                       |                       | **Range**                                                                     |
   |                       |                       |                                                                               |
   |                       |                       | N/A                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | sub_jobs_total        | Integer               | **Definition**                                                                |
   |                       |                       |                                                                               |
   |                       |                       | Specifies the number of sub-jobs.                                             |
   |                       |                       |                                                                               |
   |                       |                       | **Range**                                                                     |
   |                       |                       |                                                                               |
   |                       |                       | N/A                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | sub_jobs              | Array of objects      | **Definition**                                                                |
   |                       |                       |                                                                               |
   |                       |                       | Specifies the execution information of a sub-job.                             |
   |                       |                       |                                                                               |
   |                       |                       | For details, see :ref:`Table 4 <en-us_topic_0022225398__table1500801817135>`. |
   |                       |                       |                                                                               |
   |                       |                       | **Range**                                                                     |
   |                       |                       |                                                                               |
   |                       |                       | N/A                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+

.. _en-us_topic_0022225398__table1500801817135:

.. table:: **Table 4** **sub_jobs** field description

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                             |
   +=======================+=======================+=========================================================================================================+
   | status                | String                | **Definition**                                                                                          |
   |                       |                       |                                                                                                         |
   |                       |                       | Specifies the job status.                                                                               |
   |                       |                       |                                                                                                         |
   |                       |                       | **Range**                                                                                               |
   |                       |                       |                                                                                                         |
   |                       |                       | -  **SUCCESS**: indicates the job is successfully executed.                                             |
   |                       |                       | -  **RUNNING**: indicates that the job is in progress.                                                  |
   |                       |                       | -  **FAIL**: indicates that the job failed.                                                             |
   |                       |                       | -  **INIT**: indicates that the job is being initialized.                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | entities              | Object                | **Definition**                                                                                          |
   |                       |                       |                                                                                                         |
   |                       |                       | Specifies the object of the job. The displayed information varies depending on what tasks are executed. |
   |                       |                       |                                                                                                         |
   |                       |                       | **Range**                                                                                               |
   |                       |                       |                                                                                                         |
   |                       |                       | -  **server_id**: ECS-related operations                                                                |
   |                       |                       | -  **nic_id**: NIC-related operations                                                                   |
   |                       |                       |                                                                                                         |
   |                       |                       | For details, see :ref:`Table 5 <en-us_topic_0022225398__table2577901102930>`.                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | job_id                | String                | **Definition**                                                                                          |
   |                       |                       |                                                                                                         |
   |                       |                       | Specifies the sub-job ID.                                                                               |
   |                       |                       |                                                                                                         |
   |                       |                       | **Range**                                                                                               |
   |                       |                       |                                                                                                         |
   |                       |                       | N/A                                                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | job_type              | String                | **Definition**                                                                                          |
   |                       |                       |                                                                                                         |
   |                       |                       | Specify the sub-job type.                                                                               |
   |                       |                       |                                                                                                         |
   |                       |                       | **Range**                                                                                               |
   |                       |                       |                                                                                                         |
   |                       |                       | Only some common job types are listed below. For the actual job types, see the response.                |
   |                       |                       |                                                                                                         |
   |                       |                       | The type is the corresponding asynchronous request API. For example:                                    |
   |                       |                       |                                                                                                         |
   |                       |                       | -  createSingleServer: Single ECS creation                                                              |
   |                       |                       | -  resizeServer: ECS resizing (specification modification)                                              |
   |                       |                       | -  attachVolume: disk attachment                                                                        |
   |                       |                       | -  detachVolume: disk detachment                                                                        |
   |                       |                       | -  deleteVM: ECS deletion                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | begin_time            | String                | **Definition**                                                                                          |
   |                       |                       |                                                                                                         |
   |                       |                       | Specifies the time when the job was started.                                                            |
   |                       |                       |                                                                                                         |
   |                       |                       | **Range**                                                                                               |
   |                       |                       |                                                                                                         |
   |                       |                       | N/A                                                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | end_time              | String                | **Definition**                                                                                          |
   |                       |                       |                                                                                                         |
   |                       |                       | Specifies the time when the job was finished.                                                           |
   |                       |                       |                                                                                                         |
   |                       |                       | **Range**                                                                                               |
   |                       |                       |                                                                                                         |
   |                       |                       | N/A                                                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | error_code            | String                | **Definition**                                                                                          |
   |                       |                       |                                                                                                         |
   |                       |                       | Specifies the returned error code when the job execution fails.                                         |
   |                       |                       |                                                                                                         |
   |                       |                       | **Range**                                                                                               |
   |                       |                       |                                                                                                         |
   |                       |                       | After the job is executed successfully, the value of this parameter is null.                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | fail_reason           | String                | **Definition**                                                                                          |
   |                       |                       |                                                                                                         |
   |                       |                       | Specifies the cause of the job execution failure.                                                       |
   |                       |                       |                                                                                                         |
   |                       |                       | **Range**                                                                                               |
   |                       |                       |                                                                                                         |
   |                       |                       | After the job is executed successfully, the value of this parameter is null.                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0022225398__table2577901102930:

.. table:: **Table 5** **sub_jobs.entities** field description

   +-----------------------+-----------------------+-----------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                     |
   +=======================+=======================+=================================================================+
   | server_id             | String                | **Definition**                                                  |
   |                       |                       |                                                                 |
   |                       |                       | Displayed when the job is ECS-related.                          |
   |                       |                       |                                                                 |
   |                       |                       | **Range**                                                       |
   |                       |                       |                                                                 |
   |                       |                       | N/A                                                             |
   +-----------------------+-----------------------+-----------------------------------------------------------------+
   | nic_id                | String                | **Definition**                                                  |
   |                       |                       |                                                                 |
   |                       |                       | If the job is a NIC-related operation, the value is **nic_id**. |
   |                       |                       |                                                                 |
   |                       |                       | **Range**                                                       |
   |                       |                       |                                                                 |
   |                       |                       | N/A                                                             |
   +-----------------------+-----------------------+-----------------------------------------------------------------+
   | errorcode_message     | String                | **Definition**                                                  |
   |                       |                       |                                                                 |
   |                       |                       | Specifies the cause of a sub-job execution failure.             |
   |                       |                       |                                                                 |
   |                       |                       | **Range**                                                       |
   |                       |                       |                                                                 |
   |                       |                       | N/A                                                             |
   +-----------------------+-----------------------+-----------------------------------------------------------------+

Example Request
---------------

Query the execution status of a specified asynchronous job.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/jobs/{job_id}

Example Response
----------------

.. code-block::

   {
       "status": "SUCCESS",
       "entities": {
           "sub_jobs_total": 1,
           "sub_jobs": [
               {
                   "status": "SUCCESS",
                   "entities": {
                       "server_id": "bae51750-0089-41a1-9b18-5c777978ff6d"
                   },
                   "job_id": "2c9eb2c5544cbf6101544f0635672b60",
                   "job_type": "createSingleServer",
                   "begin_time": "2016-04-25T20:04:47.591Z",
                   "end_time": "2016-04-25T20:08:21.328Z",
                   "error_code": null,
                   "fail_reason": null
               }
           ]
       },
       "job_id": "2c9eb2c5544cbf6101544f0602af2b4f",
       "job_type": "createServer",
       "begin_time": "2016-04-25T20:04:34.604Z",
       "end_time": "2016-04-25T20:08:41.593Z",
       "error_code": null,
       "fail_reason": null
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
