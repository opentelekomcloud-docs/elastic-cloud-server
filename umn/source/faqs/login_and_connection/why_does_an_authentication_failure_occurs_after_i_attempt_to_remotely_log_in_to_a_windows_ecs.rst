:original_name: en-us_topic_0018339851.html

.. _en-us_topic_0018339851:

Why Does an Authentication Failure Occurs After I Attempt to Remotely Log In to a Windows ECS?
==============================================================================================

Symptom
-------

When a local computer running Windows attempts to access a Windows ECS using RDP (for example, MSTSC), an identity authentication failure occurs and the desired function is not supported.

-  If the error message contains only the information that an identity authentication failure occurs and that the desired function is not supported, rectify the fault by following the instructions provided in :ref:`Solution <en-us_topic_0018339851__section9947102411203>`.

-  If the error message shows that the fault was caused by "CredSSP Encryption Oracle Remediation", as shown in :ref:`Figure 1 <en-us_topic_0018339851__fig18932134871212>`, the fault may be caused by a security patch released by Microsoft in March 2018. This patch may affect RDP-based CredSSP connections. As a result, setting up RDP-based connections to ECSs failed. Rectify the fault by following the instructions provided in `official Microsoft document <https://support.microsoft.com/en-us/help/4093492/credssp-updates-for-cve-2018-0886-march-13-2018>`__.

   .. _en-us_topic_0018339851__fig18932134871212:

   .. figure:: /_static/images/en-us_image_0117334497.png
      :alt: **Figure 1** Failed to set up a remote desktop connection

      **Figure 1** Failed to set up a remote desktop connection

.. _en-us_topic_0018339851__section9947102411203:

Solution
--------

Modify the remote desktop connection settings on the Windows ECS:

#. Log in to the ECS.

#. Click **Start** in the lower left corner, right-click **Computer**, and choose **Properties** from the shortcut menu.

#. In the navigation pane on the left, choose **Remote settings**.

#. Click the **Remote** tab. In the **Remote Desktop** pane, select **Allow connections from computers running any version of Remote Desktop (less secure)**.


   .. figure:: /_static/images/en-us_image_0253037157.png
      :alt: **Figure 2** Remote settings

      **Figure 2** Remote settings

#. Click **OK**.
