:original_name: en-us_topic_0103072348.html

.. _en-us_topic_0103072348:

Image Management
================

+--------------------------------------------------------------------------+----------------------------------------------------+-------------------------+----------------------+
| Permission                                                               | API                                                | Action                  | Dependencies         |
+==========================================================================+====================================================+=========================+======================+
| :ref:`Creating an image (native OpenStack API) <en-us_topic_0065817694>` | POST /v2/{project_id}/servers/{server_id}/action   | ecs:servers:createImage | ecs:servers:list     |
|                                                                          |                                                    |                         |                      |
|                                                                          | POST /v2.1/{project_id}/servers/{server_id}/action |                         | evs:volumes:get      |
|                                                                          |                                                    |                         |                      |
|                                                                          |                                                    |                         | evs:snapshots:create |
|                                                                          |                                                    |                         |                      |
|                                                                          |                                                    |                         | ims:images:create    |
|                                                                          |                                                    |                         |                      |
|                                                                          |                                                    |                         | ims:images:get       |
|                                                                          |                                                    |                         |                      |
|                                                                          |                                                    |                         | ims:images:list      |
|                                                                          |                                                    |                         |                      |
|                                                                          |                                                    |                         | ims:images:update    |
|                                                                          |                                                    |                         |                      |
|                                                                          |                                                    |                         | ims:images:delete    |
|                                                                          |                                                    |                         |                      |
|                                                                          |                                                    |                         | ims:quotas:get       |
+--------------------------------------------------------------------------+----------------------------------------------------+-------------------------+----------------------+
