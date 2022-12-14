:original_name: en-us_topic_0020212665.html

.. _en-us_topic_0020212665:

Deleting NICs from an ECS in a Batch
====================================

Function
--------

This API is used to uninstall and delete one or multiple NICs from an ECS.

Constraints
-----------

The primary NIC of an ECS has routing rules configured and cannot be deleted.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/nics/delete

:ref:`Table 1 <en-us_topic_0020212665__table42885739>` describes the parameters in the URI.

.. _en-us_topic_0020212665__table42885739:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0020212665__table35856517>` describes the request parameters.

.. _en-us_topic_0020212665__table35856517:

.. table:: **Table 2** Request parameters

   +-----------+-----------+------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                                |
   +===========+===========+==================+============================================================================================================+
   | nics      | Yes       | Array of objects | Specifies the NICs to be deleted. For details, see :ref:`Table 3 <en-us_topic_0020212665__table43212049>`. |
   +-----------+-----------+------------------+------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020212665__table43212049:

.. table:: **Table 3** **nics** field description

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                  |
   +=================+=================+=================+==============================================================================================+
   | id              | Yes             | String          | Specifies the port ID of the NIC.                                                            |
   |                 |                 |                 |                                                                                              |
   |                 |                 |                 | .. note::                                                                                    |
   |                 |                 |                 |                                                                                              |
   |                 |                 |                 |    When the ID is the same as the ECS primary NIC ID, the system will return error code 403. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+

Response
--------

See :ref:`Responses (Task) <en-us_topic_0022067714>`.

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/nics/delete

.. code-block::

   {
       "nics": [
            {
               "id": "d32019d3-bc6e-4319-9c1d-6722fc136a23"
           }
       ]
   }

Example Response
----------------

.. code-block::

   {
       "job_id": "70a599e0-31e7-49b7-b260-868f441e862b"
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
