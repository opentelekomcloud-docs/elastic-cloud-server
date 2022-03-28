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

`Table 1 <#enustopic0065817703enustopic0057972667table32475667>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0065817703enustopic0057972667table32475667:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0065817703enustopic0057972667table58520811>`__ describes the request parameters.



.. _ENUSTOPIC0065817703enustopic0057972667table58520811:

.. table:: **Table 2** Request parameters

   +---------------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory | Type   | Description                                                                                                                                                      |
   +=====================+===========+========+==================================================================================================================================================================+
   | security_group_rule | Yes       | Object | Specifies the security group rule, which is configured in the message body. For details, see `Table 3 <#enustopic0065817703enustopic0057972667table46685187>`__. |
   +---------------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817703enustopic0057972667table46685187:

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

`Table 4 <#enustopic0065817703enustopic0057972667table37057034>`__ describes the response parameters.



.. _ENUSTOPIC0065817703enustopic0057972667table37057034:

.. table:: **Table 4** Response parameters

   +---------------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory | Type   | Description                                                                                                                                                      |
   +=====================+===========+========+==================================================================================================================================================================+
   | security_group_rule | Yes       | Object | Specifies the security group rule, which is configured in the message body. For details, see `Table 5 <#enustopic0065817703enustopic0057972667table64243102>`__. |
   +---------------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0065817703enustopic0057972667table64243102:

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



.. _ENUSTOPIC0065817703enustopic0057972667table35443891:

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

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


