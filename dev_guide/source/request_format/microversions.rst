Microversions
=============

v2.1 APIs support microversions for small/medium API changes or document changes.

Users can use a microversion to obtain the latest API microversion supported by a cloud service. A cloud service that has been upgraded to the latest microversion is compatible with the original microversions. Users can also use a microversion to obtain new cloud service properties.

The version API returns the minimum and maximum microversions. The client uses the two values to specify the microversion range supported by an API.

Microversion Response Example
-----------------------------

If the values of **version** and **min_version** are null, the endpoint does not support microversions.

-  **version**: indicates the maximum microversion.
-  **min_version**: indicates the minimum microversion.

A microversion on the client must be within the range specified by **version** and **min_version** to access the endpoint. The client uses the following HTTP header to specify a microversion:

X-OpenStack-Nova-API-Version: 2.4

Since microversion 2.27, the client can also use the following header to specify a microversion:

Openstack-API-Version: compute 2.27

In the following response example, the maximum microversion is 2.14 and the minimum one is 2.1:

.. code-block::

   {
     "versions": [
         {
             "id": "v2.0",
             "links": [
                 {
                     "href": "http://openstack.example.com/v2/",
                     "rel": "self"
                 }
             ],
             "status": "SUPPORTED",
             "version": "",
             "min_version": "",
             "updated": "2011-01-21T11:33:21Z"
         },
         {
             "id": "v2.1",
             "links": [
                 {
                     "href": "http://openstack.example.com/v2.1/",
                     "rel": "self"
                 }
             ],
             "status": "CURRENT",
             "version": "2.14",
             "min_version": "2.1",
             "updated": "2013-07-23T11:33:21Z"
         }
     ]
   }

Microversion Request Example
----------------------------

For example, you are required to use the API for details about an ECS to view the **OS-EXT-SRV-ATTR:hostname** field.

-  **Using a v2 API without a microversion**

   -  GET: https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/servers/detail

      Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

   -  Headers 

.. _ENUSTOPIC0134193006table19387710:

      ============ ================
      Content-Type application/json
      X-Auth-Token ${token}
      ============ ================

   -  Response body

      .. code-block::

         {
           "servers": [
             {
               "tenant_id": "74610f3a5ad941998e91f076297ecf27",
               "addresses": {
                 "05d4fb93-84e5-4964-853b-32992ffef627": [
                   {
                     "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:20:17:95",
                     "OS-EXT-IPS:type": "fixed",
                     "addr": "192.168.0.228",
                     "version": 4
                   },
                   {
                     "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:20:17:95",
                     "OS-EXT-IPS:type": "floating",
                     "addr": "192.168.51.61",
                     "version": 4
                   }
                 ]
               },
               "metadata": {},
               "OS-EXT-STS:task_state": null,
               "OS-DCF:diskConfig": "MANUAL",
               "OS-EXT-AZ:availability_zone": "eu-de-01",
               "links": [
                 {
                   "rel": "self",
                   "href": "https://None/v2.1/74610f3a5ad941998e91f076297ecf27/servers/89c312bb-285a-4026-a237-d441908c2f9e"
                 },
                 {
                   "rel": "bookmark",
                   "href": "https://None/74610f3a5ad941998e91f076297ecf27/servers/89c312bb-285a-4026-a237-d441908c2f9e"
                 }
               ],
               "OS-EXT-STS:power_state": 1,
               "id": "89c312bb-285a-4026-a237-d441908c2f9e",
               "os-extended-volumes:volumes_attached": [
                 {
                   "id": "c70c4b8e-33bd-4d1f-ab16-14a5a38cdeaf"
                 }
               ],
               "OS-EXT-SRV-ATTR:host": "pod05.eude01",
               "image": {
                 "links": [
                   {
                     "rel": "bookmark",
                     "href": "https://None/74610f3a5ad941998e91f076297ecf27/images/1189efbf-d48b-46ad-a823-94b942e2a000"
                   }
                 ],
                 "id": "1189efbf-d48b-46ad-a823-94b942e2a000"
               },
               "OS-SRV-USG:terminated_at": null,
               "accessIPv4": "",
               "accessIPv6": "",
               "created": "2018-05-11T03:21:56Z",
               "hostId": "fc7a8ff86bac050f0d9454b1b078dcc97060e819acbf06f04c3e338f",
               "OS-EXT-SRV-ATTR:hypervisor_hostname": "nova012@7",
               "key_name": "id_rsa",
               "flavor": {
                 "links": [
                   {
                     "rel": "bookmark",
                     "href": "https://None/74610f3a5ad941998e91f076297ecf27/flavors/s3.small.1"
                   }
                 ],
                 "id": "s3.small.1"
               },
               "security_groups": [
                 {
                   "name": "default"
                 }
               ],
               "config_drive": "",
               "OS-EXT-STS:vm_state": "active",
               "OS-EXT-SRV-ATTR:instance_name": "instance-0016c624",
               "user_id": "f79791beca3c48159ac2553fff22e166",
               "name": "zt-test",
               "progress": 0,
               "OS-SRV-USG:launched_at": "2018-05-11T03:22:16.701600",
               "updated": "2018-05-11T03:22:51Z",
               "status": "ACTIVE"
             }
           ]
         }

   -  Conclusion: The response body does not contain the **OS-EXT-SRV-ATTR:hostname** field.

