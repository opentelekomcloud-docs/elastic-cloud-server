:original_name: en-us_topic_0094148850.html

.. _en-us_topic_0094148850:

Querying Details About ECSs
===========================

Function
--------

This API is used to query ECSs according to search criteria and details about the ECSs.

The information can be queried includes ECS billing modes and ECS frozen statuses.

URI
---

GET /v1/{project_id}/cloudservers/detail?flavor={flavor}&name={name}&status={status}&limit={limit}&offset={offset}&not-tags={not-tags}&reservation_id={reservation_id}&&tags={tags}&ip={ip}

:ref:`Table 1 <en-us_topic_0094148850__table32475667>` describes the parameters in the URI.

.. _en-us_topic_0094148850__table32475667:

.. table:: **Table 1** Path parameters

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================================================+
   | offset          | No              | Integer         | Specifies a page number.                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | The value must be greater than or equal to **0** and the default value is **1**.                                                                             |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | If the value is **0**, the first page is displayed, which is the same as the value **1**.                                                                    |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavor          | No              | String          | Specifies the flavor ID. For details about the published flavors, see **ECS Types** in *Elastic Cloud Server User Guide*.                                    |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Specifies the ECS name, which is fuzzy matched.                                                                                                              |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | Specifies the ECS status.                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | Options:                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | **ACTIVE**, **BUILD**, **ERROR**, **HARD_REBOOT**, **MIGRATING**, **REBOOT**, **REBUILD**, **RESIZE**, **REVERT_RESIZE**, **SHUTOFF**, and **VERIFY_RESIZE** |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | For details, see :ref:`ECS Statuses <en-us_topic_0178420672>`.                                                                                               |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | .. note::                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 |    When an ECS is in an intermediate state, the statuses that can be obtained are as follows:                                                                |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 |    -  **ACTIVE**: **ACTIVE**, **REBOOT**, **HARD_REBOOT**, **REBUILD**, or **MIGRATING**                                                                     |
   |                 |                 |                 |    -  **SHUTOFF**: **SHUTOFF**, **RESIZE**, or **REBUILD**                                                                                                   |
   |                 |                 |                 |    -  **ERROR**: **ERROR** or **REBUILD**                                                                                                                    |
   |                 |                 |                 |    -  **VERIFY_RESIZE**: **VERIFY_RESIZE** or **REVERT_RESIZE**                                                                                              |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Specifies the maximum number of ECSs on one page.                                                                                                            |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | Each page contains 25 ECSs by default, and a maximum of 1000 ECSs are returned. For large volumes of data, you are advised to set the value to **100**.      |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags            | No              | String          | Obtains the ECSs with specified tags.                                                                                                                        |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not-tags        | No              | String          | Queries ECSs whose **tag** field does not contain the specified value.                                                                                       |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | For example, if the queried ECS list should not contain BMSs, set this parameter as follows: not-tags=__type_baremetal                                       |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | reservation_id  | No              | String          | Specifies the ID returned when ECSs are created in a batch by using OpenStack Nova API. This parameter is used to query ECSs created in a batch.             |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip              | No              | String          | Specifies the filtering result for IPv4 addresses, which are fuzzy matched.                                                                                  |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | These IP addresses are private IP addresses of the ECS.                                                                                                      |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 3 <en-us_topic_0094148850__en-us_topic_0057972909_table36183900>` describes the response parameters.

.. _en-us_topic_0094148850__en-us_topic_0057972909_table36183900:

.. table:: **Table 3** Response parameters

   +-----------+------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                                                   |
   +===========+==================+===============================================================================================================================+
   | servers   | Array of objects | Specifies details about ECSs. For details, see :ref:`Table 3 <en-us_topic_0094148849__en-us_topic_0057972887_table61673566>`. |
   +-----------+------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | count     | Integer          | Specifies the total number of ECSs.                                                                                           |
   +-----------+------------------+-------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/cloudservers/detail?offset=1&limit=10

Example Response
----------------

.. code-block::

   {
       "count": 4,
       "servers": [{
                   "fault": null,
           "id": "b37fd80e-ac67-4d02-b9f1-9891c9c0fabf",
           "name": "ecs-yuankai2",
           "addresses": {
               "164489f6-cbf7-45b4-b6d0-d407c48cf7fc": [{
                   "version": "4",
                   "addr": "192.168.0.206",
                   "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:95:88:3f",
                   "OS-EXT-IPS:port_id": "7b5d615c-186d-4646-9cb8-444addfe9b92",
                   "OS-EXT-IPS:type": "fixed"
               },
               {
                   "version": "4",
                   "addr": "192.168.0.8",
                   "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:1d:88:43",
                   "OS-EXT-IPS:port_id": "dda2027b-2f03-497b-8d42-620da2baacc3",
                   "OS-EXT-IPS:type": "fixed"
               }]
           },
           "flavor": {
               "disk": "0",
               "vcpus": "1",
               "ram": "1024",
               "id": "c1.medium",
               "name": "c1.medium"
           },
           "accessIPv4": "",
           "accessIPv6": "",
           "status": "SHUTOFF",
                   "image": {
                          "id": "1ce5800a-e487-4c1b-b264-3353a39e2b4b"
                    },
           "hostId": "f92345b97fd291f67a29ed735a82a8983f370175d2ba3d18d66893f4",
           "updated": "2018-08-14T07:26:49Z",
           "created": "2018-08-13T13:46:09Z",
           "metadata": {
               "metering.image_id": "af60e0d5-6952-4f3d-b0ed-31bb19d4a692",
               "metering.resourcespeccode": "c1.medium.linux",
               "image_name": "HEC_Public_Cloudinit_CentOS_7.4_64bit",
               "metering.product_id": "00301-253164-0--0",
               "os_bit": "64",
               "lockSourceId": "",
               "lockScene": "",
               "metering.order_id": "CS1808132145NRVRE",
               "lockCheckEndpoint": "",
               "metering.imagetype": "gold",
               "lockSource": "",
               "metering.resourcetype": "1",
               "vpc_id": "164489f6-cbf7-45b4-b6d0-d407c48cf7fc",
               "os_type": "Linux",
               "charging_mode": "1"
           },
           "tags": [],
           "description": "ecs-4cff",
           "locked": false,
           "config_drive": "",
           "tenant_id": "edcb94a885a84ed3a3fdf8ea4d2741da",
           "user_id": "bb7f23e27e7e46f3aaceb5f53a158bdc",
           "os-extended-volumes:volumes_attached": [{
               "device": "/dev/sda",
               "bootIndex": "0",
               "id": "2edc879f-022e-4bd6-b079-95a27564d449",
               "delete_on_termination": "false"
           }],
                   "OS-EXT-STS:task_state": null,
           "OS-EXT-STS:power_state": 4,
           "OS-EXT-STS:vm_state": "stopped",
           "OS-EXT-SRV-ATTR:host": "az1.dc1",
           "OS-EXT-SRV-ATTR:instance_name": "instance-00137941",
           "OS-EXT-SRV-ATTR:hypervisor_hostname": "nova001@248",
           "OS-DCF:diskConfig": "MANUAL",
           "OS-EXT-AZ:availability_zone":"az1-dc1", //AZ name
           "os:scheduler_hints": {

           },
           "OS-EXT-SRV-ATTR:root_device_name": "/dev/sda",
           "OS-EXT-SRV-ATTR:ramdisk_id": "",

           "OS-EXT-SRV-ATTR:user_data": "IyEvYmluL2Jhc2gKZWNobyAncm9vdDokNiRKQ2FzUWQkbm5wVmhJUFZlNVMwc3pXbnJGLnZVZ1FCWk4xTEo5Vy8wd09WTmFZaWpBRXdtRnhuQmZaTllVZXhBWktVWFVTeVhEeERuSUMzV2JjZEJyQUVBZkZvLy8nIHwgY2hwYXNzd2QgLWU7",
           "OS-SRV-USG:launched_at": "2018-08-13T13:46:46.000000",
           "OS-EXT-SRV-ATTR:kernel_id": "",
           "OS-EXT-SRV-ATTR:launch_index": 0,
           "host_status": "UP",
           "OS-EXT-SRV-ATTR:reservation_id": "r-a8mg9vwr",
           "OS-EXT-SRV-ATTR:hostname": "ecs-4cff",
           "sys_tags": [{
               "key": "_sys_enterprise_project_id",
               "value": "441d5677-b76a-4dd4-a97a-ef7fd633c095"
           }],
           "security_groups": [{
                           "id": "71846bf6-1cda-4515-8590-3707be295e76",
               "name": "Sys-FullAccess"
           },
           {
                           "id": "b1786350-da65-11e7-b312-0255ac101b03",
               "name": "default"
           }]
       },
       {
                   "fault": null,
           "id": "8380dcc9-0eac-4407-9f9e-df8c9eddeacd",
           "name": "ecs-f680",
           "addresses": {
               "164489f6-cbf7-45b4-b6d0-d407c48cf7fc": [{
                   "version": "4",
                   "addr": "192.168.0.218",
                   "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:bb:b3:fe",
                   "OS-EXT-IPS:port_id": "240c696f-68d8-4f3f-941d-fecf2b375132",
                   "OS-EXT-IPS:type": "fixed"
               }]
           },
           "flavor": {
               "disk": "0",
               "vcpus": "1",
               "ram": "1024",
               "id": "c1.medium",
               "name": "c1.medium"
           },
           "accessIPv4": "",
           "accessIPv6": "",
           "status": "SHUTOFF",
                   "image": {
                          "id": "1ce5800a-e487-4c1b-b264-3353a39e2b4b"
                    },
           "hostId": "f92345b97fd291f67a29ed735a82a8983f370175d2ba3d18d66893f4",
           "updated": "2018-08-14T03:01:00Z",
           "created": "2018-08-13T13:38:29Z",
           "metadata": {
               "metering.image_id": "af60e0d5-6952-4f3d-b0ed-31bb19d4a692",
               "metering.imagetype": "gold",
               "metering.resourcespeccode": "c1.medium.linux",
               "image_name": "HEC_Public_Cloudinit_CentOS_7.4_64bit",
               "metering.resourcetype": "1",
               "os_bit": "64",
               "vpc_id": "164489f6-cbf7-45b4-b6d0-d407c48cf7fc",
               "os_type": "Linux",
               "charging_mode": "0"
           },
           "tags": [],
           "description": "ecs-f680",
           "locked": false,
           "config_drive": "",
           "tenant_id": "edcb94a885a84ed3a3fdf8ea4d2741da",
           "user_id": "61ee747d36bf421fa25c51a3b9565046",
           "os-extended-volumes:volumes_attached": [{
               "device": "/dev/sda",
               "bootIndex": "0",
               "id": "3721b948-9c2f-4980-90ad-b2a16811f58c",
               "delete_on_termination": "false"
           }],
                   "OS-EXT-STS:task_state": null,
           "OS-EXT-STS:power_state": 4,
           "OS-EXT-STS:vm_state": "stopped",
           "OS-EXT-SRV-ATTR:host": "az1.dc1",
           "OS-EXT-SRV-ATTR:instance_name": "instance-00137937",
           "OS-EXT-SRV-ATTR:hypervisor_hostname": "nova001@248",
           "OS-DCF:diskConfig": "MANUAL",
           "OS-EXT-AZ:availability_zone":"az1-dc1", //AZ name
           "os:scheduler_hints": {
           },
           "OS-EXT-SRV-ATTR:root_device_name": "/dev/sda",
           "OS-EXT-SRV-ATTR:ramdisk_id": "",

           "OS-EXT-SRV-ATTR:user_data": "IyEvYmluL2Jhc2gKZWNobyAncm9vdDokNiR5aG9aeFIkVE00OWlwSGQ2OEFWcjlTMTFXNEZrZmFYTENVbEkvd0xVTmdSVjhOb0dCem5WOWFsU1lEN0ZNSHc0VmtwdU9GOERyLncudGUzVmRHLnVmY005elVZSDEnIHwgY2hwYXNzd2QgLWU7",
           "OS-SRV-USG:launched_at": "2018-08-13T13:38:53.000000",
           "OS-EXT-SRV-ATTR:kernel_id": "",
           "OS-EXT-SRV-ATTR:launch_index": 0,
           "host_status": "UP",
           "OS-EXT-SRV-ATTR:reservation_id": "r-7e2g78rq",
           "OS-EXT-SRV-ATTR:hostname": "ecs-f680",
           "sys_tags": [{
               "key": "_sys_enterprise_project_id",
               "value": "441d5677-b76a-4dd4-a97a-ef7fd633c095"
           }],
           "security_groups": [{
               "name": "test"
           }]
       },
       {
                   "fault": null,
           "id": "fb70fed9-5774-44a7-ad4a-af3ea2c2da61",
           "name": "ecs-3993",
           "addresses": {
               "00159d7d-b3c3-4108-8bc4-6658814e6422": [{
                   "version": "4",
                   "addr": "192.168.20.83",
                   "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:a9:8d:88",
                   "OS-EXT-IPS:port_id": "579ab762-bf89-435e-80ad-a8bdd25119c5",
                   "OS-EXT-IPS:type": "fixed"
               }]
           },
           "flavor": {
               "disk": "0",
               "vcpus": "1",
               "ram": "1024",
               "id": "c1.medium",
               "name": "c1.medium"
           },
           "accessIPv4": "",
           "accessIPv6": "",
           "status": "SHUTOFF",
                   "image": {
                          "id": "1ce5800a-e487-4c1b-b264-3353a39e2b4b"
                    },
           "hostId": "f92345b97fd291f67a29ed735a82a8983f370175d2ba3d18d66893f4",
           "updated": "2018-08-14T03:01:03Z",
           "created": "2018-08-13T13:38:02Z",
           "metadata": {
               "metering.image_id": "af60e0d5-6952-4f3d-b0ed-31bb19d4a692",
               "metering.imagetype": "gold",
               "metering.resourcespeccode": "c1.medium.linux",
               "image_name": "HEC_Public_Cloudinit_CentOS_7.4_64bit",
               "metering.resourcetype": "1",
               "os_bit": "64",
               "vpc_id": "00159d7d-b3c3-4108-8bc4-6658814e6422",
               "os_type": "Linux",
               "charging_mode": "0"
           },
           "tags": [],
           "description": "ecs-3993",
           "locked": false,
           "config_drive": "",
           "tenant_id": "edcb94a885a84ed3a3fdf8ea4d2741da",
           "user_id": "eb4698fe015848e9a3e86cc9956e54fa",
           "key_name": "KeyPair-3b38",
           "os-extended-volumes:volumes_attached": [{
               "device": "/dev/sda",
               "bootIndex": "0",
               "id": "85bfbc4f-7733-419a-b171-c00585abf926",
               "delete_on_termination": "false"
           }],
                   "OS-EXT-STS:task_state": null,
           "OS-EXT-STS:power_state": 4,
           "OS-EXT-STS:vm_state": "stopped",
           "OS-EXT-SRV-ATTR:host": "az1.dc1",
           "OS-EXT-SRV-ATTR:instance_name": "instance-00137936",
           "OS-EXT-SRV-ATTR:hypervisor_hostname": "nova001@248",
           "OS-DCF:diskConfig": "MANUAL",
           "OS-EXT-AZ:availability_zone":"az1-dc1", //AZ name
           "os:scheduler_hints": {
           },
           "OS-EXT-SRV-ATTR:root_device_name": "/dev/sda",
           "OS-EXT-SRV-ATTR:ramdisk_id": "",

           "OS-SRV-USG:launched_at": "2018-08-13T13:38:24.000000",
           "OS-EXT-SRV-ATTR:kernel_id": "",
           "OS-EXT-SRV-ATTR:launch_index": 0,
           "host_status": "UP",
           "OS-EXT-SRV-ATTR:reservation_id": "r-uzsewxii",
           "OS-EXT-SRV-ATTR:hostname": "ecs-3993",
           "sys_tags": [{
               "key": "_sys_enterprise_project_id",
               "value": "441d5677-b76a-4dd4-a97a-ef7fd633c095"
           }],
           "security_groups": [{
               "name": "test"
           },
           {
               "name": "default"
           }]
       },
       {
                   "fault": null,
           "id": "e3d3f219-b445-4a7a-8f00-e31412481f8c",
           "name": "ecs-1f30",
           "addresses": {
               "00159d7d-b3c3-4108-8bc4-6658814e6422": [{
                   "version": "4",
                   "addr": "192.168.20.197",
                   "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:41:5a:32",
                   "OS-EXT-IPS:port_id": "cfa2e055-54fb-427a-bde4-128bda47ae5c",
                   "OS-EXT-IPS:type": "fixed"
               }]
           },
           "flavor": {
               "disk": "0",
               "vcpus": "1",
               "ram": "1024",
               "id": "c1.medium",
               "name": "c1.medium"
           },
           "accessIPv4": "",
           "accessIPv6": "",
           "status": "ACTIVE",
                   "image": {
                          "id": "1ce5800a-e487-4c1b-b264-3353a39e2b4b"
                    },
           "progress": 0,
           "hostId": "f92345b97fd291f67a29ed735a82a8983f370175d2ba3d18d66893f4",
           "updated": "2018-08-15T08:16:01Z",
           "created": "2018-08-13T11:57:29Z",
           "metadata": {
               "sadfasfasf": "sdffffd",
               "metering.order_id": "CS180813193577ORO",
               "metering.imagetype": "gold",
               "metering.resourcespeccode": "c1.medium.win",
               "metering.image_id": "65cb40e6-f67e-4bef-a1e7-808166a5999d",
               "image_name": "HEC_Public_Windows2008R2_Ent_64bit40G_English",
               "aaaaaa": "0",
               "metering.resourcetype": "1",
               "aaaa": "0",
               "metering.product_id": "00301-146042-0--0",
               "os_bit": "64",
               "vpc_id": "00159d7d-b3c3-4108-8bc4-6658814e6422",
               "os_type": "Windows",
               "charging_mode": "1"
           },
           "tags": [],
           "description": "ecs-1f30",
           "locked": false,
           "config_drive": "",
           "tenant_id": "edcb94a885a84ed3a3fdf8ea4d2741da",
           "user_id": "bb7f23e27e7e46f3aaceb5f53a158bdc",
           "key_name": "Autotest_Init_TC_OriginalAPI_Create_Keypairs_02_keypair",
           "os-extended-volumes:volumes_attached": [{
               "device": "/dev/sda",
               "bootIndex": "0",
               "id": "5043f66b-a0d8-4eb2-8c48-49976bcdc253",
               "delete_on_termination": "false"
           }],
                   "OS-EXT-STS:task_state": null,
           "OS-EXT-STS:power_state": 1,
           "OS-EXT-STS:vm_state": "active",
           "OS-EXT-SRV-ATTR:host": "az1.dc1",
           "OS-EXT-SRV-ATTR:instance_name": "instance-0013772d",
           "OS-EXT-SRV-ATTR:hypervisor_hostname": "nova001@248",
           "OS-DCF:diskConfig": "MANUAL",
           "OS-EXT-AZ:availability_zone":"az1-dc1", //AZ name
           "os:scheduler_hints": {
           },
           "OS-EXT-SRV-ATTR:root_device_name": "/dev/sda",
           "OS-EXT-SRV-ATTR:ramdisk_id": "",

           "OS-SRV-USG:launched_at": "2018-08-13T11:57:53.576640",
           "OS-EXT-SRV-ATTR:kernel_id": "",
           "OS-EXT-SRV-ATTR:launch_index": 0,
           "host_status": "UP",
           "OS-EXT-SRV-ATTR:reservation_id": "r-xmjj4pnm",
           "OS-EXT-SRV-ATTR:hostname": "ecs-1f30",
           "sys_tags": [{
               "key": "_sys_enterprise_project_id",
               "value": "441d5677-b76a-4dd4-a97a-ef7fd633c095"
           }],
           "security_groups": [{
               "name": "default"
           }]
       }]
   }

Returned Values
---------------

See :ref:`Returned Values for General Requests <en-us_topic_0022067716>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0022067717>`.
