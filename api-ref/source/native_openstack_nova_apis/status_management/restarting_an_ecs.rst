:original_name: en-us_topic_0020212650.html

.. _en-us_topic_0020212650:

Restarting an ECS
=================

Function
--------

This API is used to restart a single ECS.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

:ref:`Table 1 <en-us_topic_0020212650__table62669527>` describes the parameters in the URI.

.. _en-us_topic_0020212650__table62669527:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0020212650__table37818817>` describes the request parameters.

.. _en-us_topic_0020212650__table37818817:

.. table:: **Table 2** Request parameters

   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                |
   +===========+===========+========+============================================================================================================================+
   | reboot    | Yes       | Object | Specifies the operation to restart the ECS. For details, see :ref:`Table 3 <en-us_topic_0020212650__table10346346162744>`. |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212650__table10346346162744:

.. table:: **Table 3** **reboot** field description

   +-----------------+-----------------+-----------------+----------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                  |
   +=================+=================+=================+==============================================+
   | type            | Yes             | String          | Specifies the type of the restart operation. |
   |                 |                 |                 |                                              |
   |                 |                 |                 | -  **SOFT**: soft restart                    |
   |                 |                 |                 | -  **HARD**: forcible restart (hard restart) |
   +-----------------+-----------------+-----------------+----------------------------------------------+

Response
--------

None

Example Request
---------------

Restart a specified ECS.

.. code-block:: text

   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

   {
       "reboot": {
           "type": "SOFT"
       }
   }

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
