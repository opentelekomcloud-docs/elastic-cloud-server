:original_name: en-us_topic_0020212666.html

.. _en-us_topic_0020212666:

Deleting a NIC from an ECS
==========================

Function
--------

This API is used to delete a NIC from an ECS based on the port ID.

Constraints
-----------

The primary NIC of an ECS has routing rules configured and cannot be deleted.

When an ECS NIC is detached, all NICs attached to the ECS through the OpenStack Nova API will be deleted.

URI
---

DELETE /v2.1/{project_id}/servers/{server_id}/os-interface/{port_id}{?reserve_port}

DELETE /v2/{project_id}/servers/{server_id}/os-interface/{port_id}{?reserve_port}

:ref:`Table 1 <en-us_topic_0020212666__table34333880>` describes the parameters in the URI.

.. _en-us_topic_0020212666__table34333880:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                  |
   +=======================+=======================+==============================================================================================+
   | project_id            | Yes                   | Specifies the project ID.                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+
   | server_id             | Yes                   | Specifies the ECS ID.                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+
   | port_id               | Yes                   | Specifies the port ID of the NIC.                                                            |
   |                       |                       |                                                                                              |
   |                       |                       | .. note::                                                                                    |
   |                       |                       |                                                                                              |
   |                       |                       |    When the ID is the same as the ECS primary NIC ID, the system will return error code 403. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+
   | reserve_port          | No                    | Indicates whether to retain the NIC port after the NIC is unbound.                           |
   |                       |                       |                                                                                              |
   |                       |                       | **True**: indicates that the port is reserved.                                               |
   |                       |                       |                                                                                              |
   |                       |                       | **False**: indicates that the port is deleted. This is the default value.                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{endpoint}/v2/{project_id}/servers/{server_id}/os-interface/{port_id}
   DELETE https://{endpoint}/v2.1/{project_id}/servers/{server_id}/os-interface/{port_id}

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
