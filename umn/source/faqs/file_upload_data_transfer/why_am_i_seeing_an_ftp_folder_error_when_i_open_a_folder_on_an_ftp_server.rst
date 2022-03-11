Why Am I Seeing an FTP Folder Error When I Open a Folder on an FTP Server?
==========================================================================

Symptom
-------

An error occurs when you open a folder on an FTP server. The system displays a message asking you to check permissions.

| **Figure 1** FTP Folder Error
| |image1|

Possible Causes
---------------

The FTP firewall configured for the browser does not allow you to open the folder.

Solution
--------

The following uses Internet Explorer as an example.

#. Open the Internet Explorer and choose **Tools** > **Internet options**.
#. Click the **Advanced** tab.
#. Deselect **Use Passive FTP (for firewall and DSL modem compatibility)**.\ **Figure 2** Internet Options
   |image2|
#. Click **OK**, restart Internet Explorer, and open the folder on the FTP server again.



.. |image1| image:: /_static/images/en-us_image_0247338934.png
   :class: imgResize

.. |image2| image:: /_static/images/en-us_image_0247293312.png
   :class: imgResize

