:original_name: en-us_topic_0198270920.html

.. _en-us_topic_0198270920:

Configuring DNS
===============

A DNS server is used to resolve domain names of file systems. The DNS server IP address is 100.125.4.25.

Scenarios
---------

By default, the IP address of the DNS server used to resolve domain names of file systems is automatically configured on ECSs when creating ECSs. No manual configuration is needed except when the resolution fails due to a change in the DNS server IP address.

Windows Server 2012 is used as an example in the operation procedures for Windows.

Procedure (Linux)
-----------------

#. Log in to the ECS as user **root**.

#. .. _en-us_topic_0198270920__en-us_topic_0054116434_li13553756203149:

   Run the **vi /etc/resolv.conf** command to edit the **/etc/resolv.conf** file. Add the DNS server IP address above the existing nameserver information. See :ref:`Figure 1 <en-us_topic_0198270920__en-us_topic_0054116434_fig3735131720121>`.

   .. _en-us_topic_0198270920__en-us_topic_0054116434_fig3735131720121:

   .. figure:: /_static/images/en-us_image_0078780345.png
      :alt: **Figure 1** Configuring DNS

      **Figure 1** Configuring DNS

   The format is as follows:

   .. code-block::

      nameserver 100.125.4.25

#. Press **Esc**, input **:wq**, and press **Enter** to save the changes and exit the vi editor.

#. Run the following command to check whether the IP address is successfully added:

   **cat /etc/resolv.conf**

#. Run the following command to check whether an IP address can be resolved from the file system domain name:

   **nslookup** *File system domain name*

   .. note::

      Obtain the file system domain name from the file system mount point.

#. (Optional) In a network environment of the DHCP server, edit the **/etc/resolv.conf** file to prevent the file from being automatically modified upon an ECS startup, and prevent the DNS server IP address added in :ref:`2 <en-us_topic_0198270920__en-us_topic_0054116434_li13553756203149>` from being reset.

   a. Run the following command to lock the file:

      **chattr +i /etc/resolv.conf**

      .. note::

         Run the **chattr -i /etc/resolv.conf** command to unlock the file if needed.

   b. Run the following command to check whether the editing is successful:

      **lsattr /etc/resolv.conf**

      If the information shown in :ref:`Figure 2 <en-us_topic_0198270920__en-us_topic_0054116434_fig46855620155120>` is displayed, the file is locked.

      .. _en-us_topic_0198270920__en-us_topic_0054116434_fig46855620155120:

      .. figure:: /_static/images/en-us_image_0058331748.png
         :alt: **Figure 2** A locked file

         **Figure 2** A locked file

Procedure (Windows)
-------------------

#. Go to the ECS console and log in to the ECS running Windows Server 2012.

#. Click **This PC** in the lower left corner.

#. On the page that is displayed, right-click **Network** and choose **Properties** from the drop-down list. The **Network and Sharing Center** page is displayed, as shown in :ref:`Figure 3 <en-us_topic_0198270920__en-us_topic_0054116434_fig11811485719>`. Click **Local Area Connection**.

   .. _en-us_topic_0198270920__en-us_topic_0054116434_fig11811485719:

   .. figure:: /_static/images/en-us_image_0110762886.png
      :alt: **Figure 3** Page for network and sharing center

      **Figure 3** Page for network and sharing center

#. In the **Activity** area, select **Properties**. See :ref:`Figure 4 <en-us_topic_0198270920__en-us_topic_0054116434_fig18980173031015>`.

   .. _en-us_topic_0198270920__en-us_topic_0054116434_fig18980173031015:

   .. figure:: /_static/images/en-us_image_0110763434.png
      :alt: **Figure 4** Local area connection

      **Figure 4** Local area connection

#. In the **Local Area Connection Properties** dialog box that is displayed, select **Internet Protocol Version 4 (TCP/IPv4)** and click **Properties**. See :ref:`Figure 5 <en-us_topic_0198270920__en-us_topic_0054116434_fig146301518171620>`.

   .. _en-us_topic_0198270920__en-us_topic_0054116434_fig146301518171620:

   .. figure:: /_static/images/en-us_image_0110764366.png
      :alt: **Figure 5** Local area connection properties

      **Figure 5** Local area connection properties

#. In the dialog box that is displayed, select **Use the following DNS server addresses:** and configure DNS, as shown in :ref:`Figure 6 <en-us_topic_0198270920__en-us_topic_0054116434_fig82464042713>`. The DNS server IP address is 100.125.4.25. After completing the configuration, click **OK**.

   .. _en-us_topic_0198270920__en-us_topic_0054116434_fig82464042713:

   .. figure:: /_static/images/en-us_image_0110765557.png
      :alt: **Figure 6** Configuring DNS on Windows

      **Figure 6** Configuring DNS on Windows
