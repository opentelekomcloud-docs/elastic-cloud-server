Adding Tags to an ECS in a Batch
================================

Function
--------

-  This API is used to add tags to a specified ECS in a batch.
-  The Tag Management Service (TMS) uses this API to batch manage the tags of an ECS.

Constraints
-----------

-  An ECS allows a maximum of 10 tags.

-  This API is idempotent.

   During tag creation, if a tag exists (both the key and value are the same as those of an existing tag), the tag is successfully processed by default.

-  A new tag will overwrite the original one if their keys are the same and values are different.

URI
---

POST /v1/{project_id}/cloudservers/{server_id}/tags/action

`Table 1 <#enustopic0167811963table73051127201915>`__ describes the parameters in the URI. 

.. _ENUSTOPIC0167811963table73051127201915:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   server_id  Yes       Specifies the ECS ID.
   ========== ========= =========================

Request
-------

`Table 2 <#enustopic0167811963table69204518218>`__ describes the request parameters.



.. _ENUSTOPIC0167811963table69204518218:

.. table:: **Table 2** Request parameters

   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                                                |
   +===========+===========+==================+============================================================================================================================+
   | tags      | Yes       | Array of objects | Specifies tags. For details, see `Table 3 <#enustopic0167811963table1534514266207>`__.                                     |
   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------+
   | action    | Yes       | String           | Specifies the operation. (Only lowercase letters are supported.) For example, **create** indicates the creation operation. |
   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------+



.. _ENUSTOPIC0167811963table1534514266207:

.. table:: **Table 3** **tags** field description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                               |
   +=================+=================+=================+===========================================================================+
   | key             | Yes             | String          | Specifies the tag key.                                                    |
   |                 |                 |                 |                                                                           |
   |                 |                 |                 | -  Cannot be left blank.                                                  |
   |                 |                 |                 | -  Must be unique for each resource.                                      |
   |                 |                 |                 | -  Contains a maximum of 36 characters.                                   |
   |                 |                 |                 | -  Can only consist of digits, letters, hyphens (-), and underscores (_). |
   |                 |                 |                 | -  Must be unique and cannot be left blank.                               |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------+
   | value           | Yes             | String          | Specifies the tag value.                                                  |
   |                 |                 |                 |                                                                           |
   |                 |                 |                 | -  Contains a maximum of 43 characters.                                   |
   |                 |                 |                 | -  Can only consist of digits, letters, hyphens (-), and underscores (_). |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------+

Response
--------

None

Example Request
---------------

.. code-block::

   POST  https://{endpoint}/v1/{project_id}/cloudservers/{server_id}/tags/action

.. code-block::

   {
       "action": "create",
       "tags": [
           {
               "key": "key1",
               "value": "value1"
           },
           {
               "key": "key2",
               "value": "value3"
           }
       ]
   }

Example Response
----------------

None

Returned Values
---------------

See `Returned Values for General Requests <../../common_parameters/returned_values_for_general_requests.html>`__.

Error Codes
-----------

See `Error Codes <../../appendix/error_codes.html>`__.


