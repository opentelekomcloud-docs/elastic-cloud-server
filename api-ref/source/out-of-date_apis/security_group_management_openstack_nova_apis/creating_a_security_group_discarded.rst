:original_name: en-us_topic_0090187680.html

.. _en-us_topic_0090187680:

Creating a Security Group (Discarded)
=====================================

Function
--------

This API is used to create a security group.

This API has been discarded. Use the API described in section "Security Group (OpenStack Neutron APIs) > Creating a Security Group" in *Virtual Private Network API Reference*.

URI
---

POST /v2/{project_id}/os-security-groups

POST /v2.1/{project_id}/os-security-groups

:ref:`Table 1 <en-us_topic_0090187680__en-us_topic_0057972662_table55945983>` describes the parameters in the URI.

.. _en-us_topic_0090187680__en-us_topic_0057972662_table55945983:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

:ref:`Table 2 <en-us_topic_0090187680__en-us_topic_0057972662_table63943666>` describes the request parameters.

.. _en-us_topic_0090187680__en-us_topic_0057972662_table63943666:

.. table:: **Table 2** Request parameters

   +----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                                                                                            |
   +================+===========+========+========================================================================================================================================================================+
   | security_group | Yes       | Object | Specifies the security group, which is configured in the message body. For details, see :ref:`Table 3 <en-us_topic_0090187680__en-us_topic_0057972662_table21940722>`. |
   +----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0090187680__en-us_topic_0057972662_table21940722:

.. table:: **Table 3** Objects of request parameter **security_group**

   +-------------+-----------+--------+------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                        |
   +=============+===========+========+====================================================================================+
   | name        | No        | String | Specifies the security group name. It must contain 0 to 255 characters.            |
   +-------------+-----------+--------+------------------------------------------------------------------------------------+
   | description | No        | String | Specifies information about a security group. It must contain 0 to 255 characters. |
   +-------------+-----------+--------+------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 4 <en-us_topic_0090187680__en-us_topic_0057972662_table61502840>` describes the response parameters.

.. _en-us_topic_0090187680__en-us_topic_0057972662_table61502840:

.. table:: **Table 4** Response parameters

   +----------------+--------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type   | Description                                                                                                                   |
   +================+========+===============================================================================================================================+
   | security_group | Object | Specifies the security group. For details, see :ref:`Table 5 <en-us_topic_0090187680__en-us_topic_0057972662_table27870469>`. |
   +----------------+--------+-------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0090187680__en-us_topic_0057972662_table27870469:

.. table:: **Table 5** Objects of response parameter **security_group**

   +-------------+------------------+---------------------------------------------------------------+
   | Parameter   | Type             | Description                                                   |
   +=============+==================+===============================================================+
   | description | String           | Provides supplementary information about the security group.  |
   +-------------+------------------+---------------------------------------------------------------+
   | id          | String           | Specifies the security group ID in UUID format.               |
   +-------------+------------------+---------------------------------------------------------------+
   | name        | String           | Specifies the security group name.                            |
   +-------------+------------------+---------------------------------------------------------------+
   | rules       | Array of objects | Specifies the rules of the security group. The list is empty. |
   +-------------+------------------+---------------------------------------------------------------+
   | tenant_id   | String           | Specifies the tenant or project ID.                           |
   +-------------+------------------+---------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v2/bb1118612ba64af3a6ea63a1bdcaa5ae/os-security-groups
   POST https://{endpoint}/v2.1/bb1118612ba64af3a6ea63a1bdcaa5ae/os-security-groups

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
           "rules": [],
           "tenant_id": "bb1118612ba64af3a6ea63a1bdcaa5ae",
           "description": "desc-sg",
           "id": "81f1d23b-b1e2-42cd-bdee-359b4a065a42",
           "name": "test-sg"
       }
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.
