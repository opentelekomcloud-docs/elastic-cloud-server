:original_name: en-us_topic_0020212663.html

.. _en-us_topic_0020212663:

Adding NICs to an ECS in a Batch
================================

Function
--------

This API is used to add one or multiple NICs to an ECS.

This API is an asynchronous API. After the NIC addition request is successfully delivered, a job ID is returned. This does not mean the NIC addition is complete. You need to call the API by referring to :ref:`Querying Job Execution Status <en-us_topic_0022225398>` to query the job status. The SUCCESS status indicates that the NIC addition is successful.

Constraints
-----------

Do not detach or delete the NICs that are being added.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/nics

:ref:`Table 1 <en-us_topic_0020212663__table54800025>` describes the parameters in the URI.

.. _en-us_topic_0020212663__table54800025:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+---------------------------+
   | Parameter             | Mandatory             | Description               |
   +=======================+=======================+===========================+
   | project_id            | Yes                   | **Definition**            |
   |                       |                       |                           |
   |                       |                       | Specifies the project ID. |
   |                       |                       |                           |
   |                       |                       | **Constraints**           |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Range**                 |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Default Value**         |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   +-----------------------+-----------------------+---------------------------+
   | server_id             | Yes                   | **Definition**            |
   |                       |                       |                           |
   |                       |                       | Specifies the ECS ID.     |
   |                       |                       |                           |
   |                       |                       | **Constraints**           |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Range**                 |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Default Value**         |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   +-----------------------+-----------------------+---------------------------+

Request
-------

:ref:`Table 2 <en-us_topic_0020212663__table23831236>` describes the request parameters.

.. _en-us_topic_0020212663__table23831236:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                              |
   +=================+=================+==================+==========================================================================================================+
   | nics            | Yes             | Array of objects | **Definition**                                                                                           |
   |                 |                 |                  |                                                                                                          |
   |                 |                 |                  | Specifies the NICs to be added. For details, see :ref:`Table 3 <en-us_topic_0020212663__table58396974>`. |
   |                 |                 |                  |                                                                                                          |
   |                 |                 |                  | **Constraints**                                                                                          |
   |                 |                 |                  |                                                                                                          |
   |                 |                 |                  | N/A                                                                                                      |
   |                 |                 |                  |                                                                                                          |
   |                 |                 |                  | **Range**                                                                                                |
   |                 |                 |                  |                                                                                                          |
   |                 |                 |                  | N/A                                                                                                      |
   |                 |                 |                  |                                                                                                          |
   |                 |                 |                  | **Default Value**                                                                                        |
   |                 |                 |                  |                                                                                                          |
   |                 |                 |                  | N/A                                                                                                      |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212663__table58396974:

.. table:: **Table 3** **nics** field description

   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                 |
   +=================+=================+==================+=============================================================================================================================================+
   | subnet_id       | Yes             | String           | **Definition**                                                                                                                              |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | Specifies the information about the NICs to be added to an ECS.                                                                             |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | The value must be the ID of a created network in UUID format.                                                                               |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Constraints**                                                                                                                             |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | N/A                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Range**                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | N/A                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Default Value**                                                                                                                           |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | N/A                                                                                                                                         |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | security_groups | No              | Array of objects | **Definition**                                                                                                                              |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | Specifies the security groups for NICs. For details, see :ref:`Table 4 <en-us_topic_0020212663__table16100147>`.                            |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Constraints**                                                                                                                             |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | N/A                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Range**                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | N/A                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Default Value**                                                                                                                           |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | N/A                                                                                                                                         |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_address      | No              | String           | **Definition**                                                                                                                              |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | Specifies the IP address.                                                                                                                   |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Constraints**                                                                                                                             |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | N/A                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Range**                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | If this parameter is empty, the IP address is automatically assigned.                                                                       |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Default Value**                                                                                                                           |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | N/A                                                                                                                                         |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | ipv6_enable     | No              | Boolean          | **Definition**                                                                                                                              |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | Specifies whether IPv6 is supported.                                                                                                        |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Constraints**                                                                                                                             |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | N/A                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Range**                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | If this parameter is set to **true**, the NIC supports IPv6.                                                                                |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Default Value**                                                                                                                           |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | N/A                                                                                                                                         |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | ipv6_bandwidth  | No              | Object           | **Definition**                                                                                                                              |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | Specifies the bound shared bandwidth. For details, see :ref:`ipv6_bandwidth Field Description <en-us_topic_0167957246__section2872318176>`. |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Constraints**                                                                                                                             |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | N/A                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Range**                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | N/A                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | **Default Value**                                                                                                                           |
   |                 |                 |                  |                                                                                                                                             |
   |                 |                 |                  | N/A                                                                                                                                         |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212663__table16100147:

.. table:: **Table 4** **security_groups** field description

   +-----------------+-----------------+-----------------+-----------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                             |
   +=================+=================+=================+=========================================+
   | id              | Yes             | String          | **Definition**                          |
   |                 |                 |                 |                                         |
   |                 |                 |                 | Specifies the ID of the security group. |
   |                 |                 |                 |                                         |
   |                 |                 |                 | **Constraints**                         |
   |                 |                 |                 |                                         |
   |                 |                 |                 | N/A                                     |
   |                 |                 |                 |                                         |
   |                 |                 |                 | **Range**                               |
   |                 |                 |                 |                                         |
   |                 |                 |                 | N/A                                     |
   |                 |                 |                 |                                         |
   |                 |                 |                 | **Default Value**                       |
   |                 |                 |                 |                                         |
   |                 |                 |                 | N/A                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------+

Response
--------

:ref:`Table 5 <en-us_topic_0020212663__table2824153181913>` describes the response parameters.

.. _en-us_topic_0020212663__table2824153181913:

.. table:: **Table 5** Response parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                 |
   +=======================+=======================+=============================================================================================================================================================================================================================================================+
   | job_id                | String                | **Definition**                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                             |
   |                       |                       | Specifies the job ID returned after a job is delivered. The job ID can be used to query the job execution progress. For details about how to query the job execution status based on **job_id**, see :ref:`Job Status Management <en-us_topic_0022225397>`. |
   |                       |                       |                                                                                                                                                                                                                                                             |
   |                       |                       | **Range**                                                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                             |
   |                       |                       | N/A                                                                                                                                                                                                                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

For details about abnormal responses, see :ref:`Responses (Jobs) <en-us_topic_0022067714>`.

Example Request
---------------

Add the NIC whose ID is **d32019d3-bc6e-4319-9c1d-6722fc136a23** and security group ID is **f0ac4394-7e4a-4409-9701-ba8be283dbc3** to an ECS.

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/nics

   {
       "nics": [
           {
               "subnet_id": "d32019d3-bc6e-4319-9c1d-6722fc136a23",
               "security_groups": [
                   {
                       "id": "f0ac4394-7e4a-4409-9701-ba8be283dbc3"
                   }
               ]
           }
       ]
   }

Example Response
----------------

.. code-block::

   {
       "job_id": "ff80808288d41e1b018990260955686a"
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
