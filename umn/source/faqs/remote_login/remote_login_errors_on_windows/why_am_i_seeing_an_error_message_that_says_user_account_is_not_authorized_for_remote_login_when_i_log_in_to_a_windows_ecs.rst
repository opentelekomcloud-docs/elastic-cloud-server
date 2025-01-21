:original_name: en-us_topic_0264235948.html

.. _en-us_topic_0264235948:

Why Am I Seeing an Error Message That Says User Account is not Authorized for Remote Login When I Log In to a Windows ECS?
==========================================================================================================================

Symptom
-------

An error message is displayed indicating that the connection is denied because the user account is not authorized for remote login.


.. figure:: /_static/images/en-us_image_0288997346.png
   :alt: **Figure 1** Error message

   **Figure 1** Error message

Possible Causes
---------------

The remote desktop connection permissions have been incorrectly configured.

Solution
--------

#. Check remote desktop permissions on the ECS.

   a. In the **Run** dialog box, enter **secpol.msc** and click **OK** to open **Local Security Policy**.

   b. Choose **Local Policies** > **User Rights Assignment** > **Allow log on through Remote Desktop Services**.


      .. figure:: /_static/images/en-us_image_0288997347.png
         :alt: **Figure 2** Local security policy

         **Figure 2** Local security policy

   c. Check whether there are user groups or users that have been granted the remote login permission.

      If not, add required users or groups.


      .. figure:: /_static/images/en-us_image_0288997348.png
         :alt: **Figure 3** Allow log on through Remote Desktop Services properties

         **Figure 3** Allow log on through Remote Desktop Services properties

#. Check the target user group.

   a. Open the **Run** dialog box, enter **lusrmgr.msc**, and click **OK** to open **Local Users and Groups**.

   b. .. _en-us_topic_0264235948__en-us_topic_0173606024_li19821176204810:

      Double-click **Users** on the left.

   c. Double-click the name of the user to whom the login error message was displayed.

   d. In the displayed dialog box, click the **Member Of** tab. Ensure that the user belongs to the user group that is assigned with the remote login permission in :ref:`2.b <en-us_topic_0264235948__en-us_topic_0173606024_li19821176204810>`.


      .. figure:: /_static/images/en-us_image_0288997349.png
         :alt: **Figure 4** Checking the target user group

         **Figure 4** Checking the target user group

#. Check the remote desktop session host configuration.

   a. In the **Run** dialog box, enter **tsconfig.msc** and click **OK** to open **Remote Desktop Session Host Configuration**.

   b. Double-click **RDP-Tcp** or other connections added by a user under **Connections** and click the **Security** tab.


      .. figure:: /_static/images/en-us_image_0288997350.png
         :alt: **Figure 5** Security

         **Figure 5** Security

   c. Check whether there are user groups or users that have been granted the remote login permission under **Group or user names**.

      If not, add required users or groups.

   d. Restart the ECS or run the following commands in the CLI to restart the Remote Desktop Services:

      **net stop TermService**

      **net start TermService**
