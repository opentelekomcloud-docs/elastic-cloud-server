Querying Security Groups (Discarded)
====================================

Function
--------

This API is used to query security groups.

This API has been discarded. Use the API described in section "Security Group (OpenStack Neutron APIs) > Querying Security Groups" in *Virtual Private Network API Reference*.

URI
---

GET /v2/{project_id}/os-security-groups

GET /v2.1/{project_id}/os-security-groups

`Table 1 <#enustopic0090187679enustopic0057973221table55945983>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0090187679enustopic0057973221table55945983:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

.. note::

   Pagination query is not supported.

Request
-------

N/A

Response
--------

`Table 2 <#enustopic0090187679enustopic0057973221table66376806>`__ describes the response parameters.



.. _ENUSTOPIC0090187679enustopic0057973221table66376806:

.. table:: **Table 2** Response parameters

   +-----------------+------------------+-----------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type             | Description                                                                                                     |
   +=================+==================+=================================================================================================================+
   | security_groups | Array of objects | Specifies security groups. For details, see `Table 3 <#enustopic0090187679enustopic0057973221table12520187>`__. |
   +-----------------+------------------+-----------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0090187679enustopic0057973221table12520187:

.. table:: **Table 3** **security_group** objects

   +-------------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type             | Description                                                                                                          |
   +=============+==================+======================================================================================================================+
   | description | String           | Specifies information about a security group. It must contain 0 to 255 characters.                                   |
   +-------------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | id          | String           | Specifies the security group ID in UUID format.                                                                      |
   +-------------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | name        | String           | Specifies the security group name. It must contain 0 to 255 characters.                                              |
   +-------------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | rules       | Array of objects | Specifies security group rules. For details, see `Table 4 <#enustopic0090187679enustopic0057973221table34485122>`__. |
   +-------------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | tenant_id   | String           | Specifies the tenant or project ID.                                                                                  |
   +-------------+------------------+----------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0090187679enustopic0057973221table34485122:

.. table:: **Table 4** **security_group_rule** objects

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                                                     |
   +=======================+=======================+=================================================================================================================================================================================================================================================================================================================+
   | parent_group_id       | String                | Specifies the associated security group ID in UUID format.                                                                                                                                                                                                                                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_protocol           | String                | Specifies the protocol type or the IP protocol number. The value can be **icmp**, **tcp**, **udp**, or the IP protocol number.                                                                                                                                                                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | from_port             | Integer               | Specifies the start port number. The value ranges from 1 to 65,535 and cannot be greater than **to_port**.                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       |                       | When **ip_protocol** is **icmp**, this parameter indicates the ICMP type field with a length from 0 to 255 characters.                                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       |                       | .. note::                                                                                                                                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       |                       |    The ICMP message type is determined by the type field and code field in the packet. For details, see **Appendix** > **ICMP-Port Range Relationship Table** in *Virtual Private Cloud API Reference*. **port_range_min** indicates the ICMP type field, and **port_range_max** indicates the ICMP code field. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | to_port               | Integer               | Specifies the stop port number. The value ranges from 1 to 65,535 and cannot be less than **from_port**.                                                                                                                                                                                                        |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       |                       | When **ip_protocol** is **icmp**, this parameter indicates the ICMP code field with a length from 0 to 255 characters.                                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       |                       | .. note::                                                                                                                                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       |                       |    The ICMP message type is determined by the type field and code field in the packet. For details, see **Appendix** > **ICMP-Port Range Relationship Table** in *Virtual Private Cloud API Reference*. **port_range_min** indicates the ICMP type, and **port_range_max** indicates the ICMP code.             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_range              | Object                | Specifies the peer IP segment in CIDR format. For details, see `Table 5 <#enustopic0090187679enustopic0057973221table4101480163218>`__.                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       |                       | Specify either **ip_range** or **group**.                                                                                                                                                                                                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group                 | Object                | Specifies the name of the peer security group and the ID of the tenant in the peer security group. For details, see `Table 6 <#enustopic0090187679enustopic0057973221table9527961163416>`__.                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       |                       | Specify either **ip_range** or **group**.                                                                                                                                                                                                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | Specifies the security group rule ID in UUID format.                                                                                                                                                                                                                                                            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0090187679enustopic0057973221table4101480163218:

.. table:: **Table 5** **ip_range** objects

   ========= ====== =============================================
   Parameter Type   Description
   ========= ====== =============================================
   cidr      String Specifies the peer IP segment in CIDR format.
   ========= ====== =============================================



.. _ENUSTOPIC0090187679enustopic0057973221table9527961163416:

.. table:: **Table 6** **group** objects

   +-----------+--------+------------------------------------------------------------+
   | Parameter | Type   | Description                                                |
   +===========+========+============================================================+
   | tenant_id | String | Specifies the ID of the tenant of the peer security group. |
   +-----------+--------+------------------------------------------------------------+
   | name      | String | Specifies the name of the peer security group.             |
   +-----------+--------+------------------------------------------------------------+

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/bb1118612ba64af3a6ea63a1bdcaa5ae/os-security-groups
   GET https://{endpoint}/v2.1/bb1118612ba64af3a6ea63a1bdcaa5ae/os-security-groups

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

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


