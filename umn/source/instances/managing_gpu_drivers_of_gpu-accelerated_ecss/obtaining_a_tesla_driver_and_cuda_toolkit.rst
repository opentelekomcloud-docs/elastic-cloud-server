:original_name: en-us_topic_0213874991.html

.. _en-us_topic_0213874991:

Obtaining a Tesla Driver and CUDA Toolkit
=========================================

Scenarios
---------

To enable compute acceleration on a GPU-accelerated ECS, you must install the Tesla driver and CUDA Toolkit. This section describes how to obtain a Tesla driver and CUDA Toolkit. Select a driver version based on your ECS series.

For instructions about how to install the Tesla driver and CUDA Toolkit, see :ref:`Manually Installing a Tesla Driver on a GPU-accelerated ECS <en-us_topic_0149470468>`.

Downloading a Tesla Driver
--------------------------

`Download a driver <https://www.nvidia.com/Download/index.aspx?lang=en-us>`__ based on your ECS series.

.. table:: **Table 1** ECS series and matched Tesla drivers

   ========== ====== ============== =======
   ECS Series Driver Product Series Product
   ========== ====== ============== =======
   P3         Tesla  A              A100
   P2s        Tesla  V              V100
   P2v        Tesla  V              V100
   Pi2        Tesla  T              T4
   G7         Tesla  A              A40
   G6         Tesla  T              T4
   ========== ====== ============== =======

Downloading a CUDA Toolkit
--------------------------

Download the `CUDA software package <https://developer.nvidia.com/cuda-toolkit-archive>`__ and select the corresponding CUDA Toolkit software package based on the ECS series and driver version.

.. note::

   Tesla driver versions must match their corresponding CUDA Toolkit versions. If the versions do not match, the driver may be unavailable.

   For version matching details, see `NVIDIA Driver Downloads <https://www.nvidia.com/Download/index.aspx?lang=en-us>`__.

The following uses Tesla T4 as an example to describe how to download the driver package and CUDA Toolkit.

#. Select the Linux operating system and the CUDA Toolkit 11.6 version.


   .. figure:: /_static/images/en-us_image_0000002150031409.png
      :alt: **Figure 1** Selecting the CUDA Toolkit version

      **Figure 1** Selecting the CUDA Toolkit version

#. Select your desired version and download the package.
