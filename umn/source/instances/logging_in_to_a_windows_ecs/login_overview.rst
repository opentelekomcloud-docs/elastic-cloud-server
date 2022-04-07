.. _en-us_topic_0092494943:

Login Overview
==============

Constraints
-----------

-  Only a running ECS can be logged in.

-  Login usernames, passwords, and constraints vary depending on OSs running on the ECSs created using a public image. For details, see `Public Images Introduction <https://docs.otc.t-systems.com/en-us/ims/index.html>`__.

-  If an ECS uses key pair authentication, use the password obtaining function available on the management console to decrypt the private key used during ECS creation to obtain a password.

-  Certain G series of ECSs do not support remote login provided by the management console. If you need to remotely log in to the ECSs, install the VNC server on them. For details, see :ref:`GPU-accelerated ECSs <en-us_topic_0097289624>`. You are suggested to log in to the ECSs using MSTSC.

-  If you log in to a GPU-accelerated ECS using MSTSC, GPU acceleration will fail. This is because MSTSC replaces the WDDM GPU driver with a non-accelerated remote desktop display driver. In such a case, you must use other methods to log in to the ECS, such as VNC. If the remote login function available on the management console fails to meet your service requirements, you must install a suitable remote login tool on the ECS, such as TightVNC.

   To download TightVNC, log in at https://www.tightvnc.com/download.php.

Login Modes
-----------

Select a login mode as required and log in to the target ECS.

.. table:: **Table 1** Windows login modes

   +-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   | ECS OS          | Local OS        | Connection Method                                                                                                                                           | Requirement                          |
   +=================+=================+=============================================================================================================================================================+======================================+
   | Windows         | Windows         | Use MSTSC.                                                                                                                                                  | The target ECS has had an EIP bound. |
   |                 |                 |                                                                                                                                                             |                                      |
   |                 |                 | Click **Start** on the local computer. In the **Search programs and files** text box, enter **mstsc** to open the **Remote Desktop Connection** dialog box. |                                      |
   |                 |                 |                                                                                                                                                             |                                      |
   |                 |                 | For details, see :ref:`Login Using MSTSC <en-us_topic_0017955381>`.                                                                                         |                                      |
   +-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                 | Linux           | Install a remote connection tool, for example, rdesktop.                                                                                                    |                                      |
   |                 |                 |                                                                                                                                                             |                                      |
   |                 |                 | For details, see :ref:`Logging In to a Windows ECS from a Linux Computer <en-us_topic_0275383051>`.                                                         |                                      |
   +-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                 | Windows         | Through the management console.                                                                                                                             | No EIP is required.                  |
   |                 |                 |                                                                                                                                                             |                                      |
   |                 |                 | For details, see :ref:`Login Using VNC <en-us_topic_0027268511>`.                                                                                           |                                      |
   +-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
