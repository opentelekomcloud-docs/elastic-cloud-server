:original_name: en-us_topic_0134192996.html

.. _en-us_topic_0134192996:

Attaching a Disk to an ECS
==========================

Scenarios
---------

If the existing disks of an ECS fail to meet service requirements, for example, due to insufficient disk space or poor disk performance, you can attach more available disks to the ECS, or call the EVS disk creation API to create disks and attach them to the ECS. To attach an EVS disk to an ECS, you need to call the required API.

.. note::

   You can attach a data disk by setting the **data_volumes** parameter during ECS creation or attach a data disk after the ECS is created. This section describes how to attach a disk to a created ECS.

Involved APIs
-------------

Attaching a disk involves the following APIs:

-  API for creating an EVS disk
-  API for attaching a disk to an ECS
-  API for viewing disks attached to an ECS

Procedure
---------

#. Create an EVS disk.

   a. Create an EVS disk.

      -  API

         URI format: POST /v2/{tenant_id}/volumes

         For details, see section "Creating an EVS Disk (Native OpenStack API v2)" in *Elastic Cloud Server API Reference*.

      -  Request example

         POST: https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/volumes

         Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

         Body

         .. code-block::

            {
                "volume": {
                    "name": "openapi_vol02",
                    "availability_zone": "eu-de-01",
                    "description": "create for api test",
                    "volume_type": "SATA",
                    "size": 40
                }
            }

      -  Response example

         .. code-block::

            {
              "volume": {
                "status": "creating",
                "user_id": "f79791beca3c48159ac2553fff22e166",
                "attachments": [],
                "links": [
                  {
                    "href": "https://xxx/v2/74610f3a5ad941998e91f076297ecf27/volumes/51f45e08-1d4f-44c6-a4a9-84a488e0e8d3",
                    "rel": "self"
                  },
                  {
                    "href": "https://xxx/74610f3a5ad941998e91f076297ecf27/volumes/51f45e08-1d4f-44c6-a4a9-84a488e0e8d3",
                    "rel": "bookmark"
                  }
                ],
                "availability_zone": "eu-de-01",
                "bootable": "false",
                "encrypted": false,
                "created_at": "2018-05-16T11:19:33.992984",
                "description": "create for api test",
                "updated_at": null,
                "volume_type": "SATA",
                "name": "openapi_vol02",
                "replication_status": "disabled",
                "consistencygroup_id": null,
                "source_volid": null,
                "snapshot_id": null,
                "shareable": false,
                "multiattach": false,
                "metadata": {
                  "__system__volume_name": "openapi_vol02"
                },
                "id": "51f45e08-1d4f-44c6-a4a9-84a488e0e8d3",
                "size": 40
              }
            }

   b. Record the **volume** ID in the response.

#. Attach the disk to the ECS.

   -  API

      URI format: POST /v2/{tenant_id}/servers/{server_id}/os-volume_attachments

      For details, see section "Attaching a Disk to an ECS" in *Elastic Cloud Server API Reference*.

   -  Request example

      https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/servers/9f4d9281-95e7-4915-a126-1ee597101e2e/os-volume_attachments

      Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

      Body

      .. code-block::

         {
             "volumeAttachment": {
                 "volumeId": "51f45e08-1d4f-44c6-a4a9-84a488e0e8d3",
                 "device": "/dev/sdb"
             }
         }

   -  Response example

      .. code-block::

         {
           "volumeAttachment": {
             "id": "51f45e08-1d4f-44c6-a4a9-84a488e0e8d3",
             "volumeId": "51f45e08-1d4f-44c6-a4a9-84a488e0e8d3",
             "serverId": "9f4d9281-95e7-4915-a126-1ee597101e2e",
             "device": "/dev/sdb"
           }
         }

#. Verify the disk attachment.

   -  API

      URI format: GET /v2/{tenant_id}/servers/{server_id}/os-volume_attachments

      For details, see section "Querying Disks Attached to an ECS" in *Elastic Cloud Server API Reference*.

   -  Request example

      https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/servers/9f4d9281-95e7-4915-a126-1ee597101e2e/os-volume_attachments

      Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

   -  Response example

      .. code-block::

         {
           "volumeAttachments": [
             {
               "volumeId": "4fc0b4cc-9d6c-431c-be70-3dfeec2ff6e0",
               "id": "4fc0b4cc-9d6c-431c-be70-3dfeec2ff6e0",
               "device": "/dev/sda",
               "serverId": "9f4d9281-95e7-4915-a126-1ee597101e2e"
             },
             {
               "volumeId": "51f45e08-1d4f-44c6-a4a9-84a488e0e8d3",
               "id": "51f45e08-1d4f-44c6-a4a9-84a488e0e8d3",
               "device": "/dev/sdb",
               "serverId": "9f4d9281-95e7-4915-a126-1ee597101e2e"
             }
           ]
         }
