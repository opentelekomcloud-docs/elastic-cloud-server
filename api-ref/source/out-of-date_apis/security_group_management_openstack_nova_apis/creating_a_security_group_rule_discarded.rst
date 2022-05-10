:original_name: en-us_topic_0065817703.html

.. _en-us_topic_0065817703:

Creating a Security Group Rule (Discarded)
==========================================

Function
--------

This API is used to create a security group rule.

This API has been discarded. Use the API described in section "Security Group (OpenStack Neutron APIs) > Creating a Security Group Rule" in *Virtual Private Network API Reference*.

URI
---

POST /v2/{project_id}/os-security-group-rules

POST /v2.1/{project_id}/os-security-group-rules

:ref:`Table 1 <en-us_topic_0065817703__en-us_topic_0057972667_table32475667>` describes the parameters in the URI.

.. _en-us_topic_0065817703__en-us_topic_0057972667_table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0065817703__en-us_topic_0057972667_table58520811>` describes the request parameters.

.. _en-us_topic_0065817703__en-us_topic_0057972667_table58520811:

.. table:: **Table 2** Request parameters

   +---------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory | Type   | Description                                                                                                                                                                 |
   +=====================+===========+========+=============================================================================================================================================================================+
   | security_group_rule | Yes       | Object | Specifies the security group rule, which is configured in the message body. For details, see :ref:`Table 3 <en-us_topic_0065817703__en-us_topic_0057972667_table46685187>`. |
   +---------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817703__en-us_topic_0057972667_table46685187:

.. table:: **Table 3** Objects of request parameter **security_group_rule**

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================================================================================+
   | parent_group_id | Yes             | String          | Specifies the associated security group ID in UUID format.                                                                                                                                    |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_protocol     | Yes             | String          | Specifies the IP protocol, which can be **icmp**, **tcp**, or **udp**.                                                                                                                        |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | from_port       | Yes             | Integer         | Specifies the start port. The value ranges from 1 to 65,535 and is no greater than the value of **to_port**.                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                               |
   |                 |                 |                 | If the value of **ip_protocol** is **icmp**, this parameter specifies the ICMP type. The value ranges from **0** to **255**.                                                                  |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | to_port         | Yes             | Integer         | Specifies the end port. The value ranges from **1** to **65,535** and cannot be less than **from_port**.                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                               |
   |                 |                 |                 | If **ip_protocol** is **icmp**, this parameter specifies the ICMP code. The value ranges from 0 to 255. If both **from_port** and **to_port** are **-1**, any ICMP packet can be transmitted. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cidr            | No              | String          | Specifies the IP address range. The address is in CIDR format, such as 192.168.0.0/24.                                                                                                        |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_id        | No              | String          | Specifies the source security group ID. If both **group_id** and **cidr** are set, **group_id** is used.                                                                                      |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 4 <en-us_topic_0065817703__en-us_topic_0057972667_table37057034>` describes the response parameters.

.. _en-us_topic_0065817703__en-us_topic_0057972667_table37057034:

.. table:: **Table 4** Response parameters

   +---------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory | Type   | Description                                                                                                                                                                 |
   +=====================+===========+========+=============================================================================================================================================================================+
   | security_group_rule | Yes       | Object | Specifies the security group rule, which is configured in the message body. For details, see :ref:`Table 5 <en-us_topic_0065817703__en-us_topic_0057972667_table64243102>`. |
   +---------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0065817703__en-us_topic_0057972667_table64243102:

.. table:: **Table 5** Objects of response parameter **security_group_rule**

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================+
   | parent_group_id | Yes             | String          | Specifies the associated security group ID in UUID format.                                                                                           |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_protocol     | Yes             | String          | Specifies the IP protocol, which can be **icmp**, **tcp**, or **udp**.                                                                               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | from_port       | Yes             | Integer         | Specifies the start port number. The value ranges from 1 to 65,535 and cannot be greater than **to_port**.                                           |
   |                 |                 |                 |                                                                                                                                                      |
   |                 |                 |                 | When the protocol type is set to ICMP, **from_port** is the ICMP type and ranges from 0 to 255.                                                      |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | to_port         | Yes             | Integer         | Specifies the end port number. The value ranges from **1** to **65,535**.                                                                            |
   |                 |                 |                 |                                                                                                                                                      |
   |                 |                 |                 | -  When the protocol type is set to ICMP, **to_port** is the ICMP code and ranges from **0** to **255**.                                             |
   |                 |                 |                 | -  If both **from_port** and **to_port** are **-1**, it indicates that any ICMP packet can be transmitted.                                           |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_range        | Yes             | Object          | Specifies the IP address range, including the CIDR information, such as **"ip_range": {"cidr": "0.0.0.0/0"}**. For details, see the ip_range object. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group           | Yes             | Object          | Nothing is returned.                                                                                                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id              | Yes             | String          | Specifies the security group rule ID in UUID format.                                                                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 6** **ip_range** objects

   +-----------+-----------+--------+----------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                            |
   +===========+===========+========+========================================================================================+
   | cidr      | Yes       | String | Specifies the IP address range. The address is in CIDR format, such as 192.168.0.0/24. |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2/{project_id}/os-security-group-rules
   POST https://{endpoint}/v2.1/{project_id}/os-security-group-rules

.. code-block::

   {
       "security_group_rule": {
           "from_port": "443",
           "ip_protocol": "tcp",
           "to_port": "443",
           "cidr": "0.0.0.0/0",
           "parent_group_id": "48700ff3-30b8-4e63-845f-a79c9633e9fb"
       }
   }

Example Response
----------------

.. code-block::

   {
       "security_group_rule": {
           "id": "F4966B29-D21D-B211-B6B4-0018E1C5D866",
           "ip_range": {
               "cidr": "0.0.0.0/0"
           },
           "parent_group_id": "48700ff3-30b8-4e63-845f-a79c9633e9fb",
           "to_port": 443,
           "ip_protocol": "tcp",
           "group": {

           },
           "from_port": 443
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
