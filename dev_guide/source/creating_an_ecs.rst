Creating an ECS
===============

Scenarios
---------

An ECS with EVS disks is required.

An ECS can be created using a disk or image. This section uses an image as an example to describe how to create an ECS.

Involved APIs
-------------

Creating an ECS involves viewing flavors and AZs as well as creating EVS disks. The following APIs are required:

-  API for viewing details about ECS flavors
-  API for viewing details about images
-  API for viewing networks
-  API for creating and importing an SSH key pair
-  API for creating an ECS
-  API for viewing details about an ECS

Procedure
---------

#. Determine the ECS flavor.

   a. View ECS flavors.

      -  API

         URI format: GET /v2/{tenant_id}/flavors/detail{?minDisk,minRam,is_public,sort_key,sort_dir}

         The fields following the question mark (?) are optional for viewing flavors. For details, see section `Querying Details About ECS Flavors <https://docs.otc.t-systems.com/en-us/api/ecs/en-us_topic_0020212658.html>`__.

      -  Request example

         GET: https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/flavors/detail

         Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

      -  Response example

         .. code-block::

            {
              "flavors": [
                {
                  "name": "c1.2xlarge",
                  "links": [
                    {
                      "href": "https://xxx/v2/74610f3a5ad941998e91f076297ecf27/flavors/c1.2xlarge",
                      "rel": "self"
                    },
                    {
                      "href": "https://xxx/74610f3a5ad941998e91f076297ecf27/flavors/c1.2xlarge",
                      "rel": "bookmark"
                    }
                  ],
                  "ram": 8192,
                  "OS-FLV-DISABLED:disabled": false,
                  "vcpus": 8,
                  "swap": "",
                  "os-flavor-access:is_public": true,
                  "rxtx_factor": 1,
                  "OS-FLV-EXT-DATA:ephemeral": 0,
                  "disk": 0,
                  "id": "c1.2xlarge"
                }
            ]
            }

   b. Select a flavor based on site requirements and record the flavor ID.

#. Determine the image.

   a. View images.

      -  API

         URI format: GET /v2/{tenant_id}/images/detail

         For details, see section "Querying Image Details" in *Elastic Cloud Server API Reference*.

      -  Request example

         GET: https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/images/detail

         Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

      -  Response example

         .. code-block::

            {
              "images": [
                {
                  "OS-EXT-IMG-SIZE:size": 0,
                  "metadata": {
                    "__os_type": "Linux",
                    "hw_vif_multiqueue_enabled": "true",
                    "__imagetype": "gold",
                    "__quick_start": "true",
                    "virtual_env_type": "FusionCompute",
                    "__support_xen": "true",
                    "__support_kvm": "true",
                    "__image_source_type": "uds",
                    "__platform": "EulerOS",
                    "__os_version": "EulerOS 2.2 64bit",
                    "__os_bit": "64",
                    "__isregistered": "false"
                  },
                  "created": "2018-05-14T06:13:50Z",
                  "minRam": 0,
                  "name": "DBS-MySQL-Image_2.1.3.3",
                  "progress": 100,
                  "links": [
                    {
                      "rel": "self",
                      "href": "https://None/v2/74610f3a5ad941998e91f076297ecf27/images/11e8f727-d439-4ed1-b3b8-33f46c0379c4"
                    },
                    {
                      "rel": "bookmark",
                      "href": "https://None/74610f3a5ad941998e91f076297ecf27/images/11e8f727-d439-4ed1-b3b8-33f46c0379c4"
                    },
                    {
                      "rel": "alternate",
                      "href": "https://None/images/11e8f727-d439-4ed1-b3b8-33f46c0379c4",
                      "type": "application/vnd.openstack.image"
                    }
                  ],
                  "id": "11e8f727-d439-4ed1-b3b8-33f46c0379c4",
                  "updated": "2018-05-14T06:13:52Z",
                  "minDisk": 40,
                  "status": "ACTIVE"
                }
              ]
            }

   b. Select an image based on site requirements and record the image ID.

#. Determine the network configuration.

   a. View networks.

      -  API

         URI format: GET /v2/{tenant_id}/os-networks

         For details, see section "Querying Networks" in *Elastic Cloud Server API Reference*.

      -  Request example

         GET: https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/os-networks

         Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

      -  Response example

         .. code-block::

            {
              "networks": [
                {
                  "id": "07a9557d-4256-48ae-847c-415a9c8f7ff6",
                  "label": "b_tt3_td1b",
                  "broadcast": null,
                  "cidr": null,
                  "dns1": null,
                  "dns2": null,
                  "gateway": null,
                  "netmask": null,
                  "cidr_v6": null,
                  "gateway_v6": null,
                  "netmask_v6": null
                }
              ]
            }

   b. Select a network based on site requirements and record the network ID.

