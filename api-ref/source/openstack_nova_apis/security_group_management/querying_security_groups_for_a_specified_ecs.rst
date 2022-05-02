:original_name: en-us_topic_0065817702.html

.. _en-us_topic_0065817702:

Querying Security Groups for a Specified ECS
============================================

Function
--------

This API is used to query security groups for a specified ECS.

URI
---

GET /v2.1/{project_id}/servers/{server_id}/os-security-groups

GET /v2/{project_id}/servers/{server_id}/os-security-groups

:ref:`Table 1 <en-us_topic_0065817702__en-us_topic_0057972666_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0065817702__en-us_topic_0057972666_table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

None

Response
--------

:ref:`Table 2 <en-us_topic_0065817702__en-us_topic_0057972666_table35383970>` describes the response parameters.

.. _en-us_topic_0065817702__en-us_topic_0057972666_table35383970:

.. table:: **Table 2** Response parameters

   +-----------------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type             | Description                                                                                                                |
   +=================+===========+==================+============================================================================================================================+
   | security_groups | Yes       | Array of objects | Specifies security groups. For details, see :ref:`Table 3 <en-us_topic_0065817702__en-us_topic_0057972666_table19346796>`. |
   +-----------------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817702__en-us_topic_0057972666_table19346796:

.. table:: **Table 3** **security_group** objects

   +-------------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type             | Description                                                                                                                     |
   +=============+===========+==================+=================================================================================================================================+
   | description | Yes       | String           | Specifies information about a security group. It must contain 0 to 255 characters.                                              |
   +-------------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | id          | Yes       | String           | Specifies the security group ID in UUID format.                                                                                 |
   +-------------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | name        | Yes       | String           | Specifies the security group name. It must contain 0 to 255 characters.                                                         |
   +-------------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | rules       | Yes       | Array of objects | Specifies security group rules. For details, see :ref:`Table 4 <en-us_topic_0065817702__en-us_topic_0057972666_table44319244>`. |
   +-------------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id   | Yes       | String           | Specifies the tenant or project ID.                                                                                             |
   +-------------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817702__en-us_topic_0057972666_table44319244:

.. table:: **Table 4** **security_group_rule** objects

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================================================================================+
   | parent_group_id | Yes             | String          | Specifies the associated security group ID in UUID format.                                                                                                                                              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_protocol     | Yes             | String          | Specifies the protocol type or the IP protocol number. The value can be **icmp**, **tcp**, **udp**, or the IP protocol number.                                                                          |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | from_port       | Yes             | Integer         | Specifies the start port number. The value ranges from 1 to 65,535 and cannot be greater than **to_port**.                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | When **ip_protocol** is **icmp**, this parameter specifies a port type with a length from 0 to 255 characters.                                                                                          |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | to_port         | Yes             | Integer         | Specifies the stop port number. The value ranges from 1 to 65,535 and cannot be less than **from_port**.                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | When **ip_protocol** is **icmp**, it specifies the code. The value ranges from 0 to 255. If both **from_port** and **to_port** are **-1**, any ICMP packet can be transmitted.                          |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_range        | Yes             | Object          | Specifies the peer IP segment in CIDR format. For details, see :ref:`Table 5 <en-us_topic_0065817702__en-us_topic_0057972666_table4101480163218>`.                                                      |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | The value of **ip_range** or **group** must be empty.                                                                                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group           | Yes             | Object          | Specifies the name of the peer security group and the ID of the tenant in the peer security group. For details, see :ref:`Table 6 <en-us_topic_0065817702__en-us_topic_0057972666_table9527961163416>`. |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | The value of **ip_range** or **group** must be empty.                                                                                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id              | Yes             | String          | Specifies the security group rule ID in UUID format.                                                                                                                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817702__en-us_topic_0057972666_table4101480163218:

.. table:: **Table 5** **ip_range** objects

   ========= ========= ====== =============================================
   Parameter Mandatory Type   Description
   ========= ========= ====== =============================================
   cidr      No        String Specifies the peer IP segment in CIDR format.
   ========= ========= ====== =============================================

.. _en-us_topic_0065817702__en-us_topic_0057972666_table9527961163416:

.. table:: **Table 6** **group** objects

   +-----------+-----------+--------+------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                |
   +===========+===========+========+============================================================+
   | tenant_id | No        | String | Specifies the ID of the tenant of the peer security group. |
   +-----------+-----------+--------+------------------------------------------------------------+
   | name      | No        | String | Specifies the name of the peer security group.             |
   +-----------+-----------+--------+------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v2/e73621affb8f44e1bc01898747ca09d4/servers/65fae4c2-3a09-46c6-af12-3b04f1fdba1e/os-security-groups
   GET https://{endpoint}/v2.1/e73621affb8f44e1bc01898747ca09d4/servers/65fae4c2-3a09-46c6-af12-3b04f1fdba1e/os-security-groups

Example Response
----------------

.. code-block::

   {
       "security_groups": [
           {
               "rules": [
                   {
                       "from_port": null,
                       "group": {
                           "tenant_id": "bb1118612ba64af3a6ea63a1bdcaa5ae",
                           "name": "default"
                       },
                       "ip_protocol": null,
                       "to_port": null,
                       "parent_group_id": "bc4ac1d1-dc77-4b7d-a97d-af86eb0dc450",
                       "ip_range": {},
                       "id": "bb3cc988-e06a-49f6-b668-600e8bf193ee"
                   },
                   {
                       "from_port": null,
                       "group": {
                           "tenant_id": "bb1118612ba64af3a6ea63a1bdcaa5ae",
                           "name": "default"
                       },
                       "ip_protocol": null,
                       "to_port": null,
                       "parent_group_id": "bc4ac1d1-dc77-4b7d-a97d-af86eb0dc450",
                       "ip_range": {},
                       "id": "f9371051-d7e1-4be4-8748-77b1e0913730"
                   }
               ],
               "tenant_id": "bb1118612ba64af3a6ea63a1bdcaa5ae",
               "description": "default",
               "id": "bc4ac1d1-dc77-4b7d-a97d-af86eb0dc450",
               "name": "default"
           },
           {
               "rules": [
                   {
                       "from_port": 200,
                       "group": {},
                       "ip_protocol": "tcp",
                       "to_port": 400,
                       "parent_group_id": "b3e4b615-a40f-4e1c-92af-2e0d382141d5",
                       "ip_range": {
                           "cidr": "0.0.0.0/0"
                       },
                       "id": "3330120d-bbd1-4a73-bda9-0196a84d5670"
                   },
                   {
                       "from_port": 201,
                       "group": {},
                       "ip_protocol": "tcp",
                       "to_port": 400,
                       "parent_group_id": "b3e4b615-a40f-4e1c-92af-2e0d382141d5",
                       "ip_range": {
                           "cidr": "0.0.0.0/0"
                       },
                       "id": "b550c9a6-970a-462d-984e-265e88020818"
                   }
               ],
               "tenant_id": "bb1118612ba64af3a6ea63a1bdcaa5ae",
               "description": "desc-sg",
               "id": "b3e4b615-a40f-4e1c-92af-2e0d382141d5",
               "name": "test-sg"
           }
       ]
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
