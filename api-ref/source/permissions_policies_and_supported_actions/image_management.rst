Image Management
================



.. _ENUSTOPIC0103072348table326212151339:

+------------------------------------------+----------------------------------------------------+-------------------------+----------------------+
| Permission                               | API                                                | Action                  | Dependent Permission |
+==========================================+====================================================+=========================+======================+
| Creating an Image (Native OpenStack API) | POST /v2/{project_id}/servers/{server_id}/action   | ecs:servers:createImage | evs:volumes:get      |
|                                          |                                                    |                         |                      |
|                                          | POST /v2.1/{project_id}/servers/{server_id}/action |                         | evs:snapshots:create |
|                                          |                                                    |                         |                      |
|                                          |                                                    |                         | ims:images:create    |
|                                          |                                                    |                         |                      |
|                                          |                                                    |                         | ims:images:get       |
|                                          |                                                    |                         |                      |
|                                          |                                                    |                         | ims:images:list      |
|                                          |                                                    |                         |                      |
|                                          |                                                    |                         | ims:images:update    |
|                                          |                                                    |                         |                      |
|                                          |                                                    |                         | ims:images:delete    |
+------------------------------------------+----------------------------------------------------+-------------------------+----------------------+