#. Set the login mode to key pair.

   a. Create a key pair.

      -  API

         URI format: POST /v2/{tenant_id}/os-keypairs

         For details, see section "Creating and Importing an SSH Key Pair" in *Elastic Cloud Server API Reference*.

      -  Request example

         POST: https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/os-keypairs

         Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

         Body

         .. code-block::

            {
                "keypair": {
                    "type": "ssh",
                    "name": "demo1",
                    "user_id": "fake"
                }
            }

      -  Response example

         .. code-block::

            {
              "keypair": {
                "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCrR5Gcwlh5ih7JOvzIUuQxS5qzWWPMYHeDXkDKSQ9W5pumOV05SiO3WCswnaQ5xMdOl31mNiHtwlwq9dJi7X6jJBB2shTD+00G5WuwkBbFU4CLvt1B44u0NUiaTJ35NAvW2/4XvpXm9OwiQ3B5ge6ZY7Esi38Unh+pkbhPkYxNBCK8yoOlojQhWs75abdxZBi811/8RwLcNiFiocA2RGxtRjBdpEScj+1TU+OcfZdQnr0AFbO11z7yxfIygwwzVTgUuJNbMbKHStQqRbklfMlHY4RBPQgb7RN/YaXKTQSXT84k+D9xlDNo7Wj4fwOJTOz/s/PvbIOqjRHt9D6Y4IKd Generated-by-Nova\n",
                "private_key": "-----BEGIN RSA PRIVATE KEY-----\nMIIEogIBAAKCAQEAq0eRnMJYeYoeyTr8yFLkMUuas1ljzGB3g15AykkPVuabpjld\nOUojt1grMJ2kOcTHTpd9ZjYh7cJcKvXSYu1+oyQQdrIUw/tNBuVrsJAWxVOAi77d\nQeOLtDVImkyd+TQL1tv+F76V5vTsIkNweYHumWOxLIt/FJ4fqZG4T5GMTQQivMqD\npaI0IVrO+Wm3cWQYvNdf/EcC3DYhYqHANkRsbUYwXaREnI/tU1PjnH2XUJ69ABWz\ntdc+8sXyMoMMM1U4FLiTWzGyh0rUKkW5JXzJR2OEQT0IG+0Tf2Glyk0El0/OJPg/\ncZQzaO1o+H8DiUzs/7Pz72yDqo0R7fQ+mOCCnQIDAQABAoIBAA6/c9dGmK2mae4z\nyQ5KrOFdvC1TNhej+sZx+CwyzEJUSvSuHcvQCXFBAz8FY92hhvPKcX66jINXZ+4/\nCmWAQ5YyhcRiow0Y91HvsS0bywoknX3q6kxBFodmyyCWFkgd5iMTADb1Lx0a27Y7\njlS4Dl5gyiGmxUN2Ng24wWEAjE8ZNuI0lrtr5IZKp+s5IAi/rb5AG/mL7EzicE8c\nmGP+QAa+nzwhAwNhFwVID230xen/ZcoL1d77hxeARNqJUxoR25gwJd6Ebg2y9pDW\nVu6cbbzgdGUCfQYlMEoAamAkCswOsDpVDBXwQnt2A537n6Wq2bgYIKusHr9thtxP\n/5ubQLUCgYEA4zYuBG2vtLHnvce26P8o2j1xcJS9K0ozkah9JFl3hqFN0sAqLlz7\n/Fm1jA4kzHJS3d0UqP3AMDxY3HkIqCn4Be7lqeAAe2AfqkOZpt9MDNv4VwKe9sPb\nViW1qjL3FxziLC/YWTRNSlpwRjqJJGhA+UQt8rOia1k/zXmrEs7bXLcCgYEAwPsu\nK3j5QoAiziYVMYf5iCzWwAM9Ljpf9gw23lefTdIzhhfFtJplVRSyxRGU0UZ84GMI\nTd5zmcIF/1KUfhqmeiQzz6NIPEYEReahjpQ/sOH/Gk5Rwr3QwYPrwAu5x+kk/SRi\nKPkqw7APTR0sMQBcUq+ZYwGYLGPMdd1zUdLfb0sCgYBkuz11iydtxb3G/obSD2WO\nM9VaIycmzRPFzNwGRH/gOR0mhTluKp0wyJjbSd34oeqpH/2r2ivddrOysxoqa8jg\n4IQDZyLvj7MaKjQxrieqP89+y9Or9TMFo1xB46x2G8EN8/xHuA9YGnZSPFtWv72m\nhRqV0hv82amWsA0vHnRUSwKBgDsKHXvrTMbNkNhkykMXCH5iyWiBFSyZa1ZJMlgf\nknsqfdzeVPwF6E55QKAN2uuTlwzG/3ljPxahR1hvmUJjQN9JSBiUKbtW6GPCRVbr\nf/jLi1Iu99COZdluVKeybqn8Z/aSNP24DR9FM8kxzZ1IMPaTBmhFypp6BclhcLBt\nxTG1AoGAfcrkVbV1SOy7fECUtMpUECcw0yU4GWj3sR2RbII63C500RVYQlUpUaRR\naANbASHTVR4myOKtGSxEUhAQHlxFDwsDL7W3gzAqTFbEDp1xAAUyT/nkOAhQjEm4\nORFdDETeXLQG1KMUj+8AdnhfYp3JTdft6rmPpZEBUFiCAUMAvb0=\n-----END RSA PRIVATE KEY-----\n",
                "user_id": "f79791beca3c48159ac2553fff22e166",
                "name": "demo1",
                "fingerprint": "57:a7:a2:ed:5f:aa:e7:54:62:2e:bb:e7:92:22:cb:40"
              }
            }

   b. Import the key pair.

      -  API

         URI format: POST /v2/{tenant_id}/os-keypairs

         For details, see section "Creating and Importing an SSH Key Pair" in *Elastic Cloud Server API Reference*.

      -  Request example

         POST: https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/os-keypairs

         Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

         Body

         .. code-block::

            {
                "keypair": {
                    "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDY8wMTdBYiJgi62o6eShoOlSKx3CZ3cE6PHisDblfK3Y0Bg7EHV7iV9c74pqsrIhK0xuGUuO1NxDQWbkwLTPN4F9Iy5CIYohLuMIpbln6LDtfRPpdhEh3lxL8MM61gyfpKzeKkwkEpSFj27Rgh6zCyJgBpkA2A0HTP737UlitahL4faCWDIS+Vj6mbcfkWiMhuMCzTZgSKAZ4PfoG4B5HJhR52C6A4XLiQFT9heh9gnIsIG+uTogTKUbcJKuN7M6AraJpul6eHhV9YI4433sDmuiBF/njvreVPWwAHlAkgT9I8q1T/cfEFiwzXpdGbkK5O8NC7K+qNbbdKihlahONt Generated-by-Nova\n",
                    "type": "ssh",
                    "name": "demo2",
                    "user_id": "fake"
                }
            }

      -  Response example

         .. code-block::

            {
              "keypair": {
                "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDY8wMTdBYiJgi62o6eShoOlSKx3CZ3cE6PHisDblfK3Y0Bg7EHV7iV9c74pqsrIhK0xuGUuO1NxDQWbkwLTPN4F9Iy5CIYohLuMIpbln6LDtfRPpdhEh3lxL8MM61gyfpKzeKkwkEpSFj27Rgh6zCyJgBpkA2A0HTP737UlitahL4faCWDIS+Vj6mbcfkWiMhuMCzTZgSKAZ4PfoG4B5HJhR52C6A4XLiQFT9heh9gnIsIG+uTogTKUbcJKuN7M6AraJpul6eHhV9YI4433sDmuiBF/njvreVPWwAHlAkgT9I8q1T/cfEFiwzXpdGbkK5O8NC7K+qNbbdKihlahONt Generated-by-Nova\n",
                "user_id": "f79791beca3c48159ac2553fff22e166",
                "name": "demo2",
                "fingerprint": "dd:44:45:49:d9:f6:4f:c0:24:2d:81:aa:c4:4b:83:c2"
              }
            }

   c. Record the name in the response body, for example, **demo2**.

