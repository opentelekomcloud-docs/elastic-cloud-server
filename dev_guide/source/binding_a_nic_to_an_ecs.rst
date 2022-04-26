:original_name: en-us_topic_0134192997.html

.. _en-us_topic_0134192997:

Binding a NIC to an ECS
=======================

Scenarios
---------

If an ECS requires multiple NICs, you can call the API for creating NICs and bind them to the ECS.

.. note::

   You can bind a NIC by setting the **nics** parameter during ECS creation or bind a NIC after the ECS is created. This section describes how to bind a NIC to a created ECS.

Involved APIs
-------------

Binding a NIC involves the following APIs:

-  API for creating a network
-  API for creating a subnet
-  API for creating a port
-  API for binding a NIC to an ECS
-  API for viewing ECS NICs

Procedure
---------

#. Create a NIC.

   a. Create a network.

      -  API

         URI format: POST /v2.0/networks

         For details, see section "Creating a Network" in *Virtual Private Cloud API Reference*.

      -  Request example

         POST: https://*{endpoint}*/v2.0/networks

         Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

         Body

         .. code-block::

            {
              "network": {
                "shared": false, 
                "name": "demo-net", 
                "admin_state_up": true, 
                "tenant_id": "74610f3a5ad941998e91f076297ecf27"
              }
            }

      -  Response example

         .. code-block::

            {
              "network": {
                "id": "c4a3019d-1ac0-4cfb-a838-2342eb992e6b",
                "name": "demo-net",
                "status": "ACTIVE",
                "shared": false,
                "subnets": [],
                "availability_zone_hints": [],
                "availability_zones": [
                  "eu-de-01",
                  "eu-de-02"
                ],
                "admin_state_up": true,
                "tenant_id": "74610f3a5ad941998e91f076297ecf27",
                "provider:network_type": "vxlan",
                "router:external": false
              }
            }

   b. Record the **network** ID in the response.
   c. Create a subnet.

      -  API

         URI format: POST /v2.0/subnets

         For details, see section "Creating a Subnet" in *Virtual Private Cloud API Reference*.

      -  Request example

         POST: https://{endpoint}/v2.0/subnets

         Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

         Body

         .. code-block::

            {
                "subnet": {
                    "name": "testsubnet",
                    "enable_dhcp": true,
                    "network_id": "c4a3019d-1ac0-4cfb-a838-2342eb992e6b",
                    "tenant_id": "74610f3a5ad941998e91f076297ecf27",
                    "dns_nameservers": [
                        "8.8.8.8",
                        "8.8.8.7"
                    ],
                    "allocation_pools": [
                        {
                            "start": "10.0.10.2",
                            "end": "10.0.10.254"
                        }
                    ],
                    "host_routes": [],
                    "ip_version": 4,
                    "gateway_ip": "10.0.10.1",
                    "cidr": "10.0.10.0/24"
                }
            }

      -  Response example

         .. code-block::

            {
              "subnet": {
                "name": "testsubnet",
                "cidr": "10.0.10.0/24",
                "id": "877b5567-e8c6-4a0d-aabf-0f13da225fe5",
                "enable_dhcp": true,
                "network_id": "c4a3019d-1ac0-4cfb-a838-2342eb992e6b",
                "tenant_id": "74610f3a5ad941998e91f076297ecf27",
                "dns_nameservers": [
                  "8.8.8.8",
                  "8.8.8.7"
                ],
                "allocation_pools": [
                  {
                    "start": "10.0.10.2",
                    "end": "10.0.10.254"
                  }
                ],
                "host_routes": [],
                "ip_version": 4,
                "gateway_ip": "10.0.10.1"
              }
            }

   d. Record the **subnet** ID in the response.
   e. Create a port.

      -  API

         URI format: POST /v2.0/ports

         For details, see section "Creating a Port" in *Virtual Private Cloud API Reference*.

      -  Request example

         POST: https://*{endpoint}*/v2.0/ports

         Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

         Body

         .. code-block::

            {
                "port": {
                    "admin_state_up": true, 

                    "fixed_ips": [
                        {
                            "subnet_id": "877b5567-e8c6-4a0d-aabf-0f13da225fe5"
                        }
                    ], 
                    "name": "test", 
                    "network_id": "c4a3019d-1ac0-4cfb-a838-2342eb992e6b",
                    "tenant_id": "74610f3a5ad941998e91f076297ecf27"
                }
            }

      -  Response example

         .. code-block::

            {
              "port": {
                "id": "7bf1c36f-e7f8-478a-be3d-674b486abbc4",
                "name": "test",
                "status": "DOWN",
                "admin_state_up": true,
                "fixed_ips": [
                  {
                    "subnet_id": "877b5567-e8c6-4a0d-aabf-0f13da225fe5",
                    "ip_address": "10.0.10.233"
                  }
                ],
                "mac_address": "fa:16:3e:db:91:f6",
                "network_id": "c4a3019d-1ac0-4cfb-a838-2342eb992e6b",
                "tenant_id": "74610f3a5ad941998e91f076297ecf27",
                "device_id": "",
                "device_owner": "",
                "security_groups": [
                  "93031677-2895-4b83-855a-637e309aa9e6"
                ],
                "extra_dhcp_opts": [],
                "allowed_address_pairs": [],
                "binding:vnic_type": "normal",
                "binding:vif_details": {},
                "binding:profile": {}
              }
            }

   f. Record the **port** ID in the response.

