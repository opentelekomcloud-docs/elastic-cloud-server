:original_name: en-us_topic_0230783964.html

.. _en-us_topic_0230783964:

Updating NIC Attachment Information of an ECS
=============================================

Function
--------

This API is used to update the NIC attachment information of an ECS. Currently, only **delete_on_termination** can be updated.

URI
---

PUT /v1/{project_id}/cloudservers/{server_id}/os-interface/{port_id}

:ref:`Table 1 <en-us_topic_0230783964__table15447181641516>` describes the parameters in the URI.

.. _en-us_topic_0230783964__table15447181641516:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+---------------------------+
   | Parameter             | Mandatory             | Description               |
   +=======================+=======================+===========================+
   | project_id            | Yes                   | **Definition**            |
   |                       |                       |                           |
   |                       |                       | Specifies the project ID. |
   |                       |                       |                           |
   |                       |                       | **Constraints**           |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Range**                 |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Default Value**         |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   +-----------------------+-----------------------+---------------------------+
   | server_id             | Yes                   | **Definition**            |
   |                       |                       |                           |
   |                       |                       | Specifies the ECS ID.     |
   |                       |                       |                           |
   |                       |                       | **Constraints**           |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Range**                 |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Default Value**         |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   +-----------------------+-----------------------+---------------------------+
   | port_id               | Yes                   | **Definition**            |
   |                       |                       |                           |
   |                       |                       | Specifies the NIC ID.     |
   |                       |                       |                           |
   |                       |                       | **Constraints**           |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Range**                 |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   |                       |                       |                           |
   |                       |                       | **Default Value**         |
   |                       |                       |                           |
   |                       |                       | N/A                       |
   +-----------------------+-----------------------+---------------------------+

Request
-------

:ref:`Table 2 <en-us_topic_0230783964__table184471161152>` describes the request parameters.

.. _en-us_topic_0230783964__table184471161152:

.. table:: **Table 2** Request parameters

   +----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory       | Type            | Description                                                                                                                                       |
   +======================+=================+=================+===================================================================================================================================================+
   | interface_attachment | Yes             | Object          | **Definition**                                                                                                                                    |
   |                      |                 |                 |                                                                                                                                                   |
   |                      |                 |                 | Specifies the structure of the ECS NIC information to be updated. For details, see :ref:`Table 3 <en-us_topic_0230783964__table144481416121516>`. |
   |                      |                 |                 |                                                                                                                                                   |
   |                      |                 |                 | **Constraints**                                                                                                                                   |
   |                      |                 |                 |                                                                                                                                                   |
   |                      |                 |                 | N/A                                                                                                                                               |
   |                      |                 |                 |                                                                                                                                                   |
   |                      |                 |                 | **Range**                                                                                                                                         |
   |                      |                 |                 |                                                                                                                                                   |
   |                      |                 |                 | N/A                                                                                                                                               |
   |                      |                 |                 |                                                                                                                                                   |
   |                      |                 |                 | **Default Value**                                                                                                                                 |
   |                      |                 |                 |                                                                                                                                                   |
   |                      |                 |                 | N/A                                                                                                                                               |
   +----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0230783964__table144481416121516:

.. table:: **Table 3** **interface_attachment** data structure

   +-----------------------+-----------------+-----------------+------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                          |
   +=======================+=================+=================+======================================================+
   | delete_on_termination | Yes             | Boolean         | **Definition**                                       |
   |                       |                 |                 |                                                      |
   |                       |                 |                 | Specifies whether to delete a NIC when detaching it. |
   |                       |                 |                 |                                                      |
   |                       |                 |                 | **Constraints**                                      |
   |                       |                 |                 |                                                      |
   |                       |                 |                 | N/A                                                  |
   |                       |                 |                 |                                                      |
   |                       |                 |                 | **Range**                                            |
   |                       |                 |                 |                                                      |
   |                       |                 |                 | -  **true**: Delete the NIC.                         |
   |                       |                 |                 | -  **false**: Do not delete the NIC.                 |
   |                       |                 |                 |                                                      |
   |                       |                 |                 | **Default Value**                                    |
   |                       |                 |                 |                                                      |
   |                       |                 |                 | N/A                                                  |
   +-----------------------+-----------------+-----------------+------------------------------------------------------+

Response
--------

None

Example Request
---------------

.. code-block:: text

   PUT  https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/os-interface/{port_id}

   {
       "interface_attachment":
       {
            "delete_on_termination": true
       }
   }

Example Response
----------------

None

Returned Values
---------------

For details, see :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

For details, see :ref:`Error Codes <en-us_topic_0022067717>`.
