:original_name: en-us_topic_0067600284.html

.. _en-us_topic_0067600284:

Managing Automatic Recovery of an ECS (Discarded)
=================================================

Function
--------

This API is used to configure or delete automatic recovery of an ECS.

URI
---

PUT /v1/{project_id}/cloudservers/{server_id}/autorecovery

:ref:`Table 1 <en-us_topic_0067600284__table32475667>` describes the parameters in the URI.

.. _en-us_topic_0067600284__table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0067600284__table10194370103926>` describes the request parameters.

.. _en-us_topic_0067600284__table10194370103926:

.. table:: **Table 2** Request parameters

   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                       |
   +=======================+=================+=================+===================================================================+
   | support_auto_recovery | Yes             | String          | Configures or deletes automatic recovery of an ECS.               |
   |                       |                 |                 |                                                                   |
   |                       |                 |                 | -  **true**: indicates configuring automatic recovery for an ECS. |
   |                       |                 |                 | -  **false**: indicates deleting automatic recovery of an ECS.    |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------+

Response
--------

None

Example Request
---------------

.. code-block:: text

   PUT https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/autorecovery

.. code-block::

   {
       "support_auto_recovery": "true"
   }

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
