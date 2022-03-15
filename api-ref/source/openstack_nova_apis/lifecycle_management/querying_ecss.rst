Querying ECSs
=============

Function
--------

This API is used to query ECSs.

URI
---

GET /v2.1/{project_id}/servers?changes-since={changes-since}&image={image}&flavor={flavor}&name={name}&status={status}&limit={limit}&marker={marker}&not-tags={not-tags}&reservation_id={reservation_id}&ip={ip}

GET /v2/{project_id}/servers?changes-since={changes-since}&image={image}&flavor={flavor}&name={name}&status={status}&limit={limit}&marker={marker}&not-tags={not-tags}&reservation_id={eservation_id}&ip={ip}

`Table 1 <#enustopic0020212688table5536817>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0020212688table5536817:

.. table:: **Table 1** Path parameters

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================



.. _ENUSTOPIC0020212688table34603472320:

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================================================================================================================================================================================+
   | changes-since   | No              | String          | Specifies the timestamp of the last ECS status update, which is used to filter out the ECSs with statuses updated later than the timestamp. The format must comply with ISO 8601 in the format of CCYY-MM-DDThh:mm:ss+/-hh:mm, for example, 2018-01-17T03:03:32Z.                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image           | No              | String          | Specifies the image ID.                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 | When image is used as a filter criterion, other filter criteria and paging criteria are not supported. If both the image and other filter criteria are specified, the image filter criterion is used. If the query criteria do not contain the image filter criterion, API functions are not restricted. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavor          | No              | String          | Specifies the ECS type ID, which is fuzzy matched.                                                                                                                                                                                                                                                       |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Specifies the ECS name, which is fuzzy matched.                                                                                                                                                                                                                                                          |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | Specifies the ECS status.                                                                                                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 | Options:                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 | **ACTIVE**, **BUILD**, **ERROR**, **HARD_REBOOT**, **MIGRATING**, **REBOOT**, **REBUILD**, **RESIZE**, **REVERT_RESIZE**, **SHUTOFF**, and **VERIFY_RESIZE**                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 | In microversion 2.37, the system will return an empty list for the **status** field out of the preceding options. In microversion 2.38 and later, the system will return error 400.                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 | For details, see `ECS Statuses <../../appendix/ecs_statuses.html>`__.                                                                                                                                                                                                                                    |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Specifies the upper limit on the number of returned results.                                                                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 | The default value on each page is 25, and the information of a maximum of 1000 ECSs is displayed on each page.                                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Specifies the ECS ID to which the marker points. The query will start from its next ID.                                                                                                                                                                                                                  |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags            | No              | String          | Queries ECSs with tags containing the specified value.                                                                                                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not-tags        | No              | String          | Queries ECSs with tags not containing the specified value. The value is the tag key.                                                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 | For details about key rules, see `Tag Types <../../openstack_nova_apis/tag_management/tag_types.html>`__.                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 | .. note::                                                                                                                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 |    Tag functions have been upgraded on the public cloud. If the tags added before the function upgrade are in the format of "Key.Value", query tags using "Key".                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 |    For example, an existing tag is **a.b**. After the tag function upgrade, query the tag using "not-tags=a".                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | reservation_id  | No              | String          | Specifies the ID returned when ECSs are created in a batch. This parameter is used to query ECSs created in a batch.                                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_key        | No              | String          | Sorts query results by ECS attribute. The default sorting order is the reverse order of **created_at**.                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 | Options: **created_at**, **availability_zone**, **display_name**, **host**, **instance_type_id**, **key_name**, **project_id**, **user_id**, **updated_at**, **uuid**, and **vm_state**                                                                                                                  |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip              | No              | String          | Indicates the filtering result for IPv4 addresses, which are fuzzy matched.                                                                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

`Table 3 <#enustopic0020212688table44736746>`__ describes the response parameters.



.. _ENUSTOPIC0020212688table44736746:

.. table:: **Table 3** Response parameters

   +---------------+------------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type             | Description                                                                                                                |
   +===============+==================+============================================================================================================================+
   | servers       | Array of objects | Specifies the ECSs to be queried. For details, see `Table 4 <#enustopic0020212688table11253402>`__.                        |
   +---------------+------------------+----------------------------------------------------------------------------------------------------------------------------+
   | servers_links | Array of objects | Specifies the link of the next page in pagination query. For details, see `Table 5 <#enustopic0020212688table64121649>`__. |
   +---------------+------------------+----------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212688table11253402:

.. table:: **Table 4** **servers** field description

   +-----------+------------------+-------------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                     |
   +===========+==================+=================================================================================================+
   | name      | String           | Specifies the ECS name.                                                                         |
   +-----------+------------------+-------------------------------------------------------------------------------------------------+
   | id        | String           | Specifies an ECS uniquely.                                                                      |
   +-----------+------------------+-------------------------------------------------------------------------------------------------+
   | links     | Array of objects | Specifies ECS shortcut links. For details, see `Table 5 <#enustopic0020212688table64121649>`__. |
   +-----------+------------------+-------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0020212688table64121649:

.. table:: **Table 5** **servers_links** and **links** field description

   ========= ====== ========================================
   Parameter Type   Description
   ========= ====== ========================================
   rel       String Specifies the shortcut link marker name.
   href      String Specifies the shortcut link.
   ========= ====== ========================================

Example Request
---------------

.. code-block::

   GET https://{endpoint}/v2/{project_id}/servers
   GET https://{endpoint}/v2.1/{project_id}/servers

Example Response
----------------

.. code-block::

   {
       "servers": [
           {
               "id": "616fb98f-46ca-475e-917e-2563e5a8cd19", 
               "links": [
                   {
                       "href": "http://openstack.example.com/v2/openstack/servers/616fb98f-46ca-475e-917e-2563e5a8cd19", 
                       "rel": "self"
                   }, 
                   {
                       "href": "http://openstack.example.com/openstack/servers/616fb98f-46ca-475e-917e-2563e5a8cd19", 
                       "rel": "bookmark"
                   }
               ], 
               "name": "new-server-test"
           }
       ]
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


