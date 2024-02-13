:original_name: en-us_topic_0213874991.html

.. _en-us_topic_0213874991:

Obtaining a Tesla Driver and CUDA Toolkit
=========================================

Scenarios
---------

Before using a GPU-accelerated ECS, make sure that the desired Tesla driver and CUDA toolkit have been installed on the ECS. Otherwise, computing acceleration will not take effect. This section describes how to obtain a Tesla driver and CUDA toolkit. Select a driver version based on your ECS type.

For instructions about how to install the Tesla driver and CUDA toolkit, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.

Downloading a Tesla Driver
--------------------------

`Download a driver <https://www.nvidia.com/Download/index.aspx?lang=en-us>`__ based on your ECS type.

.. table:: **Table 1** Mapping between Tesla drivers and ECS types

   ======== ====== ============== =======
   ECS Type Driver Product Series Product
   ======== ====== ============== =======
   P3       Tesla  A              A100
   P2s      Tesla  V              V100
   P2v      Tesla  V              V100
   P2       Tesla  V              V100
   P1       Tesla  P              P100
   Pi2      Tesla  T              T4
   G7       Tesla  A              A40
   G6       Tesla  T              T4
   ======== ====== ============== =======

.. _en-us_topic_0213874991__section10203125783920:

Downloading a CUDA Toolkit
--------------------------

Download the `CUDA software package <https://developer.nvidia.com/cuda-toolkit-archive>`__ and select the corresponding CUDA Toolkit software package based on the instance type and driver version.

.. note::

   `NVIDIA Driver Downloads <https://www.nvidia.com/Download/index.aspx?lang=en-us>`__ provides the mapping between the driver version and CUDA Toolkit. If the versions do not match, the driver may be unavailable.

The following uses Tesla T4 as an example to describe how to download the driver package and CUDA Toolkit.

#. Select the Linux operating system and the CUDA Toolkit 11.6 version.


   .. figure:: /_static/images/en-us_image_0000001411215958.png
      :alt: **Figure 1** Selecting the CUDA Toolkit version

      **Figure 1** Selecting the CUDA Toolkit version

#. Select a CUDA Toolkit 11.6 package to download.


   .. figure:: /_static/images/en-us_image_0000001461461773.png
      :alt: **Figure 2** Downloading a CUDA Toolkit 11.6 package

      **Figure 2** Downloading a CUDA Toolkit 11.6 package
