Attaching a Disk to an ECS
==========================

Function
--------

This API is used to attach a disk to an ECS.

Constraints
-----------

#. If you attach a bootable disk to an ECS, you must specify the disk drive letter.
#. A disk created using a backup cannot be attached to an ECS as the system disk.
#. An ECS in the **SUSPENDED** or **PAUSED** state, which is specified using the **OS-EXT-STS:vm_state** parameter of the ECS, cannot have a disk attached.
#. The EVS must be in the **available** status.
#. The EVS disk and the target ECS must be located in the same AZ.
#. VBD EVS disks cannot be attached to BMSs.

URI
---

POST /v2/{project_id}/servers/{server_id}/os-volume_attachments

POST /v2.1/{project_id}/servers/{server_id}/os-volume_attachments

`Table 1 <#enustopic0031167350table60562285165259>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0031167350table60562285165259:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0031167350table38613152151549>`__ describes the request parameters. 

.. _ENUSTOPIC0031167350table38613152151549:

.. table:: **Table 2** Request parameters

   +------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory | Type   | Description                                                                                                   |
   +==================+===========+========+===============================================================================================================+
   | volumeAttachment | Yes       | Object | Specifies the volumes to be attached. For details, see `Table 3 <#enustopic0031167350table40707503151632>`__. |
   +------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0031167350table40707503151632:

.. table:: **Table 3** **volumeAttachment** field description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                           |
   +=================+=================+=================+=======================================================================================================================================================================================================+
   | volumeId        | Yes             | String          | Specifies the ID of the disk to be attached. The value is in UUID format.                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | device          | No              | String          | Specifies the device name, such as **/dev/sda** or **/dev/sdb**.                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                       |
   |                 |                 |                 | The new disk device name cannot be the same as an existing one.                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                       |
   |                 |                 |                 | The device name must be specified based on the sequence of existing device names. Otherwise, the system automatically generates one.                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                       |
   |                 |                 |                 | .. note::                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                       |
   |                 |                 |                 |    VBD disk device names can only be **/dev/vdb** through **/dev/vdx**. You are advised to attach the VBD disks in alphabetical order. Otherwise, the disk drive letters may be incorrect on the ECS. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

`Table 4 <#enustopic0031167350table57959838>`__ describes the response parameters. 

.. _ENUSTOPIC0031167350table57959838:

.. table:: **Table 4** Response parameters

   +------------------+--------+---------------------------------------------------------------------------------------------------------------+
   | Parameter        | Type   | Description                                                                                                   |
   +==================+========+===============================================================================================================+
   | volumeAttachment | Object | Specifies the disks attached to an ECS. For details, see `Table 5 <#enustopic0031167350table548498215180>`__. |
   +------------------+--------+---------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0031167350table548498215180:

.. table:: **Table 5** **volumeAttachment** field description

   +-----------+--------+------------------------------------------------------------+
   | Parameter | Type   | Description                                                |
   +===========+========+============================================================+
   | device    | String | Specifies the device name.                                 |
   +-----------+--------+------------------------------------------------------------+
   | serverId  | String | Specifies the ID of the target ECS in UUID format.         |
   +-----------+--------+------------------------------------------------------------+
   | id        | String | Specifies the disk ID in UUID format.                      |
   +-----------+--------+------------------------------------------------------------+
   | volumeId  | String | Specifies the attaching ID, which is the same as the UUID. |
   +-----------+--------+------------------------------------------------------------+

Example Request
---------------

.. code-block::

   POST https://{endpoint}/v2/{project_id}/servers/{server_id}/os-volume_attachments
   POST https://{endpoint}/v2.1/{project_id}/servers/{server_id}/os-volume_attachments

.. code-block::

   {
       "volumeAttachment": {
           "volumeId": "54667652-3029-4af8-9222-2d53066fd61c",
           "device": "/dev/sdb"
       }
   }

Example Response
----------------

.. code-block::

   {
       "volumeAttachment": {
           "device": "/dev/vdb",
           "serverId": "ab258e25-e351-47c7-b6e3-0749c5d9ed6a",
           "id": "54667652-3029-4af8-9222-2d53066fd61c",
           "volumeId": "54667652-3029-4af8-9222-2d53066fd61c"
       }
   }

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.


