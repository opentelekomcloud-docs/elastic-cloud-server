How Can I Obtain the Permission to Remotely Log In to a Windows ECS?
====================================================================

Symptom
-------

When you connect a remote desktop to a Windows ECS, the system prompts that you need to be granted the right to sign in through Remote Desktop Services.

| **Figure 1** Remote login right missing.
| |image1|

Solution
--------

#. Open the **cmd** window and enter **gpedit.msc**.
#. Click **OK** to start Local Group Policy Editor.
#. Choose **Computer Configuration** > **Windows Settings** > **Security Settings** > **Local Policies** > **User Rights Assignment**.

   a. Locate and double-click **Allow log on through Remote Desktop Services**. Ensure that **Administrators** and **Remote Desktop Users** have been added.\ **Figure 2** Allow log on through Remote Desktop Services properties
      |image2|
   b. Locate and double-click **Deny log on through Remote Desktop Services**. If the administrator account exists, delete it.\ **Figure 3** Deny log on through Remote Desktop Services properties
      |image3|


.. |image1| image:: /_static/images/en-us_image_0288997257.png
   :class: imgResize

.. |image2| image:: /_static/images/en-us_image_0288997258.png
   :class: imgResize

.. |image3| image:: /_static/images/en-us_image_0288997259.png
   :class: imgResize

