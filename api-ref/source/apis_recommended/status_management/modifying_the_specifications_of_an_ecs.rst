:original_name: en-us_topic_0020212653.html

.. _en-us_topic_0020212653:

Modifying the Specifications of an ECS
======================================

Function
--------

ECS specifications can be modified, for example, upgrading the vCPUs and memory, to meet service requirements. This API is used to modify ECS specifications.

This API is an asynchronous API. After the specifications modification request is successfully delivered, a job ID is returned. This does not mean the modification is complete. You need to call the API by referring to :ref:`Querying Task Execution Status <en-us_topic_0022225398>` to query the job status. The SUCCESS status indicates that the modification is successful.

An ECS flavor cannot be changed to certain flavors. For details, see :ref:`Querying the Target Flavors to Which an ECS Flavor Can Be Changed <en-us_topic_0110472767>`.

Constraints
-----------

-  You can modify the ECS specifications only when the ECS is stopped.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/resize

:ref:`Table 1 <en-us_topic_0020212653__table29396722>` describes the parameters in the URI.

.. _en-us_topic_0020212653__table29396722:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0020212653__table6742880>` describes the request parameters.

.. _en-us_topic_0020212653__table6742880:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================+
   | resize          | Yes             | Object          | Specifies the operation to modify ECS specifications. For details, see :ref:`Table 3 <en-us_topic_0020212653__table7657338>`.           |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | dry_run         | No              | Boolean         | Specifies whether to only check the request and not modify the ECS specifications.                                                      |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | **true**: The request is sent and the ECS specifications are not modified. Check items include mandatory parameters and request format. |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | -  If the check fails, the system returns an error.                                                                                     |
   |                 |                 |                 | -  If the check is successful, the system returns status code 202.                                                                      |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | **false**: The request is sent and the ECS specifications will be modified after the check is passed.                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212653__table7657338:

.. table:: **Table 3** **resize** field description

   +-----------+-----------+--------+------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                |
   +===========+===========+========+============================================================+
   | flavorRef | Yes       | String | Specifies the flavor ID of the ECS after the modification. |
   +-----------+-----------+--------+------------------------------------------------------------+

Response
--------

See :ref:`Responses (Task) <en-us_topic_0022067714>`.

Example Request
---------------

Change the ECS flavor to c3.15xlarge.2.

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/resize

   {
       "resize": {
           "flavorRef": "c3.15xlarge.2"
       }
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
