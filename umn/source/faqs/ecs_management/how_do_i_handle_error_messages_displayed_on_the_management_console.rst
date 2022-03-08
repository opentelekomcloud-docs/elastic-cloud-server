How Do I Handle Error Messages Displayed on the Management Console?
===================================================================

Symptom
-------

This section helps you resolve the following issues:

-  An error message was displayed on the management console after you performed ECS-related operations.
-  An error code was displayed after you used an ECS API (see *Elastic Cloud Server API Reference*).

Background
----------

After you perform ECS-related operations on the management console, the system displays the request status on the **Elastic Cloud Server** page. You can determine the request execution status based on the information displayed in the request status.

-  If the operation request is executed, the system automatically clears the task prompt.
-  If an error occurs during the request execution, the system displays an error code and its description in the taskbar.

Solution
--------

If an error occurs, check the error code and perform the corresponding operations listed in `Table 1 <#EN-US_TOPIC_0032398121__table52205309173837>`__.



.. _EN-US_TOPIC_0032398121__table52205309173837:

.. table:: **Table 1** Error codes and solution suggestions

   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Error Code                            | Message Displayed on the Management   | Solution Suggestion                   |
   |                                       | Console                               |                                       |
   +=======================================+=======================================+=======================================+
   | Ecs.0000                              | Request error. Try again later or     | Adjust the request structure as       |
   |                                       | contact customer service.             | directed in *Elastic Cloud Server API |
   |                                       |                                       | Reference*.                           |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Ecs.0001                              | The maximum number of ECSs or EVS     | Contact customer service and request  |
   |                                       | disks has been reached. Contact the   | an ECS quota increase.                |
   |                                       | customer service and request an ECS   |                                       |
   |                                       | quota increase.                       | NOTE:                                 |
   |                                       |                                       | Before requesting for increasing your |
   |                                       |                                       | ECS quota, consider the number of     |
   |                                       |                                       | to-be-added ECSs, vCPUs, and memory   |
   |                                       |                                       | capacity required.                    |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Ecs.0003                              | You do not have the permission or     | Contact customer service to check     |
   |                                       | your balance is insufficient.         | your account information.             |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Ecs.0005                              | System error. Try again later or      | Adjust the request structure as       |
   |                                       | contact customer service.             | directed in *Elastic Cloud Server API |
   |                                       |                                       | Reference*.                           |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Ecs.0010                              | The private IP address is in use.     | Use an idle IP address for ECS        |
   |                                       | Select an available IP address for    | creation.                             |
   |                                       | ECS creation.                         |                                       |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Ecs.0011                              | Invalid password. Change the password | Input a password that meets password  |
   |                                       | to make it meet the password          | complexity requirements. Then,        |
   |                                       | complexity requirements, and perform  | initial the request again.            |
   |                                       | the required operation again.         |                                       |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Ecs.0012                              | Insufficient IP addresses in the      | Release IP addresses in the subnet or |
   |                                       | subnet. Release IP addresses in the   | select another subnet for ECS         |
   |                                       | subnet or select another subnet for   | creation.                             |
   |                                       | ECS creation.                         |                                       |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Ecs.0013                              | Contact customer service and request  | Contact customer service and request  |
   |                                       | an EIP quota increase.                | an EIP quota increase.                |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Ecs.0015                              | The disk of this type is not          | Select a proper disk and attach it to |
   |                                       | supported by the ECS.                 | the ECS.                              |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Ecs.0100                              | Invalid ECS status. Change the status | Change the ECS status to the desired  |
   |                                       | and try again.                        | one and try again.                    |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Ecs.0103                              | The disk is unavailable.              | Change the ECS status to the desired  |
   |                                       |                                       | one and try again. If the EVS disk is |
   |                                       |                                       | faulty, contact customer service for  |
   |                                       |                                       | troubleshooting.                      |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Ecs.0104                              | The number of disks to be attached to | Detach EVS disks from the ECS before  |
   |                                       | an ECS exceeds the number allowed.    | attaching new ones.                   |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Ecs.0105                              | No system disk found.                 | Attach the system disk to the ECS and |
   |                                       |                                       | perform the desired operation again.  |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Ecs.0107                              | The number of shared disks to be      | Detach EVS disks from the ECS before  |
   |                                       | attached to an ECS exceeds the        | attaching new ones.                   |
   |                                       | maximum limit.                        |                                       |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Other error codes                     | Other error messages                  | Initiate the request again. If the    |
   |                                       |                                       | error persists, record the returned   |
   |                                       |                                       | error code and contact customer       |
   |                                       |                                       | service for troubleshooting.          |
   +---------------------------------------+---------------------------------------+---------------------------------------+

