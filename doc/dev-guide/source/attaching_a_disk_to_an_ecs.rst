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

         URI format: POST /v2/{project_id}/volumes

         For details, see "Creating EVS Disks" in *Elastic Volume Service API Reference*.

      -  Request example

         POST https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/volumes

         Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

         Body:

         .. code-block::

            {
                "volume": {
                    "name": "openapi_vol02",
                    "availability_zone": "eu-de-01",
                    "description": "create for api test",
                    "volume_type": "SSD",
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
                "volume_type": "SSD",
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

      URI format: POST /v2/{project_id}/servers/{server_id}/os-volume_attachments

      For details, see section "Attaching an ECS Data Disk" in *Elastic Cloud Server API Reference*.

   -  Request example

      POST https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/servers/11e8f727-d439-4ed1-b3b8-33f46c0379c4/os-volume_attachments

      Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

      Body:

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
             "device": "/dev/sdb",
             "serverId": "11e8f727-d439-4ed1-b3b8-33f46c0379c4",
             "id": "51f45e08-1d4f-44c6-a4a9-84a488e0e8d3",
             "volumeId": "51f45e08-1d4f-44c6-a4a9-84a488e0e8d3"
           }
         }

#. Verify the disk attachment.

   -  API

      URI format: GET /v2/{project_id}/servers/{server_id}/os-volume_attachments

      For details, see section "Listing Details About Disks Attached to an ECS" in *Elastic Cloud Server API Reference*.

   -  Request example

      GET https://*{endpoint}*/v2/74610f3a5ad941998e91f076297ecf27/servers/11e8f727-d439-4ed1-b3b8-33f46c0379c4/os-volume_attachments

      Obtain the endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

   -  Response example

      .. code-block::

         {
             "volumeAttachments": [
                 {
                     "device": "/dev/sda",
                     "id": "51f45e08-1d4f-44c6-a4a9-84a488e0e8d3",
                     "serverId": "11e8f727-d439-4ed1-b3b8-33f46c0379c4",
                     "volumeId": "51f45e08-1d4f-44c6-a4a9-84a488e0e8d3"
                 },
                 {
                     "device": "/dev/sdb",
                     "id": "51f45e08-1d4f-44c6-a4a9-84a488e0e8d3",
                     "serverId": "11e8f727-d439-4ed1-b3b8-33f46c0379c4",
                     "volumeId": "51f45e08-1d4f-44c6-a4a9-84a488e0e8d3"
                 }
             ]
         }
