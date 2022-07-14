:original_name: en-us_topic_0067600148.html

.. _en-us_topic_0067600148:

Querying Automatic Recovery of an ECS (Discarded)
=================================================

Function
--------

This API is used to query automatic recovery configured for an ECS.

URI
---

GET /v1/{project_id}/cloudservers/{server_id}/autorecovery

:ref:`Table 1 <en-us_topic_0067600148__table32475667>` describes the parameters in the URI.

.. _en-us_topic_0067600148__table32475667:

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

:ref:`Table 2 <en-us_topic_0067600148__en-us_topic_0057973216_table30138413>` describes the response parameters.

.. _en-us_topic_0067600148__en-us_topic_0057973216_table30138413:

.. table:: **Table 2** Response parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                   |
   +=======================+=======================+===============================================================================+
   | support_auto_recovery | String                | Queries automatic recovery configured for an ECS.                             |
   |                       |                       |                                                                               |
   |                       |                       | -  **true**: indicates that automatic recovery is configured for an ECS.      |
   |                       |                       | -  **false**: indicates that automatic recovery is not configured for an ECS. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+

Example Request
---------------

None

Example Response
----------------

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/autorecovery

.. code-block::

   {
      "support_auto_recovery": "true"
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
