:original_name: en-us_topic_0090187681.html

.. _en-us_topic_0090187681:

Querying Details About a Security Group (Discarded)
===================================================

Function
--------

This API is used to query details about a security group.

This API can only query the inbound security group rules. To query the outbound security group rules, see "Querying a Security Group" in "Security Group (Native OpenStack API)" in the *Virtual Private Cloud API Reference*.

This API has been discarded. Use the API described in section "Security Group (OpenStack Neutron APIs) > Querying a Security Group" in *Virtual Private Network API Reference*.

URI
---

GET /v2/{project_id}/os-security-groups/{security_group_id}

GET /v2.1/{project_id}/os-security-groups/{security_group_id}

:ref:`Table 1 <en-us_topic_0090187681__en-us_topic_0057972663_table55945983>` describes the parameters in the URI.

.. _en-us_topic_0090187681__en-us_topic_0057972663_table55945983:

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

:ref:`Table 2 <en-us_topic_0090187681__en-us_topic_0057972663_table50358210>` describes the response parameters.

.. _en-us_topic_0090187681__en-us_topic_0057972663_table50358210:

.. table:: **Table 2** Response parameters

   +----------------+--------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type   | Description                                                                                                                   |
   +================+========+===============================================================================================================================+
   | security_group | Object | Specifies the security group. For details, see :ref:`Table 3 <en-us_topic_0090187681__en-us_topic_0057972663_table35285314>`. |
   +----------------+--------+-------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0090187681__en-us_topic_0057972663_table35285314:

.. table:: **Table 3** **security_group** objects

   +-------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type             | Description                                                                                                                     |
   +=============+==================+=================================================================================================================================+
   | description | String           | Specifies information about a security group. It must contain 0 to 255 characters.                                              |
   +-------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | id          | String           | Specifies the security group ID in UUID format.                                                                                 |
   +-------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | name        | String           | Specifies the security group name. It must contain 0 to 255 characters.                                                         |
   +-------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | rules       | Array of objects | Specifies security group rules. For details, see :ref:`Table 4 <en-us_topic_0090187681__en-us_topic_0057972663_table19372405>`. |
   +-------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id   | String           | Specifies the tenant or project ID.                                                                                             |
   +-------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0090187681__en-us_topic_0057972663_table19372405:

.. table:: **Table 4** **security_group_rule** objects

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================================================================================================================================================================================+
   | parent_group_id       | String                | Specifies the associated security group ID in UUID format.                                                                                                                                                                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_protocol           | String                | Specifies the protocol type or the IP protocol number. The value can be **icmp**, **tcp**, **udp**, or the IP protocol number.                                                                                                                                                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | from_port             | Integer               | Specifies the start port number. The value ranges from **1** to **65,535** and cannot be greater than **to_port**.                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                                                     |
   |                       |                       | When **ip_protocol** is **icmp**, this parameter indicates the ICMP type field with a length from 0 to 255 characters.                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                     |
   |                       |                       | .. note::                                                                                                                                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                                                                                                     |
   |                       |                       |    The ICMP message type is determined by the type field and code field in the packet. For details, see **Appendix** > **ICMP-Port Range Relationship Table** in *Virtual Private Cloud API Reference*. **port_range_min** indicates the ICMP type, and **port_range_max** indicates the ICMP code. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | to_port               | Integer               | Specifies the stop port number. The value ranges from 1 to 65,535 and cannot be less than **from_port**.                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                                                                     |
   |                       |                       | When **ip_protocol** is **icmp**, this parameter indicates the ICMP code field with a length from 0 to 255 characters.                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                     |
   |                       |                       | .. note::                                                                                                                                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                                                                                                     |
   |                       |                       |    The ICMP message type is determined by the type field and code field in the packet. For details, see **Appendix** > **ICMP-Port Range Relationship Table** in *Virtual Private Cloud API Reference*. **port_range_min** indicates the ICMP type, and **port_range_max** indicates the ICMP code. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_range              | Object                | Specifies the peer IP segment in CIDR format. For details, see :ref:`Table 5 <en-us_topic_0090187681__en-us_topic_0057972663_table4101480163218>`.                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                                                     |
   |                       |                       | Specify either **ip_range** or **group**.                                                                                                                                                                                                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group                 | Object                | Specifies the name of the peer security group and the ID of the tenant in the peer security group. For details, see :ref:`Table 6 <en-us_topic_0090187681__en-us_topic_0057972663_table9527961163416>`.                                                                                             |
   |                       |                       |                                                                                                                                                                                                                                                                                                     |
   |                       |                       | Specify either **ip_range** or **group**.                                                                                                                                                                                                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | Specifies the security group rule ID.                                                                                                                                                                                                                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0090187681__en-us_topic_0057972663_table4101480163218:

.. table:: **Table 5** **ip_range** objects

   ========= ====== =============================================
   Parameter Type   Description
   ========= ====== =============================================
   cidr      String Specifies the peer IP segment in CIDR format.
   ========= ====== =============================================

.. _en-us_topic_0090187681__en-us_topic_0057972663_table9527961163416:

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

.. code-block:: text

   GET https://{endpoint}/v2/bb1118612ba64af3a6ea63a1bdcaa5ae/os-security-groups/81f1d23b-b1e2-42cd-bdee-359b4a065a42
   GET https://{endpoint}/v2.1/bb1118612ba64af3a6ea63a1bdcaa5ae/os-security-groups/81f1d23b-b1e2-42cd-bdee-359b4a065a42

Example Response
----------------

.. code-block::

   {
       "security_group": {
           "rules": [],
           "tenant_id": "bb1118612ba64af3a6ea63a1bdcaa5ae",
           "id": "81f1d23b-b1e2-42cd-bdee-359b4a065a42",
           "name": "test-sg",
           "description": "desc-sg"
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
