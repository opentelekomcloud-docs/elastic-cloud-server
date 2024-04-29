:original_name: en-us_topic_0020212648.html

.. _en-us_topic_0020212648:

Starting an ECS
===============

Function
--------

This API is used to start a single ECS.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

:ref:`Table 1 <en-us_topic_0020212648__table48630964>` describes the parameters in the URI.

.. _en-us_topic_0020212648__table48630964:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0020212648__table48180537>` describes the request parameters.

.. _en-us_topic_0020212648__table48180537:

.. table:: **Table 2** Request parameters

   +-----------+-----------+------+------------------------------------------------------------------------+
   | Parameter | Mandatory | Type | Description                                                            |
   +===========+===========+======+========================================================================+
   | os-start  | Yes       | Null | Specifies the operation to start the ECS. The data structure is empty. |
   +-----------+-----------+------+------------------------------------------------------------------------+

Response
--------

None

Example Request
---------------

Start a specified ECS.

.. code-block:: text

   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

   {
       "os-start": {}
                       }

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
