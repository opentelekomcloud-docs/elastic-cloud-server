Updating a Security Group (Discarded)
=====================================

Function
--------

This API is used to update a security group.

This API has been discarded. Use the API described in section "Security Group (OpenStack Neutron APIs) > Updating a Security Group" in *Virtual Private Network API Reference*.

URI
---

PUT /v2/{project_id}/os-security-groups/{security_group_id}

PUT /v2.1/{project_id}/os-security-groups/{security_group_id}

`Table 1 <#enustopic0065817700enustopic0057972664table55945983>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817700enustopic0057972664table55945983:

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

`Table 2 <#enustopic0065817700enustopic0057972664table52078514>`__ describes the request parameters.



.. _ENUSTOPIC0065817700enustopic0057972664table52078514:

.. table:: **Table 2** Request parameters

   +----------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                                                            |
   +================+===========+========+========================================================================================================================================+
   | security_group | Yes       | Object | Specifies the security group in the message body. For details, see `Table 3 <#enustopic0065817700enustopic0057972664table11041789>`__. |
   +----------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817700enustopic0057972664table11041789:

.. table:: **Table 3** Objects of request parameter **security_group**

   +-----------------+-----------------+-----------------+-----------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                   |
   +=================+=================+=================+===============================================+
   | name            | Yes             | String          | Specifies the security group name.            |
   |                 |                 |                 |                                               |
   |                 |                 |                 | The value cannot exceed 255 characters.       |
   +-----------------+-----------------+-----------------+-----------------------------------------------+
   | description     | Yes             | String          | Specifies information about a security group. |
   |                 |                 |                 |                                               |
   |                 |                 |                 | The value cannot exceed 255 characters.       |
   +-----------------+-----------------+-----------------+-----------------------------------------------+

Response
--------

`Table 4 <#enustopic0065817700enustopic0057972664table44133910>`__ describes the response parameters.



.. _ENUSTOPIC0065817700enustopic0057972664table44133910:

.. table:: **Table 4** Response parameters

   +----------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                                       |
   +================+===========+========+===================================================================================================================+
   | security_group | Yes       | Object | Specifies the security group. For details, see `Table 5 <#enustopic0065817700enustopic0057972664table5938035>`__. |
   +----------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817700enustopic0057972664table5938035:

.. table:: **Table 5** Objects of response parameter **security_group**

   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                  |
   +=================+=================+==================+==============================================================================================================================+
   | description     | Yes             | String           | Specifies information about a security group.                                                                                |
   |                 |                 |                  |                                                                                                                              |
   |                 |                 |                  | The value cannot exceed 255 characters.                                                                                      |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------+
   | id              | Yes             | String           | Specifies the security group ID in UUID format.                                                                              |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------+
   | name            | Yes             | String           | Specifies the security group name.                                                                                           |
   |                 |                 |                  |                                                                                                                              |
   |                 |                 |                  | The value cannot exceed 255 characters.                                                                                      |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------+
   | rules           | Yes             | Array of objects | Specifies the security group rule list. For details, see `Table 6 <#enustopic0065817700enustopic0057972664table64215808>`__. |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id       | Yes             | String           | Specifies the tenant or project ID.                                                                                          |
   |                 |                 |                  |                                                                                                                              |
   |                 |                 |                  | The value cannot exceed 255 characters.                                                                                      |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817700enustopic0057972664table64215808:

.. table:: **Table 6** **security_group_rule** objects

   +-----------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type    | Description                                                                                                                                                                                                                                                                     |
   +=================+===========+=========+=================================================================================================================================================================================================================================================================================+
   | parent_group_id | Yes       | String  | Specifies the associated security group ID in UUID format.                                                                                                                                                                                                                      |
   +-----------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_protocol     | Yes       | String  | Specifies the protocol type or the IP protocol number. The value can be **icmp**, **tcp**, **udp**, or the IP protocol number.                                                                                                                                                  |
   +-----------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | from_port       | Yes       | Integer | Specifies the start port. The value ranges from 1 to 65,535 and cannot be greater than **to_port**. When **ip_protocol** is **icmp**, this parameter specifies a port type with a length from 0 to 255 characters.                                                              |
   +-----------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | to_port         | Yes       | Integer | Specifies the end port. The value ranges from 1 to 65,535 and cannot be less than **from_port**. When **ip_protocol** is **icmp**, it specifies the code. The value ranges from 0 to 255. If both **from_port** and **to_port** are **-1**, any ICMP packet can be transmitted. |
   +-----------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_range        | Yes       | Object  | Specifies the peer IP segment in CIDR format. For details, see `Table 7 <#enustopic0065817700enustopic0057972664table4101480163218>`__. The value of **ip_range** or **group** must be empty.                                                                                   |
   +-----------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group           | Yes       | Object  | Specifies the name of the peer security group and the ID of the tenant in the peer security group. For details, see `Table 8 <#enustopic0065817700enustopic0057972664table9527961163416>`__. The value of **ip_range** or **group** must be empty.                              |
   +-----------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id              | Yes       | String  | Specifies the security group rule ID in UUID format.                                                                                                                                                                                                                            |
   +-----------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817700enustopic0057972664table4101480163218:

.. table:: **Table 7** **ip_range** objects

   +-----------------+-----------------+-----------------+-----------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                   |
   +=================+=================+=================+===============================================+
   | cidr            | Yes             | String          | Specifies the peer IP segment in CIDR format. |
   |                 |                 |                 |                                               |
   |                 |                 |                 | The value cannot exceed 255 characters.       |
   +-----------------+-----------------+-----------------+-----------------------------------------------+



.. _ENUSTOPIC0065817700enustopic0057972664table9527961163416:

.. table:: **Table 8** **group** objects

   +-----------+-----------+--------+------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                |
   +===========+===========+========+============================================================+
   | tenant_id | Yes       | String | Specifies the ID of the tenant of the peer security group. |
   +-----------+-----------+--------+------------------------------------------------------------+
   | name      | Yes       | String | Specifies the name of the peer security group.             |
   +-----------+-----------+--------+------------------------------------------------------------+

Example Request
---------------

.. code-block::

   PUT https://{endpoint}/v2/bb1118612ba64af3a6ea63a1bdcaa5ae/os-security-groups/3d02312d-0764-49c9-8244-2368ddce0045
   PUT https://{endpoint}/v2.1/bb1118612ba64af3a6ea63a1bdcaa5ae/os-security-groups/3d02312d-0764-49c9-8244-2368ddce0045

.. code-block::

   {
       "security_group": {
           "name": "test",
           "description": "description"
       }
   }

Example Response
----------------

.. code-block::

   {
     "security_group": {
       "rules": [
         {
           "from_port": null,
           "group": {
             "tenant_id": "bb1118612ba64af3a6ea63a1bdcaa5ae",
             "name": "test"
           },
           "ip_protocol": null,
           "to_port": null,
           "parent_group_id": "3d02312d-0764-49c9-8244-2368ddce0045",
           "ip_range": {},
           "id": "00dec0b6-8e96-4906-aadf-46cfe54cf5ef"
         }
       ],
       "tenant_id": "bb1118612ba64af3a6ea63a1bdcaa5ae",
       "id": "3d02312d-0764-49c9-8244-2368ddce0045",
       "name": "test",
       "description": "description"
     }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


