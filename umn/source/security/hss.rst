:original_name: en-us_topic_0206596990.html

.. _en-us_topic_0206596990:

HSS
===

What Is HSS?
------------

Host Security Service (HSS) helps you identify and manage the assets on your servers, eliminate risks, and defend against intrusions and web page tampering. There are also advanced protection and security operations functions available to help you easily detect and handle threats.

After installing the HSS agent on your ECSs, you will be able to check the ECS security status and risks in a region on the HSS console.

How Do I Use HSS?
-----------------

Before using the HSS service, install the agent on your ECS.

-  **Scenario 1: An ECS is to be created.**

   When you use certain public images to create ECSs, you are advised to use HSS to protect your ECSs.

   Select one of the following options:

   -  **Advanced HSS edition (paid)**: You can choose the enterprise edition and you need to pay for it.
   -  **None**: HSS is disabled and servers are not protected.

   After you select an HSS edition, the system automatically installs the HSS agent, enables account cracking prevention, and offers host security functions.

-  **Scenario 2: An ECS is already created and HSS is not configured for it.**

   For an existing ECS without HSS configured, you can manually install an Agent on it.

   For details, see the *Host Security Service User Guide*.

How Do I Check Host Security Statuses?
--------------------------------------

On the **Server** tab, you can view the ECS security statuses in the current region.

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and project.
#. Click |image2| and choose **Security** > **Host Security Service**.
#. Choose **Asset Management** > **Servers & Quota** and go to the **Servers** tab to view the protection status of the target servers.

   .. table:: **Table 1** Statuses

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================+
      | Agent Status                      | -  **Not installed**: The agent has not been started or even has not been installed.                                                                                                                    |
      |                                   |                                                                                                                                                                                                         |
      |                                   | -  **Online**: The agent is running properly.                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                         |
      |                                   | -  **Offline**: The agent fails to communicate with the HSS server. Therefore, HSS cannot protect your ECS.                                                                                             |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    Click **Offline**. Then, the ECSs with agent being offline and the offline reasons are displayed.                                                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protection Status                 | -  **Protected**: The ECS is fully protected by HSS.                                                                                                                                                    |
      |                                   | -  **Unprotected**: HSS is disabled for the ECS. After the agent is installed, click **Enable** in the **Operation** column to enable protection.                                                       |
      |                                   | -  **Protection interruption**: The ECS is not protected, because the HSS protection server is interrupted. You can hover the cursor on |image3| next to **Protection interruption** to view the cause. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scan Results                      | -  **Risky**: The ECS is risky.                                                                                                                                                                         |
      |                                   | -  **Safe**: No risks are detected.                                                                                                                                                                     |
      |                                   | -  **Pending risk detection**: HSS is not enabled for the ECS.                                                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

For more details, see `What Is HSS? <https://docs.otc.t-systems.com/host-security-service/umn/introduction/index.html>`__

.. |image1| image:: /_static/images/en-us_image_0000002188678994.png
.. |image2| image:: /_static/images/en-us_image_0000001526737785.jpg
.. |image3| image:: /_static/images/en-us_image_0000002039480781.png
