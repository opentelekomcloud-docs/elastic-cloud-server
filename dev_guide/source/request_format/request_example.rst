:original_name: en-us_topic_0134192984.html

.. _en-us_topic_0134192984:

Request Example
===============

#. .. _en-us_topic_0134192984__li1785204217617:

   Obtain a token.

   -  POST: https://*{endpoint}*/v3/auth/tokens

   -  Headers

      .. table:: **Table 1** Parameter description

         ============ ================
         Parameter    Value
         ============ ================
         Content-Type application/json
         ============ ================

   -  Body

      .. code-block::

         {
             "auth":{
                 "identity":{
                     "password":{
                         "user":{
                             "name":"testuser",
                             "domain":{
                                 "id":"2aa29cbca17a4822abd096610e378ffa"
                             },
                             "password":"Test@123"
                         }
                     },
                     "methods":[
                         "password"
                     ]
                 },
                 "scope":{
                     "project":{
                         "id":"fb770eb43f934b5a8bda955642b954b9"
                     }
                 }
             }
         }

   Obtain the token (**x-subject-token**) in **Headers**

   .. _en-us_topic_0134192984__fig71433122328:

   .. figure:: /_static/images/en-us_image_0173496405.png
      :alt: Click to enlarge
      :figclass: imgResize
   

      **Figure 1** Obtaining the token

