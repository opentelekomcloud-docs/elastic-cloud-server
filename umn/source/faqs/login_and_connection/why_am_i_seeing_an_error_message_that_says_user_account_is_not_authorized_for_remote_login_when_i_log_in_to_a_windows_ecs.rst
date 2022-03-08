Why Am I Seeing an Error Message That Says User Account is not Authorized for Remote Login When I Log In to a Windows ECS?
==========================================================================================================================

Symptom
-------

An error message is displayed indicating that the connection is denied because the user account is not authorized for remote login.

| **Figure 1** Error message
| |image1|

Possible Causes
---------------

The remote desktop connection permissions have been incorrectly configured.

Solution
--------

#. Check remote desktop permissions on the ECS.

   a. In the **Run** dialog box, enter **secpol.msc** and click **OK** to open **Local Security Policy**.

   b. Choose **Local Policies** > **User Rights Assignment** > **Allow log on through Remote Desktop Services**.\ **Figure 2** Local security policy
      |image2|

   c. Check whether there are user groups or users that have been granted the remote login permission.

      If not, add required users or groups.

      | **Figure 3** Allow log on through Remote Desktop Services properties
      | |image3|

#. Check the target user group.

   a. Open the **Run** dialog box, enter **lusrmgr.msc**, and click **OK** to open **Local Users and Groups**.
   b. Double-click **Users** on the left.
   c. Double-click the name of the user to whom the login error message was displayed.
   d. In the displayed dialog box, click the **Member Of** tab. Ensure that the user belongs to the user group that is assigned with the remote login permission in `2.b <#EN-US_TOPIC_0264235948__en-us_topic_0173606024_li19821176204810>`__.\ **Figure 4** Checking the target user group
      |image4|

#. Check the remote desktop session host configuration.

   a. In the **Run** dialog box, enter **tsconfig.msc** and click **OK** to open **Remote Desktop Session Host Configuration**.

   b. Double-click **RDP-Tcp** or other connections added by a user under **Connections** and click the **Security** tab.\ **Figure 5** Security
      |image5|

   c. Check whether there are user groups or users that have been granted the remote login permission under **Group or user names**.

      If not, add required users or groups.

   d. Restart the ECS or run the following commands in the CLI to restart the Remote Desktop Services:

      **net stop TermService**

      **net start TermService**


.. |image1| image:: /_static/images/en-us_image_0288997346.png
   :class: imgResize

.. |image2| image:: /_static/images/en-us_image_0288997347.png
   :class: imgResize

.. |image3| image:: /_static/images/en-us_image_0288997348.png

.. |image4| image:: /_static/images/en-us_image_0288997349.png
   :class: imgResize

.. |image5| image:: /_static/images/en-us_image_0288997350.png
   :class: imgResize

