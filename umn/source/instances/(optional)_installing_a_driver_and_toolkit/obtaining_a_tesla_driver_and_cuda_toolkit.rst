Obtaining a Tesla Driver and CUDA Toolkit
=========================================

Scenarios
---------

Before using a GPU-accelerated ECS, make sure that the desired Tesla driver and CUDA toolkit have been installed on the EIP. Otherwise, computing acceleration will not take effect. This section describes how to obtain a Tesla driver and CUDA toolkit. Select a driver version based on your ECS type.

For instructions about how to install the Tesla driver and CUDA toolkit, see `Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468.html>`__.

Downloading a Tesla Driver
--------------------------

`Download a driver <https://www.nvidia.com/Download/index.aspx?lang=en-us>`__ based on your ECS type.


.. _EN-US_TOPIC_0213874991__table394113539174:

.. table:: **Table 1** Mapping between Tesla drivers and ECS types

   ======== ====== ============== =======
   ECS Type Driver Product Series Product
   ======== ====== ============== =======
   P2s      Tesla  V              V100
   P2v      Tesla  V              V100
   P2       Tesla  V              V100
   P1       Tesla  P              P100
   PI2      Tesla  T              T4
   G6       Tesla  T              T4
   ======== ====== ============== =======

Downloading a CUDA Toolkit
--------------------------



.. _EN-US_TOPIC_0213874991__table189141151993:

.. table:: **Table 2** Path in which the CUDA toolkit is downloaded for P2s ECSs

   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | ECS Type              | OS                    | CUDA Version          | How to Obtain         | CPU Architecture      |
   +=======================+=======================+=======================+=======================+=======================+
   | P2s                   | CentOS 7.4 64bit      | 9.2 or later          | Select a CUDA version | x86_64                |
   |                       |                       |                       | as required.          |                       |
   | (V100)                |                       | If the kernel version |                       |                       |
   |                       |                       | is                    | h                     |                       |
   |                       |                       | 3.10                  | ttps://developer.nvid |                       |
   |                       |                       | .0-957.5.1.e17.x86_64 | ia.com/cuda-downloads |                       |
   |                       |                       | or earlier, install   |                       |                       |
   |                       |                       | the CUDA toolkit of   |                       |                       |
   |                       |                       | version 9.2.          |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | P2s                   | Ubuntu 16.04 64bit    | 9.2 or later          |                       | x86_64                |
   |                       |                       |                       |                       |                       |
   | (V100)                |                       | If the kernel version |                       |                       |
   |                       |                       | is 4.4.0-141-generic  |                       |                       |
   |                       |                       | or earlier, install   |                       |                       |
   |                       |                       | the CUDA toolkit of   |                       |                       |
   |                       |                       | version 9.2.          |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | P2s                   | Windows Server 2016   | 9.2 or later          |                       | x86_64                |
   |                       | Standard 64bit        |                       |                       |                       |
   | (V100)                |                       |                       |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | P2s                   | Windows Server 2012   | 9.2 or later          |                       | x86_64                |
   |                       | R2 Standard 64bit     |                       |                       |                       |
   | (V100)                |                       |                       |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+



.. _EN-US_TOPIC_0213874991__table6501649192616:

.. table:: **Table 3** Path in which the CUDA toolkit is downloaded for P2v ECSs

   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | ECS Type              | OS                    | CUDA Version          | How to Obtain         | CPU Architecture      |
   +=======================+=======================+=======================+=======================+=======================+
   | P2v                   | CentOS 7.7 64bit      | 9.2/10.1              | Version 9.2:          | x86_64                |
   |                       |                       |                       | https://dev           |                       |
   | (V100)                |                       | If the kernel version | eloper.nvidia.com/cud |                       |
   |                       |                       | is                    | a-92-download-archive |                       |
   |                       |                       | 3.10                  |                       |                       |
   |                       |                       | .0-957.5.1.e17.x86_64 | Version 10.1:         |                       |
   |                       |                       | or earlier, install   |                       |                       |
   |                       |                       | the CUDA toolkit of   | https://developer.    |                       |
   |                       |                       | version 9.2.          | nvidia.com/cuda-10.1- |                       |
   |                       |                       |                       | download-archive-base |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | P2v                   | EulerOS 2.5 64bit     | 9.2                   |                       | x86_64                |
   |                       |                       |                       |                       |                       |
   | (V100)                |                       |                       |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | P2v                   | Ubuntu 16.04 64bit    | 9.2/10.1              |                       | x86_64                |
   |                       |                       |                       |                       |                       |
   | (V100)                |                       | If the kernel version |                       |                       |
   |                       |                       | is 4.4.0-141-generic  |                       |                       |
   |                       |                       | or earlier, install   |                       |                       |
   |                       |                       | the CUDA toolkit of   |                       |                       |
   |                       |                       | version 9.2.          |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | P2v                   | Windows Server 2019   | 9.2/10.1              |                       | x86_64                |
   |                       | Standard 64bit        |                       |                       |                       |
   | (V100)                |                       |                       |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | P2v                   | Windows Server 2016   | 9.2/10.1              |                       | x86_64                |
   |                       | Standard 64bit        |                       |                       |                       |
   | (V100)                |                       |                       |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | P2v                   | Windows Server 2012   | 9.2/10.1              |                       | x86_64                |
   |                       | R2 Standard 64bit     |                       |                       |                       |
   | (V100)                |                       |                       |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+



