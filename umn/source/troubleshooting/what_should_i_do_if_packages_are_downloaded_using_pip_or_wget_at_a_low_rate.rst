:original_name: en-us_topic_0107490388.html

.. _en-us_topic_0107490388:

What Should I Do If Packages Are Downloaded Using PIP or wget at a Low Rate?
============================================================================

Symptom
-------

When a user runs the wget command to download software packages, the download rate is far less than the bandwidth.


.. figure:: /_static/images/en-us_image_0107505891.png
   :alt: **Figure 1** wget-based package downloading

   **Figure 1** wget-based package downloading

Possible Causes
---------------

The official PIP website is accessed using HTTPS. Each time PIP is used to install a third-party Python module, the source code package must be downloaded at the official PIP website. Therefore, openssl packages are required.

Solution
--------

Run the following command to install openssl packages:

**yum install openssl openssl-devel**