#. Bind the NIC to the ECS.

   -  API

      URI format: POST /v2/{tenant_id}/servers/{server_id}/os-interface

      For details, see section "Adding a NIC to an ECS" in *Elastic Cloud Server API Reference*.

   -  Request example

      POST: https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/servers/9f4d9281-95e7-4915-a126-1ee597101e2e/os-interface

      Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

      Body

      .. code-block::

         {
             "interfaceAttachment": {
                 "port_id": "7bf1c36f-e7f8-478a-be3d-674b486abbc4"
             }
         }

   -  Response example

      .. code-block::

         {
           "interfaceAttachment": {
             "port_state": "ACTIVE",
             "fixed_ips": [
               {
                 "subnet_id": "877b5567-e8c6-4a0d-aabf-0f13da225fe5",
                 "ip_address": "10.0.10.233"
               }
             ],
             "port_id": "7bf1c36f-e7f8-478a-be3d-674b486abbc4",
             "net_id": "c4a3019d-1ac0-4cfb-a838-2342eb992e6b",
             "mac_addr": "fa:16:3e:db:91:f6"
           }
         }

#. Verify the NIC binding.

   -  API

      URI format: GET /v2/{tenant_id}/servers/{server_id}/os-interface

      For details, see section "Querying ECS NICs" in *Elastic Cloud Server API Reference*.

   -  Request example

      GET: https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/servers/9f4d9281-95e7-4915-a126-1ee597101e2e/os-interface

      Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

   -  Response example

      .. code-block::

         {
           "interfaceAttachments": [
             {
               "port_state": "ACTIVE",
               "fixed_ips": [
                 {
                   "subnet_id": "46712fe4-25bd-4eae-874b-a528abfb76be",
                   "ip_address": "192.168.0.50"
                 }
               ],
               "port_id": "dd706739-b696-40be-a9f4-477ce478cb18",
               "net_id": "17251a8f-a671-4d7c-85d9-af5415962994",
               "mac_addr": "fa:16:3e:a5:e0:3c"
             },
         {
               "port_state": "ACTIVE",
               "fixed_ips": [
                 {
                   "subnet_id": "877b5567-e8c6-4a0d-aabf-0f13da225fe5",
                   "ip_address": "10.0.10.233"
                 }
               ],
               "port_id": "7bf1c36f-e7f8-478a-be3d-674b486abbc4",
               "net_id": "c4a3019d-1ac0-4cfb-a838-2342eb992e6b",
               "mac_addr": "fa:16:3e:db:91:f6"
             }
           ]
         }