-  **Using a v2.1 API with a microversion**

   -  GET: https://*{endpoint}*/v2.1/74610f3a5ad941998e91f076297ecf27/servers/detail

      Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

   -  Headers 

.. _ENUSTOPIC0134193006table41684430:

      ============================ ================
      Content-Type                 application/json
      X-Auth-Token                 ${token}
      X-OpenStack-Nova-API-Version 2.26
      ============================ ================

   -  Response body

      .. code-block::

         {
           "servers": [
             {
               "tenant_id": "74610f3a5ad941998e91f076297ecf27",
               "addresses": {
                 "05d4fb93-84e5-4964-853b-32992ffef627": [
                   {
                     "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:20:17:95",
                     "OS-EXT-IPS:type": "fixed",
                     "addr": "192.168.0.228",
                     "version": 4
                   },
                   {
                     "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:20:17:95",
                     "OS-EXT-IPS:type": "floating",
                     "addr": "192.168.51.61",
                     "version": 4
                   }
                 ]
               },
               "metadata": {},
               "OS-EXT-STS:task_state": null,
               "description": "zt-test",
               "OS-EXT-SRV-ATTR:hostname": "zt-test",
               "OS-DCF:diskConfig": "MANUAL",
               "OS-EXT-AZ:availability_zone": "eu-de-01",
               "links": [
                 {
                   "rel": "self",
                   "href": "https://None/v2.1/74610f3a5ad941998e91f076297ecf27/servers/89c312bb-285a-4026-a237-d441908c2f9e"
                 },
                 {
                   "rel": "bookmark",
                   "href": "https://None/74610f3a5ad941998e91f076297ecf27/servers/89c312bb-285a-4026-a237-d441908c2f9e"
                 }
               ],
               "OS-EXT-STS:power_state": 1,
               "id": "89c312bb-285a-4026-a237-d441908c2f9e",
               "os-extended-volumes:volumes_attached": [
                 {
                   "delete_on_termination": true,
                   "id": "c70c4b8e-33bd-4d1f-ab16-14a5a38cdeaf"
                 }
               ],
               "locked": false,
               "OS-EXT-SRV-ATTR:kernel_id": "",
               "OS-EXT-SRV-ATTR:host": "pod05.eude01",
               "OS-EXT-SRV-ATTR:ramdisk_id": "",
               "image": {
                 "links": [
                   {
                     "rel": "bookmark",
                     "href": "https://None/74610f3a5ad941998e91f076297ecf27/images/1189efbf-d48b-46ad-a823-94b942e2a000"
                   }
                 ],
                 "id": "1189efbf-d48b-46ad-a823-94b942e2a000"
               },
               "accessIPv4": "",
               "OS-SRV-USG:terminated_at": null,
               "accessIPv6": "",
               "OS-EXT-SRV-ATTR:launch_index": 0,
               "created": "2018-05-11T03:21:56Z",
               "OS-EXT-SRV-ATTR:user_data": null,
               "hostId": "fc7a8ff86bac050f0d9454b1b078dcc97060e819acbf06f04c3e338f",
               "OS-EXT-SRV-ATTR:reservation_id": "r-pbqmaxer",
               "OS-EXT-SRV-ATTR:root_device_name": "/dev/vda",
               "host_status": "UP",
               "OS-EXT-SRV-ATTR:hypervisor_hostname": "nova012@7",
               "tags": [],
               "key_name": "id_rsa",
               "flavor": {
                 "links": [
                   {
                     "rel": "bookmark",
                     "href": "https://None/74610f3a5ad941998e91f076297ecf27/flavors/s3.small.1"
                   }
                 ],
                 "id": "s3.small.1"
               },
               "security_groups": [
                 {
                   "name": "default"
                 }
               ],
               "config_drive": "",
               "OS-EXT-STS:vm_state": "active",
               "OS-EXT-SRV-ATTR:instance_name": "instance-0016c624",
               "user_id": "f79791beca3c48159ac2553fff22e166",
               "name": "zt-test",
               "progress": 0,
               "OS-SRV-USG:launched_at": "2018-05-11T03:22:16.701600",
               "updated": "2018-05-11T03:22:51Z",
               "status": "ACTIVE"
             }
           ]
         }

   -  Conclusion: The response body contains the **OS-EXT-SRV-ATTR:hostname** field.


