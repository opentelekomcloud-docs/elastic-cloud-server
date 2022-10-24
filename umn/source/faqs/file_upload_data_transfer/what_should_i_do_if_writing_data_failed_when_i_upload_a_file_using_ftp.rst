:original_name: en-us_topic_0170139798.html

.. _en-us_topic_0170139798:

What Should I Do If Writing Data Failed When I Upload a File Using FTP?
=======================================================================

Symptom
-------

When I attempted to upload a file using FTP, writing data failed. As a result, the file transfer failed.

Constraints
-----------

The operations described in this section apply to FTP on Windows ECSs only.

Possible Causes
---------------

When NAT is enabled on the FTP server, the FTP client must connect to the FTP server in passive mode. In such a case, the public IP address (EIP) of the server cannot be accessed from the router. Therefore, you need to add the EIP to the public IP address list on the server. Additionally, set the port range to limit the number of ports with data forwarded by the router.

Solution
--------

The public IP address must be associated with the private IP address using NAT. Therefore, the server must be configured accordingly.

#. Configure the public IP address of the server.

   Choose **Edit** > **Settings**.


   .. figure:: /_static/images/en-us_image_0171674763.png
      :alt: **Figure 1** Setting the public IP address

      **Figure 1** Setting the public IP address

#. Choose **Passive mode settings**, set the port range (for example, 50000-50100) for transmitting data, and enter the target public IP address.


   .. figure:: /_static/images/en-us_image_0182087025.png
      :alt: **Figure 2** Setting the range of ports for data transmission

      **Figure 2** Setting the range of ports for data transmission

#. Click **OK**.

#. Allow traffic on TCP ports 50000-50100 and 21 in the security group in the inbound direction.

#. Test the connection on the client.
