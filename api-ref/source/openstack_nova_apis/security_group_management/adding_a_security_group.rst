:original_name: en-us_topic_0067161469.html

.. _en-us_topic_0067161469:

Adding a Security Group
=======================

Function
--------

This API is used to add an ECS to a security group.

You are suggested to add an ECS to a maximum of five security groups.

URI
---

POST /v2.1/{project_id}/servers/{server_id}/action

POST /v2/{project_id}/servers/{server_id}/action

:ref:`Table 1 <en-us_topic_0067161469__table55945983>` describes the parameters in the URI.

.. _en-us_topic_0067161469__table55945983:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0067161469__en-us_topic_0058745339_table44724688204850>` describes the request parameters.

.. _en-us_topic_0067161469__en-us_topic_0058745339_table44724688204850:

.. table:: **Table 2** Request parameter

   +------------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory | Type   | Description                                                                                                                                                |
   +==================+===========+========+============================================================================================================================================================+
   | addSecurityGroup | Yes       | Object | Specifies the security group where the ECS is added. For details, see :ref:`Table 3 <en-us_topic_0067161469__en-us_topic_0058745339_table59377750205027>`. |
   +------------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0067161469__en-us_topic_0058745339_table59377750205027:

.. table:: **Table 3** **addSecurityGroup** parameter description

   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                         |
   +===========+===========+========+=====================================================================================================================================+
   | name      | Yes       | String | Specifies the UUID or name of the security group to which the ECS is added. The configuration takes effect for the NICs on the ECS. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

None

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/action

.. code-block::

   {
       "addSecurityGroup": {
           "name": "sg-test"
       }
   }

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
