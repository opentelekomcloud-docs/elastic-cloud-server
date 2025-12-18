:original_name: en-us_topic_0093492518.html

.. _en-us_topic_0093492518:

Attaching a Network Interface
=============================

Scenarios
---------

If your ECS requires multiple network interfaces, you can attach them to your ECS.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. Click the name of the ECS to which you want to attach a network interface.

   The ECS details page is displayed.

#. On the **Network Interfaces** tab, click **Attach Network Interface**.

#. Select either of the following methods to attach the network interface.

   -  Use an existing network interface.

      a. (Optional) Search for the network interface by name, ID, or private IP address.
      b. In the network interface list, select the target one.

   -  Create a new network interface.

      Set the subnet and security group for the network interface to be attached.


      .. figure:: /_static/images/en-us_image_0000002351500708.png
         :alt: **Figure 1** Configuring the subnet and security group

         **Figure 1** Configuring the subnet and security group

      -  **Subnet**: the subnet that the network interface belongs to.
      -  **New Private IP Address**: If you want to add a network interface with a specified IP address, enter an IP address into the **New Private IP Address** field.
      -  **Security Group**: You can select multiple security groups. In such a case, the access rules of all the selected security groups will apply to the ECS.

#. Click **OK**.

Follow-up Procedure
-------------------

Some OSs cannot identify newly attached network interfaces. In this case, you need to manually activate the network interfaces. The following uses Ubuntu as an example to show how to activate network interfaces. Operations may vary depending on the operating system. You can refer to the corresponding OS documentation for assistance.

#. Locate the row containing the target ECS and click **Remote Login** in the **Operation** column.

   Log in to the ECS.

#. .. _en-us_topic_0093492518__li595089165210:

   Run the following command to view the network interface name:

   **ifconfig -a**

   In this example, the network interface name is **eth2**.

#. Run the following command to switch to the target directory:

   **cd /etc/network**

#. Run the following command to open the **interfaces** file:

   **vi interfaces**

#. Add the following information to the **interfaces** file:

   **auto** *eth2*

   **iface** *eth2* **inet dhcp**

#. Run the following command to save and exit the **interfaces** file:

   **:wq**

#. Run either the **ifup eth**\ **X** command or the **/etc/init.d/networking restart** command to make the newly added network interface take effect.

   *X* in the preceding command indicates the serial number of the network interface, for example, **ifup eth2**.

#. Run the following command to check whether the network interface name obtained in step :ref:`2 <en-us_topic_0093492518__li595089165210>` is displayed in the command output:

   **ifconfig**

   For example, check whether **eth2** is displayed in the command output.

   -  If yes, the newly added network interface has been activated. No further action is required.
   -  If no, the newly added network interface failed to be activated. Go to step :ref:`9 <en-us_topic_0093492518__li1695469165210>`.

#. .. _en-us_topic_0093492518__li1695469165210:

   Log in to the management console. On the ECS list page, locate the row that contains the target ECS and choose **More** > **Restart** in the **Operation** column.

#. Run **ifconfig** again to check whether the network interface name obtained in step :ref:`2 <en-us_topic_0093492518__li595089165210>` is displayed in the command output.

   -  If yes, no further action is required.
   -  If no, contact customer service.

.. |image1| image:: /_static/images/en-us_image_0000002188678994.png
