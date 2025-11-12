:original_name: en-us_topic_0065817700.html

.. _en-us_topic_0065817700:

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

:ref:`Table 1 <en-us_topic_0065817700__en-us_topic_0057972664_table55945983>` describes the parameters in the URI.

.. _en-us_topic_0065817700__en-us_topic_0057972664_table55945983:

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

:ref:`Table 2 <en-us_topic_0065817700__en-us_topic_0057972664_table52078514>` describes the request parameters.

.. _en-us_topic_0065817700__en-us_topic_0057972664_table52078514:

.. table:: **Table 2** Request parameters

   +----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                                                                       |
   +================+===========+========+===================================================================================================================================================+
   | security_group | Yes       | Object | Specifies the security group in the message body. For details, see :ref:`Table 3 <en-us_topic_0065817700__en-us_topic_0057972664_table11041789>`. |
   +----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817700__en-us_topic_0057972664_table11041789:

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

:ref:`Table 4 <en-us_topic_0065817700__en-us_topic_0057972664_table44133910>` describes the response parameters.

.. _en-us_topic_0065817700__en-us_topic_0057972664_table44133910:

.. table:: **Table 4** Response parameters

   +----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                                                  |
   +================+===========+========+==============================================================================================================================+
   | security_group | Yes       | Object | Specifies the security group. For details, see :ref:`Table 5 <en-us_topic_0065817700__en-us_topic_0057972664_table5938035>`. |
   +----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817700__en-us_topic_0057972664_table5938035:

.. table:: **Table 5** Objects of response parameter **security_group**

   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                             |
   +=================+=================+==================+=========================================================================================================================================+
   | description     | Yes             | String           | Specifies information about a security group.                                                                                           |
   |                 |                 |                  |                                                                                                                                         |
   |                 |                 |                  | The value cannot exceed 255 characters.                                                                                                 |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | id              | Yes             | String           | Specifies the security group ID in UUID format.                                                                                         |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | name            | Yes             | String           | Specifies the security group name.                                                                                                      |
   |                 |                 |                  |                                                                                                                                         |
   |                 |                 |                  | The value cannot exceed 255 characters.                                                                                                 |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | rules           | Yes             | Array of objects | Specifies the security group rule list. For details, see :ref:`Table 6 <en-us_topic_0065817700__en-us_topic_0057972664_table64215808>`. |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id       | Yes             | String           | Specifies the tenant or project ID.                                                                                                     |
   |                 |                 |                  |                                                                                                                                         |
   |                 |                 |                  | The value cannot exceed 255 characters.                                                                                                 |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817700__en-us_topic_0057972664_table64215808:

.. table:: **Table 6** **security_group_rule** objects

   +-----------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type    | Description                                                                                                                                                                                                                                                                    |
   +=================+===========+=========+================================================================================================================================================================================================================================================================================+
   | parent_group_id | Yes       | String  | Specifies the associated security group ID in UUID format.                                                                                                                                                                                                                     |
   +-----------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_protocol     | Yes       | String  | Specifies the protocol type or the IP protocol number. The value can be **icmp**, **tcp**, **udp**, or the IP protocol number.                                                                                                                                                 |
   +-----------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | from_port       | Yes       | Integer | Specifies the start port. The value ranges from 1 to 65535 and cannot be greater than **to_port**. When **ip_protocol** is **icmp**, this parameter specifies a port type with a length from 0 to 255 characters.                                                              |
   +-----------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | to_port         | Yes       | Integer | Specifies the end port. The value ranges from 1 to 65535 and cannot be less than **from_port**. When **ip_protocol** is **icmp**, it specifies the code. The value ranges from 0 to 255. If both **from_port** and **to_port** are **-1**, any ICMP packet can be transmitted. |
   +-----------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_range        | Yes       | Object  | Specifies the peer IP segment in CIDR format. For details, see :ref:`Table 7 <en-us_topic_0065817700__en-us_topic_0057972664_table4101480163218>`. The value of **ip_range** or **group** must be empty.                                                                       |
   +-----------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group           | Yes       | Object  | Specifies the name of the peer security group and the ID of the tenant in the peer security group. For details, see :ref:`Table 8 <en-us_topic_0065817700__en-us_topic_0057972664_table9527961163416>`. The value of **ip_range** or **group** must be empty.                  |
   +-----------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id              | Yes       | String  | Specifies the security group rule ID in UUID format.                                                                                                                                                                                                                           |
   +-----------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817700__en-us_topic_0057972664_table4101480163218:

.. table:: **Table 7** **ip_range** objects

   +-----------------+-----------------+-----------------+-----------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                   |
   +=================+=================+=================+===============================================+
   | cidr            | Yes             | String          | Specifies the peer IP segment in CIDR format. |
   |                 |                 |                 |                                               |
   |                 |                 |                 | The value cannot exceed 255 characters.       |
   +-----------------+-----------------+-----------------+-----------------------------------------------+

.. _en-us_topic_0065817700__en-us_topic_0057972664_table9527961163416:

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

.. code-block:: text

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

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
