:original_name: en-us_topic_0247282819.html

.. _en-us_topic_0247282819:

Why Am I Seeing an FTP Folder Error When I Open a Folder on an FTP Server?
==========================================================================

Symptom
-------

An error occurs when you open a folder on an FTP server. The system displays a message asking you to check permissions.


.. figure:: /_static/images/en-us_image_0247338934.png
   :alt: **Figure 1** FTP Folder Error

   **Figure 1** FTP Folder Error

Possible Causes
---------------

The FTP firewall configured for the browser does not allow you to open the folder.

Solution
--------

The following uses Internet Explorer as an example.

#. Open the Internet Explorer and choose **Tools** > **Internet options**.

#. Click the **Advanced** tab.

#. Deselect **Use Passive FTP (for firewall and DSL modem compatibility)**.


   .. figure:: /_static/images/en-us_image_0247293312.png
      :alt: **Figure 2** Internet Options

      **Figure 2** Internet Options

#. Click **OK**, restart Internet Explorer, and open the folder on the FTP server again.
