:original_name: en-us_topic_0122110044.html

.. _en-us_topic_0122110044:

Updating ECS Metadata
=====================

Function
--------

This API is used to update ECS metadata.

-  If the metadata does not contain the field to be updated, the field is automatically added.
-  If the metadata contains the field to be updated, the field value is automatically updated.
-  If the field in the metadata is not requested, the field value remains unchanged.

.. note::

   If the metadata contains sensitive data, take appropriate measures to protect the sensitive data, for example, controlling access permissions and encrypting the data.

Constraints
-----------

An ECS must be in active, stopped, paused, or suspended state, which is specified by **OS-EXT-STS:vm_state**.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/metadata

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

Request
-------

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type               | Description                                                                                                                                                                             |
   +=================+=================+====================+=========================================================================================================================================================================================+
   | metadata        | Yes             | Map<String,String> | **Definition**                                                                                                                                                                          |
   |                 |                 |                    |                                                                                                                                                                                         |
   |                 |                 |                    | This API is used to update ECS metadata.                                                                                                                                                |
   |                 |                 |                    |                                                                                                                                                                                         |
   |                 |                 |                    | You can use metadata to customize key-value pairs. For details about reserved key-value pairs, see :ref:`Table 9 <en-us_topic_0167957246__table2373623012315>`.                         |
   |                 |                 |                    |                                                                                                                                                                                         |
   |                 |                 |                    | **Constraints**                                                                                                                                                                         |
   |                 |                 |                    |                                                                                                                                                                                         |
   |                 |                 |                    | If the metadata contains sensitive data, take appropriate measures to protect the sensitive data, for example, controlling access permissions and encrypting the data.                  |
   |                 |                 |                    |                                                                                                                                                                                         |
   |                 |                 |                    | **Range**                                                                                                                                                                               |
   |                 |                 |                    |                                                                                                                                                                                         |
   |                 |                 |                    | -  A metadata key consists of 1 to 255 characters and can only contain uppercase letters, lowercase letters, digits, spaces, hyphens (-), underscores (_), colons (:), and periods (.). |
   |                 |                 |                    | -  A metadata value consists of a maximum of 255 characters.                                                                                                                            |
   |                 |                 |                    |                                                                                                                                                                                         |
   |                 |                 |                    | **Default Value**                                                                                                                                                                       |
   |                 |                 |                    |                                                                                                                                                                                         |
   |                 |                 |                    | N/A                                                                                                                                                                                     |
   +-----------------+-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

.. table:: **Table 3** Parameter description

   +-----------------------+-----------------------+-----------------------------------------------------+
   | Parameter             | Type                  | Description                                         |
   +=======================+=======================+=====================================================+
   | metadata              | Object                | **Definition**                                      |
   |                       |                       |                                                     |
   |                       |                       | Specifies the user-defined metadata key-value pair. |
   |                       |                       |                                                     |
   |                       |                       | **Range**                                           |
   |                       |                       |                                                     |
   |                       |                       | N/A                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------+

Example Request
---------------

Updated the metadata of an ECS with the user-defined metadata key-value pair.

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/metadata

   {
       "metadata": {
           "key": "value"
       }
   }

Example Response
----------------

.. code-block::

   {
       "metadata":{
           "key":"value"
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