#. Create an ECS authenticated using the key pair.

   -  API

      URI format: POST /v2/{tenant_id}/servers

      For details about API constraints and request parameters, see section "Creating an ECS" in *Elastic Cloud Server API Reference*.

      .. note::

         In this example, the ECS is created using a specified image. Therefore,

         -  In **block_device_mapping_v2**, set **source_type** to **image**, **uuid** to the image ID, **destination_type** to **volume**, and **boot_index** to **0**.
         -  The **volume_size** must be greater than or equal to the minimum value specified in the image metadata.

   -  Request example

      POST: https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/servers

      Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

      Body

      .. code-block::

         {
             "server": {
                 "flavorRef": "c1.large",
                 "name": "zttestvm1",
                 "block_device_mapping_v2": [{
                 "source_type": "image",
                 "destination_type": "volume",
                 "volume_type": "SATA",
                       "volume_size": "40",
                       "delete_on_termination": "true",
                 "uuid": "11e8f727-d439-4ed1-b3b8-33f46c0379c4",
                 "boot_index": "0"
                 }],
                 "networks": [{
                     "uuid": "fb68519f-a7c0-476e-98d4-2e4cf6de6def"
                 }],
                 "key_name": "demo2",
                 "availability_zone": "eu-de-01"
             }
         }

   -  Response example

      .. code-block::

         {
           "server": {
             "security_groups": [
               {
                 "name": "default"
               }
             ],
             "OS-DCF:diskConfig": "MANUAL",
             "links": [
               {
                 "rel": "self",
                 "href": "https://None/v2/74610f3a5ad941998e91f076297ecf27/servers/6d311127-bce1-48db-bf0f-cac9f8f7f077"
               },
               {
                 "rel": "bookmark",
                 "href": "https://None/74610f3a5ad941998e91f076297ecf27/servers/6d311127-bce1-48db-bf0f-cac9f8f7f077"
               }
             ],
             "id": "6d311127-bce1-48db-bf0f-cac9f8f7f077",
             "adminPass": "WcC4QoVZPXpV"
           }
         }

