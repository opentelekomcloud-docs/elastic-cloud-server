:original_name: en-us_topic_0065817701.html

.. _en-us_topic_0065817701:

Deleting a Security Group (Discarded)
=====================================

Function
--------

This API is used to delete a security group.

This API has been discarded. Use the API described in section "Security Group (OpenStack Neutron APIs) > Deleting a Security Group" in *Virtual Private Network API Reference*.

URI
---

DELETE /v2/{project_id}/os-security-groups/{security_group_id}

DELETE /v2.1/{project_id}/os-security-groups/{security_group_id}

:ref:`Table 1 <en-us_topic_0065817701__en-us_topic_0057972665_table55945983>` describes the parameters in the URI.

.. _en-us_topic_0065817701__en-us_topic_0057972665_table55945983:

.. table:: **Table 1** Parameter description

   +-------------------+-----------+-----------------------------------------------------------------+
   | Parameter         | Mandatory | Description                                                     |
   +===================+===========+=================================================================+
   | project_id        | Yes       | Specifies the project ID.                                       |
   +-------------------+-----------+-----------------------------------------------------------------+
   | security_group_id | Yes       | Specifies the security group ID, which is specified in the URI. |
   +-------------------+-----------+-----------------------------------------------------------------+

Request
-------

None

Response
--------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{endpoint}/v2/bb1118612ba64af3a6ea63a1bdcaa5ae/os-security-groups/81f1d23b-b1e2-42cd-bdee-359b4a065a42
   DELETE https://{endpoint}/v2.1/bb1118612ba64af3a6ea63a1bdcaa5ae/os-security-groups/81f1d23b-b1e2-42cd-bdee-359b4a065a42

Example Response
----------------

None

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
