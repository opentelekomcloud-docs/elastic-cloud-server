:original_name: en-us_topic_0025560296.html

.. _en-us_topic_0025560296:

Deleting an ECS
===============

Function
--------

This API is used to delete an ECS.

Constraints
-----------

When an ECS is deleted, all NICs attached to the ECS through the OpenStack Nova API will be deleted.

URI
---

DELETE /v2.1/{project_id}/servers/{server_id}

DELETE /v2/{project_id}/servers/{server_id}

:ref:`Table 1 <en-us_topic_0025560296__table2659898791032>` describes the parameters in the URI.

.. _en-us_topic_0025560296__table2659898791032:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

None

Response
--------

None

Example Request
---------------

Delete a specified ECS.

.. code-block:: text

   DELETE https://{endpoint}/v2/{project_id}/servers/{server_id}
   DELETE https://{endpoint}/v2.1/{project_id}/servers/{server_id}

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