.. _EN-US_TOPIC_0213874991__table15666175112518:

.. table:: **Table 4** Path in which the CUDA toolkit is downloaded for P2 ECSs

   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | ECS Type              | OS                    | CUDA Version          | How to Obtain         | CPU Architecture      |
   +=======================+=======================+=======================+=======================+=======================+
   | P2                    | Ubuntu Server 16.04   | 9                     | https://dev           | x86_64                |
   |                       | 64bit                 |                       | eloper.nvidia.com/cud |                       |
   | (V100)                |                       |                       | a-90-download-archive |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+



.. _EN-US_TOPIC_0213874991__table10558744163515:

.. table:: **Table 5** Path in which the CUDA toolkit is downloaded for P1 ECSs

   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | ECS Type              | OS                    | CUDA Version          | How to Obtain         | CPU Architecture      |
   +=======================+=======================+=======================+=======================+=======================+
   | P1                    | CentOS 7.3 64bit      | 9                     | https://dev           | x86_64                |
   |                       |                       |                       | eloper.nvidia.com/cud |                       |
   | (P100)                |                       |                       | a-90-download-archive |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | P1                    | Ubuntu 16.04 64bit    | 9                     |                       | x86_64                |
   |                       |                       |                       |                       |                       |
   | (P100)                |                       |                       |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | P1                    | Windows Server 2012   | 9                     |                       | x86_64                |
   |                       | R2 Standard 64bit     |                       |                       |                       |
   | (P100)                |                       |                       |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+



.. _EN-US_TOPIC_0213874991__table12527182514438:

.. table:: **Table 6** Path in which the CUDA toolkit is downloaded for PI2 ECSs

   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | ECS Type              | OS                    | CUDA Version          | How to Obtain         | CPU Architecture      |
   +=======================+=======================+=======================+=======================+=======================+
   | PI2                   | CentOS 7.8 64bit      | 10.1                  | https://developer.    | x86_64                |
   |                       |                       |                       | nvidia.com/cuda-10.1- |                       |
   | (T4)                  |                       |                       | download-archive-base |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | PI2                   | Ubuntu 16.04 64bit    | 10.1                  |                       | x86_64                |
   |                       |                       |                       |                       |                       |
   | (T4)                  |                       |                       |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | PI2                   | Windows Server 2019   | 10.1                  |                       | x86_64                |
   |                       | Standard 64bit        |                       |                       |                       |
   | (T4)                  |                       |                       |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | PI2                   | Windows Server 2016   | 10.1                  |                       | x86_64                |
   |                       | Standard 64bit        |                       |                       |                       |
   | (T4)                  |                       |                       |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | PI2                   | Windows Server 2012   | 10.1                  |                       | x86_64                |
   |                       | R2 Standard 64bit     |                       |                       |                       |
   | (T4)                  |                       |                       |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+



.. _EN-US_TOPIC_0213874991__table69013507215:

.. table:: **Table 7** Path in which the CUDA toolkit is downloaded for G6 ECSs

   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | ECS                   | OS                    | CUDA Version          | How to Obtain         | CPU Architecture      |
   |                       |                       |                       |                       |                       |
   | Type                  |                       |                       |                       |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
   | G6                    | Windows Server 2016   | 10.1                  | https://developer.    | x86_64                |
   |                       | Standard 64bit        |                       | nvidia.com/cuda-10.1- |                       |
   | (T4)                  |                       |                       | download-archive-base |                       |
   +-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+

