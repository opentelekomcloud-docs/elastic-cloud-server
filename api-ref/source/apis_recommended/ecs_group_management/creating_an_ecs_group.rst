:original_name: en-us_topic_0161097718.html

.. _en-us_topic_0161097718:

Creating an ECS Group
=====================

Function
--------

This API is used to create an ECS group.

Constraints
-----------

Only anti-affinity groups are supported.

URI
---

POST /v1/{project_id}/cloudservers/os-server-groups

:ref:`Table 1 <en-us_topic_0161097718__table11729101619308>` describes the parameters in the URI.

.. _en-us_topic_0161097718__table11729101619308:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0161097718__table146581144163019>` describes the request parameters.

.. _en-us_topic_0161097718__table146581144163019:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================+
   | server_group    | Yes             | Object          | **Definition**                                                                                                                       |
   |                 |                 |                 |                                                                                                                                      |
   |                 |                 |                 | Specifies the ECS group information. For details, see :ref:`Table 3 <en-us_topic_0161097718__en-us_topic_0057973153_table19917766>`. |
   |                 |                 |                 |                                                                                                                                      |
   |                 |                 |                 | **Constraints**                                                                                                                      |
   |                 |                 |                 |                                                                                                                                      |
   |                 |                 |                 | N/A                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                      |
   |                 |                 |                 | **Range**                                                                                                                            |
   |                 |                 |                 |                                                                                                                                      |
   |                 |                 |                 | N/A                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                      |
   |                 |                 |                 | **Default Value**                                                                                                                    |
   |                 |                 |                 |                                                                                                                                      |
   |                 |                 |                 | N/A                                                                                                                                  |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0161097718__en-us_topic_0057973153_table19917766:

.. table:: **Table 3** **server_group** parameters

   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                   |
   +=================+=================+==================+===============================================================================+
   | name            | Yes             | String           | **Definition**                                                                |
   |                 |                 |                  |                                                                               |
   |                 |                 |                  | Specifies the ECS group name.                                                 |
   |                 |                 |                  |                                                                               |
   |                 |                 |                  | **Constraints**                                                               |
   |                 |                 |                  |                                                                               |
   |                 |                 |                  | N/A                                                                           |
   |                 |                 |                  |                                                                               |
   |                 |                 |                  | **Range**                                                                     |
   |                 |                 |                  |                                                                               |
   |                 |                 |                  | 1 to 255 characters                                                           |
   |                 |                 |                  |                                                                               |
   |                 |                 |                  | **Default Value**                                                             |
   |                 |                 |                  |                                                                               |
   |                 |                 |                  | N/A                                                                           |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------+
   | policies        | Yes             | Array of strings | **Definition**                                                                |
   |                 |                 |                  |                                                                               |
   |                 |                 |                  | Specifies the list of policies associated with the ECS group.                 |
   |                 |                 |                  |                                                                               |
   |                 |                 |                  | **Constraints**                                                               |
   |                 |                 |                  |                                                                               |
   |                 |                 |                  | N/A                                                                           |
   |                 |                 |                  |                                                                               |
   |                 |                 |                  | **Range**                                                                     |
   |                 |                 |                  |                                                                               |
   |                 |                 |                  | -  **anti-affinity**: ECSs in this group must be deployed on different hosts. |
   |                 |                 |                  |                                                                               |
   |                 |                 |                  | **Default Value**                                                             |
   |                 |                 |                  |                                                                               |
   |                 |                 |                  | N/A                                                                           |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------+

Response
--------

:ref:`Table 4 <en-us_topic_0161097718__table776421293115>` describes the response parameters.

.. _en-us_topic_0161097718__table776421293115:

.. table:: **Table 4** Response parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================+
   | server_group          | Object                | **Definition**                                                                                                                      |
   |                       |                       |                                                                                                                                     |
   |                       |                       | Specifies the ECS group information. For details, see :ref:`Table 5 <en-us_topic_0161097718__en-us_topic_0057973153_table7944126>`. |
   |                       |                       |                                                                                                                                     |
   |                       |                       | **Range**                                                                                                                           |
   |                       |                       |                                                                                                                                     |
   |                       |                       | N/A                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0161097718__en-us_topic_0057973153_table7944126:

.. table:: **Table 5** **server_group** parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                   |
   +=======================+=======================+===============================================================================+
   | id                    | String                | **Definition**                                                                |
   |                       |                       |                                                                               |
   |                       |                       | Specifies the ECS group UUID.                                                 |
   |                       |                       |                                                                               |
   |                       |                       | **Range**                                                                     |
   |                       |                       |                                                                               |
   |                       |                       | N/A                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | name                  | String                | **Definition**                                                                |
   |                       |                       |                                                                               |
   |                       |                       | Specifies the ECS group name.                                                 |
   |                       |                       |                                                                               |
   |                       |                       | **Range**                                                                     |
   |                       |                       |                                                                               |
   |                       |                       | N/A                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | policies              | Array of strings      | **Definition**                                                                |
   |                       |                       |                                                                               |
   |                       |                       | Specifies the list of policies associated with the ECS group.                 |
   |                       |                       |                                                                               |
   |                       |                       | **Range**                                                                     |
   |                       |                       |                                                                               |
   |                       |                       | -  **anti-affinity**: ECSs in this group must be deployed on different hosts. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | members               | Array of strings      | **Definition**                                                                |
   |                       |                       |                                                                               |
   |                       |                       | Specifies the IDs of the ECSs in an ECS group.                                |
   |                       |                       |                                                                               |
   |                       |                       | **Range**                                                                     |
   |                       |                       |                                                                               |
   |                       |                       | N/A                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | metadata              | Object                | **Definition**                                                                |
   |                       |                       |                                                                               |
   |                       |                       | Specifies the ECS group metadata.                                             |
   |                       |                       |                                                                               |
   |                       |                       | **Range**                                                                     |
   |                       |                       |                                                                               |
   |                       |                       | N/A                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+

Example Request
---------------

Create an ECS group.

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/cloudservers/os-server-groups

   {
       "server_group": {
           "name": "test",
           "policies": ["anti-affinity"]
       }
   }

Example Response
----------------

.. code-block::

   {
       "server_group": {
           "id": "5bbcc3c4-1da2-4437-a48a-66f15b1b13f9",
           "name": "test",
           "policies": [
               "anti-affinity"
           ],
           "members": [],
           "metadata": {}
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