#. Verify the ECS creation.

   -  API

      URI format: GET /v2/{tenant_id}/servers/{server_id}

      For details, see section "Querying Details About an ECS" in *Elastic Cloud Server API Reference*.

   -  Request example

      GET: https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/servers/0c71c0da-8852-4c56-a1d1-3a9b9bcb6da6

      Where,

      **0c71c0da-8852-4c56-a1d1-3a9b9bcb6da6** is the UUID of the created ECS.

      Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

   -  Response example

      .. code-block::

         {
           "server": {
             "tenant_id": "74610f3a5ad941998e91f076297ecf27",
             "addresses": {
               "2a6f4aa6-d93e-45f5-a8cb-b030dbf8cd68": [
                 {
                   "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:88:01:1b",
                   "OS-EXT-IPS:type": "fixed",
                   "addr": "192.168.2.192",
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
                 "href": "https://None/v2/74610f3a5ad941998e91f076297ecf27/servers/0c71c0da-8852-4c56-a1d1-3a9b9bcb6da6"
               },
               {
                 "rel": "bookmark",
                 "href": "https://None/74610f3a5ad941998e91f076297ecf27/servers/0c71c0da-8852-4c56-a1d1-3a9b9bcb6da6"
               }
             ],
             "OS-EXT-STS:power_state": 1,
             "id": "0c71c0da-8852-4c56-a1d1-3a9b9bcb6da6",
             "os-extended-volumes:volumes_attached": [
               {
                 "id": "b551445a-e749-4d53-932a-638a455cb6c3"
               }
             ],
             "OS-EXT-SRV-ATTR:host": "pod1a.eude1",
             "image": {
               "links": [
                 {
                   "rel": "bookmark",
                   "href": "https://None/74610f3a5ad941998e91f076297ecf27/images/11e8f727-d439-4ed1-b3b8-33f46c0379c4"
                 }
               ],
               "id": "11e8f727-d439-4ed1-b3b8-33f46c0379c4"
             },
             "OS-SRV-USG:terminated_at": null,
             "accessIPv4": "",
             "accessIPv6": "",
             "created": "2018-05-25T01:47:11Z",
             "hostId": "b2792bef989888d2df1f51bff81de5ac58a4117f4e9ec3059c1a0410",
             "OS-EXT-SRV-ATTR:hypervisor_hostname": "nova001@36",
             "key_name": null,
             "flavor": {
               "links": [
                 {
                   "rel": "bookmark",
                   "href": "https://None/74610f3a5ad941998e91f076297ecf27/flavors/c1.large"
                 }
               ],
               "id": "c1.large"
             },
             "security_groups": [
               {
                 "name": "default"
               }
             ],
             "config_drive": "",
             "OS-EXT-STS:vm_state": "active",
             "OS-EXT-SRV-ATTR:instance_name": "instance-001883cd",
             "user_id": "f79791beca3c48159ac2553fff22e166",
             "name": "zttestvm1",
             "progress": 0,
             "OS-SRV-USG:launched_at": "2018-05-25T01:47:55.755922",
             "updated": "2018-05-25T01:47:55Z",
             "status": "ACTIVE"
           }
         }
