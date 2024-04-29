:original_name: en-us_topic_0020212652.html

.. _en-us_topic_0020212652:

Stopping an ECS
===============

Function
--------

This API is used to stop a single ECS.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

:ref:`Table 1 <en-us_topic_0020212652__table52155720>` describes the parameters in the URI.

.. _en-us_topic_0020212652__table52155720:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0020212652__table54550461>` describes the request parameters.

.. _en-us_topic_0020212652__table54550461:

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                             |
   +===========+===========+========+=========================================================================================================================+
   | os-stop   | Yes       | Object | Specifies the operation to stop the ECS. For details, see :ref:`Table 3 <en-us_topic_0020212652__table10346346162744>`. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212652__table10346346162744:

.. table:: **Table 3** **os-stop** field description

   +-----------------+-----------------+-----------------+------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                |
   +=================+=================+=================+============================================================+
   | type            | No              | String          | Specifies an ECS stop type. The default value is **SOFT**. |
   |                 |                 |                 |                                                            |
   |                 |                 |                 | -  **SOFT**: normal ECS stop                               |
   |                 |                 |                 | -  **HARD**: forcible ECS stop                             |
   +-----------------+-----------------+-----------------+------------------------------------------------------------+

Response
--------

None

Example Request
---------------

Stop a specified ECS.

.. code-block:: text

   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

   {
       "os-stop": {}
   }

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
