.. _en-us_topic_0065817712:

Deleting a Disk (Discarded)
===========================

Function
--------

This API is used to delete a specified disk.

This API has been discarded. Use the EVS API "Deleting an EVS Disk (OpenStack Cinder API v2)".

Constraints
-----------

-  If the volume has a snapshot not deleted, the volume cannot be deleted.
-  A volume that is being attached to an ECS cannot be deleted.
-  A volume that is being migrated cannot be deleted.
-  Only a volume in the available, error, error_restoring, or error_extending state can be deleted.

URI
---

DELETE /v2/{project_id}/os-volumes/{volume_id}

DELETE /v2.1/{project_id}/os-volumes/{volume_id}

:ref:`Table 1 <en-us_topic_0065817712__en-us_topic_0057973213_table2814978410562>` describes the parameters in the URI.

.. _en-us_topic_0065817712__en-us_topic_0057973213_table2814978410562:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   volume_id  Yes       Specifies the volume ID.
   ========== ========= =========================

Request
-------

None

Response
--------

None

Example Request
---------------

.. code-block::

   DELETE https://{endpoint}/v2/b84c367e4d1047fc9b54f28b400ddbc2/os-volumes/0cf90bab-c513-46df-8559-45ba6de80e3f
   DELETE https://{endpoint}/v2.1/b84c367e4d1047fc9b54f28b400ddbc2/os-volumes/0cf90bab-c513-46df-8559-45ba6de80e3f

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
