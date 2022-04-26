:original_name: en-us_topic_0142195139.html

.. _en-us_topic_0142195139:

Responses (Batch Operation)
===========================

The following responses are only for resetting the passwords for logging in to ECSs in a batch and for modifying ECS specifications in a batch. For details about the responses of other batch operations, see :ref:`Responses (Task) <en-us_topic_0022067714>`.

-  Normal responses

   +-----------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                                                                             |
   +===========+==================+=========================================================================================================================================================+
   | response  | Array of objects | Specifies the response returned after a request is successfully submitted. For details, see :ref:`Table 1 <en-us_topic_0142195139__table849372311389>`. |
   +-----------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0142195139__table849372311389:

   .. table:: **Table 1** **response** field description

      +-----------+--------+-------------------------------------------------------------------------------------+
      | Parameter | Type   | Description                                                                         |
      +===========+========+=====================================================================================+
      | id        | String | Specifies the ID of the ECS on which the operation has been successfully performed. |
      +-----------+--------+-------------------------------------------------------------------------------------+

-  Abnormal responses

   +---------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type             | Description                                                                                                                                                |
   +===============+==================+============================================================================================================================================================+
   | error         | Object           | Specifies the error in a batch request. For details, see :ref:`Table 2 <en-us_topic_0142195139__table6409189311151>`.                                      |
   +---------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | internalError | Array of objects | Specifies the error in each request among the requests submitted in a batch. For details, see :ref:`Table 3 <en-us_topic_0142195139__table1540134517514>`. |
   +---------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0142195139__table6409189311151:

   .. table:: **Table 2** **error** field structure

      ========= ====== ===============================================
      Parameter Type   Description
      ========= ====== ===============================================
      message   String Describes a batch operation error.
      code      String Specifies the code for a batch operation error.
      ========= ====== ===============================================

   .. _en-us_topic_0142195139__table1540134517514:

   .. table:: **Table 3** **internalEroCMM.0101r** field description

      +---------------+--------+--------------------------------------------------------+
      | Parameter     | Type   | Description                                            |
      +===============+========+========================================================+
      | id            | String | Specifies the ID of the ECS on which a request failed. |
      +---------------+--------+--------------------------------------------------------+
      | error_message | String | Describes a single request failure.                    |
      +---------------+--------+--------------------------------------------------------+
      | error_code    | String | Specifies the code for a single request error.         |
      +---------------+--------+--------------------------------------------------------+

-  Example response

   Normal response

   .. code-block::

      { 
          "response": [
                        {
                          "id": "616fb98f-46ca-475e-917e-2563e5a8cd19"   
                        },
                        {
                          "id": "516fb98f-46ca-475e-917e-2563e5a8cd12"   
                        }
                     ]
      } 

   Abnormal response

   .. code-block::

      {
           "error": {
                       "code": "Ecs.xxxx",
                       "message": "xxxxxxxxxxxxxxx" 
                     },
           "internalError": [
                       {
                          "id": "616fb98f-46ca-475e-917e-2563e5a8cd19",
                          "error_code": "ECS.XXXX",
                          "error_message": "xxxxxxxxxxxxxxx" 
                        },
                       {
                           "id": "516fb98f-46ca-475e-917e-2563e5a8cd12",
                           "error_code": "ECS.XXXX",
                           "error_message": "xxxxxxxxxxxxxxx" 
                       }
                    ]
      }
