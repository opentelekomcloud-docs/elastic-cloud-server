.. _en-us_topic_0028714263:

Rolling Back ECS Specifications Modification
============================================

Function
--------

This API is used to roll back ECS specifications modification.

Constraints
-----------

After the rollback, the data modified during migration will be lost.

Before calling this API, ensure that the ECS status (which can be queried using the API for querying details about the ECS) meets the following requirements:

OS-EXT-STS:vm_state=resized

OS-EXT-STS:task_state=""

status=VERIFY_RESIZE

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

:ref:`Table 1 <en-us_topic_0028714263__table60562285165259>` describes the parameters in the URI.

.. _en-us_topic_0028714263__table60562285165259:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0028714263__table7412452165259>` describes the request parameters.

.. _en-us_topic_0028714263__table7412452165259:

.. table:: **Table 2** Request parameters

   +--------------+-----------+------+--------------------------------------------------------------+
   | Parameter    | Mandatory | Type | Description                                                  |
   +==============+===========+======+==============================================================+
   | revertResize | Yes       | Null | Confirms the rollback of the ECS specification modification. |
   +--------------+-----------+------+--------------------------------------------------------------+

Response
--------

None

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2/{project_id}/servers/{server_id}/action
   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

.. code-block::

   {
       "revertResize" : null
   }

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
