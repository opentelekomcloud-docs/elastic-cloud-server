:original_name: en-us_topic_0132905656.html

.. _en-us_topic_0132905656:

Cold Migrating an ECS
=====================

Function
--------

-  An ECS deployed on a DeH can be migrated to another DeH.
-  An ECS deployed on a DeH can be migrated to a public resource pool.
-  An ECS deployed in a public resource pool can be migrated to a DeH.

This API is an asynchronous API. After the cold migration request is successfully delivered, a job ID is returned. This does not mean the cold migration is complete. You need to call the API by referring to :ref:`Querying Task Execution Status <en-us_topic_0022225398>` to query the job status. The SUCCESS status indicates that the cold migration is successful.

.. note::

   If the migration does not cross NUMA nodes, the migration may fail due to insufficient resources on a single NUMA node.

Constraints
-----------

-  Currently, this API applies only to dedicated hosts.
-  Only a stopped ECS can be cold migrated.
-  Existing constraints of the native cold migration API are inherited.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/migrate

:ref:`Table 1 <en-us_topic_0132905656__table29396722>` describes the parameters in the URI.

.. _en-us_topic_0132905656__table29396722:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0132905656__table6742880>` describes the request parameters.

.. _en-us_topic_0132905656__table6742880:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                               |
   +=================+=================+=================+===========================================================================================================+
   | migrate         | Yes             | Object          | Specifies the ECS to be migrated. For details, see :ref:`Table 3 <en-us_topic_0132905656__table7657338>`. |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | This parameter is **null** when you migrate an ECS from a dedicated host to a public resource pool.       |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0132905656__table7657338:

.. table:: **Table 3** **migrate** field description

   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                               |
   +===================+=================+=================+===========================================================================================================+
   | dedicated_host_id | No              | String          | Specifies the DeH ID.                                                                                     |
   |                   |                 |                 |                                                                                                           |
   |                   |                 |                 | This parameter takes effect when an ECS is migrated from a public resource pool to a DeH or between DeHs. |
   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+

Response
--------

See :ref:`Responses (Task) <en-us_topic_0022067714>`.

Example Request
---------------

Migrate the ECS from the public resource pool to the DeH whose ID is **459a2b9d-804a-4745-ab19-a113bb1b4ddc**.

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/migrate

   {
       "migrate": {
           "dedicated_host_id": "459a2b9d-804a-4745-ab19-a113bb1b4ddc"
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
