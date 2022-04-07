.. _en-us_topic_0067161717:

Deleting a Security Group
=========================

Function
--------

This API is used to delete a security group for an ECS.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

:ref:`Table 1 <en-us_topic_0067161717__table55945983>` describes the parameters in the URI.

.. _en-us_topic_0067161717__table55945983:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0067161717__en-us_topic_0058745339_table44724688204850>` describes the request parameters.

.. _en-us_topic_0067161717__en-us_topic_0058745339_table44724688204850:

.. table:: **Table 2** Request parameter

   +---------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory | Type   | Description                                                                                                                                                  |
   +=====================+===========+========+==============================================================================================================================================================+
   | removeSecurityGroup | Yes       | Object | Specifies the security group to be deleted for an ECS. For details, see :ref:`Table 3 <en-us_topic_0067161717__en-us_topic_0058745339_table59377750205027>`. |
   +---------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0067161717__en-us_topic_0058745339_table59377750205027:

.. table:: **Table 3** **removeSecurityGroup** parameter description

   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                             |
   +===========+===========+========+=========================================================================================================================================+
   | name      | Yes       | String | Specifies the UUID or name of the security group from which the ECS is removed. The configuration takes effect for the NICs on the ECS. |
   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

None

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

.. code-block::

   { 
       "removeSecurityGroup": { 
           "name": "sg-test"
       }
   }

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
