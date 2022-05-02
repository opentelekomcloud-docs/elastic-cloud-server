:original_name: en-us_topic_0161097719.html

.. _en-us_topic_0161097719:

Deleting an ECS Group
=====================

Function
--------

This API is used to delete an ECS group.

URI
---

DELETE /v1/{project_id}/cloudservers/os-server-groups/{server_group_id}

:ref:`Table 1 <en-us_topic_0161097719__table1962114910318>` describes the parameters in the URI.

.. _en-us_topic_0161097719__table1962114910318:

.. table:: **Table 1** Parameter description

   =============== ========= =============================
   Parameter       Mandatory Description
   =============== ========= =============================
   project_id      Yes       Specifies the project ID.
   server_group_id Yes       Specifies the ECS group UUID.
   =============== ========= =============================

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{endpoint}/v1/{project_id}/cloudservers/os-server-groups/{server_group_id}

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
