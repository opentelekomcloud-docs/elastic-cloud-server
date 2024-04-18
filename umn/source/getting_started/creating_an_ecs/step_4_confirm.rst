:original_name: en-us_topic_0163572592.html

.. _en-us_topic_0163572592:

Step 4: Confirm
===============

Confirming the Order
--------------------

#. On the **Confirm** page, view details about the ECS configuration.

   To learn more about the price, click **Pricing details**.

#. Set **Enterprise Project**.

   This function is provided for enterprise users. To enable this function, contact customer service.

   An enterprise project facilitates project-level management and grouping of cloud resources and users. The default project is **default**.

#. Set the number of ECSs to be created.

   After the configuration, click **Price Calculator** to view the ECS configuration fee.

#. Confirm the configuration and click **Create Now**.

Follow-up Procedure
-------------------

-  After an ECS with an EIP bound is created, the system automatically generates a reverse domain name in the format of "ecs-xx-xx-xx-xx.compute.xxx.com" for each EIP by default. In the format, "xx-xx-xx-xx" indicates the EIP, and "xxx" indicates the domain name of the cloud service provider. You can use the reverse domain name to access the ECS.

   Use one of the following commands to obtain the default reverse domain name of an EIP:

   -  ping -a *EIP*
   -  nslookup [-qt=ptr] *EIP*
   -  dig -x *EIP*