#. Initiate a request and access the API for viewing details about an ECS.

   -  GET: https://*{endpoint}*/v2/fb770eb43f934b5a8bda955642b954b9/servers/detail

      -  URI format: GET /v2/{tenant_id}/servers/detail{?changes-since,image,flavor,name,status,limit,marker,not-tags,reservation_id,all_tenants}
      -  tenant_id: fb770eb43f934b5a8bda955642b954b9
      -  The fields, **changes-since,image,flavor,name,status,limit,marker,not-tags,reservation_id,all_tenants**, following the question mark (?) are optional for viewing an ECS.

   -  Headers

      +--------------+----------------------------------------------------------------+
      | Content-Type | application/json                                               |
      +--------------+----------------------------------------------------------------+
      | X-Auth-Token | Obtained in :ref:`1 <en-us_topic_0134192984__li1785204217617>` |
      +--------------+----------------------------------------------------------------+

   -  Response body: JSON data in UTF-8 code format

      .. code-block::

         {
           "servers": [
             {
               "tenant_id": "fb770eb43f934b5a8bda955642b954b9",
               "addresses": {
                 "196b63ba-4201-4b55-b5aa-62ab6085d884": [
                   {
                     "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:82:2b:a0",
                     "OS-EXT-IPS:type": "fixed",
                     "addr": "192.168.1.10",
                     "version": 4
                   },
                   {
                     "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:82:2b:a0",
                     "OS-EXT-IPS:type": "floating",
                     "addr": "192.168.213.134",
                     "version": 4
                   }
                 ]
               },
               "metadata": {},
               "OS-EXT-STS:task_state": null,
               "OS-DCF:diskConfig": "MANUAL",
               "OS-EXT-AZ:availability_zone": "eu-de-02",
               "links": [
                 {
                   "rel": "self",
                   "href": "https://xxx/v2/fb770eb43f934b5a8bda955642b954b9/servers/0e56e372-31d4-40b6-8c85-d82a3cfeb05c"
                 },
                 {
                   "rel": "bookmark",
                   "href": "https://xxx/fb770eb43f934b5a8bda955642b954b9/servers/0e56e372-31d4-40b6-8c85-d82a3cfeb05c"
                 }
               ],
               "OS-EXT-STS:power_state": 1,
               "id": "0e56e372-31d4-40b6-8c85-d82a3cfeb05c",
               "os-extended-volumes:volumes_attached": [
                 {
                   "id": "3e3fd674-a816-4602-8175-d9b2e20a65d5"
                 }
               ],
               "OS-EXT-SRV-ATTR:host": "pod01.eu-de-02",
               "image": {
                 "links": [
                   {
                     "rel": "bookmark",
                     "href": "https://xxx/fb770eb43f934b5a8bda955642b954b9/images/f3966520-45ce-45d3-b099-0123d1cd0043"
                   }
                 ],
                 "id": "f3966520-45ce-45d3-b099-0123d1cd0043"
               },
               "OS-SRV-USG:terminated_at": null,
               "accessIPv4": "",
               "accessIPv6": "",
               "created": "2018-05-10T09:13:29Z",
               "hostId": "1ee40e90e4774fc712d7e881d62ac5be9b05c9006504a69b9ab15aa0",
               "OS-EXT-SRV-ATTR:hypervisor_hostname": "nova005@7",
               "key_name": null,
               "flavor": {
                 "links": [
                   {
                     "rel": "bookmark",
                     "href": "https://xxx/fb770eb43f934b5a8bda955642b954b9/flavors/s2.small.1"
                   }
                 ],
                 "id": "s2.small.1"
               },
               "security_groups": [
                 {
                   "name": "default"
                 }
               ],
               "config_drive": "",
               "OS-EXT-STS:vm_state": "active",
               "OS-EXT-SRV-ATTR:instance_name": "instance-0009d9c4",
               "user_id": "f79791beca3c48159ac2553fff22e166",
               "name": "ecs-65a7",
               "progress": 0,
               "OS-SRV-USG:launched_at": "2018-05-10T12:11:10.803603",
               "updated": "2018-05-10T12:11:10Z",
               "status": "ACTIVE"
             },
             {
               "tenant_id": "fb770eb43f934b5a8bda955642b954b9",
               "addresses": {
                 "21bcff3b-3a71-4304-ab62-dad0b305890e": [
                   {
                     "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:e8:ab:b2",
                     "OS-EXT-IPS:type": "fixed",
                     "addr": "192.168.0.79",
                     "version": 4
                   },
                   {
                     "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:e8:ab:b2",
                     "OS-EXT-IPS:type": "floating",
                     "addr": "192.168.218.86",
                     "version": 4
                   }
                 ]
               },
               "metadata": {},
               "OS-EXT-STS:task_state": null,
               "OS-DCF:diskConfig": "MANUAL",
               "OS-EXT-AZ:availability_zone": "eu-de-02",
               "links": [
                 {
                   "rel": "self",
                   "href": "https://xxx/v2/fb770eb43f934b5a8bda955642b954b9/servers/3e6388ea-3467-436e-b11f-4dddbc3dd810"
                 },
                 {
                   "rel": "bookmark",
                   "href": "https://xxx/fb770eb43f934b5a8bda955642b954b9/servers/3e6388ea-3467-436e-b11f-4dddbc3dd810"
                 }
               ],
               "OS-EXT-STS:power_state": 1,
               "id": "3e6388ea-3467-436e-b11f-4dddbc3dd810",
               "os-extended-volumes:volumes_attached": [
                 {
                   "id": "1bb5c0f6-300d-45c9-81f0-ad41736716de"
                 }
               ],
               "OS-EXT-SRV-ATTR:host": "pod01.eu-de-02",
               "image": {
                 "links": [
                   {
                     "rel": "bookmark",
                     "href": "https://xxx/fb770eb43f934b5a8bda955642b954b9/images/f1d75ee7-83bc-4e43-81fb-b69b4625fdea"
                   }
                 ],
                 "id": "f1d75ee7-83bc-4e43-81fb-b69b4625fdea"
               },
               "OS-SRV-USG:terminated_at": null,
               "accessIPv4": "",
               "accessIPv6": "",
               "created": "2018-01-27T10:01:35Z",
               "hostId": "1ee40e90e4774fc712d7e881d62ac5be9b05c9006504a69b9ab15aa0",
               "OS-EXT-SRV-ATTR:hypervisor_hostname": "nova005@7",
               "key_name": null,
               "flavor": {
                 "links": [
                   {
                     "rel": "bookmark",
                     "href": "https://xxx/fb770eb43f934b5a8bda955642b954b9/flavors/s2.small.1"
                   }
                 ],
                 "id": "s2.small.1"
               },
               "security_groups": [
                 {
                   "name": "default"
                 }
               ],
               "config_drive": "",
               "OS-EXT-STS:vm_state": "active",
               "OS-EXT-SRV-ATTR:instance_name": "instance-00070c07",
               "user_id": "f79791beca3c48159ac2553fff22e166",
               "name": "ecs-terraformCLI",
               "progress": 0,
               "OS-SRV-USG:launched_at": "2018-05-10T10:19:04.709851",
               "updated": "2018-05-10T10:19:04Z",
               "status": "ACTIVE"
             }
           ]
         }
