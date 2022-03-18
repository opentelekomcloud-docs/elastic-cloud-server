GPU Driver
==========

Overview
--------

Before using a GPU-accelerated ECS, make sure that a GPU driver has been installed on the ECS for GPU acceleration.

GPU-accelerated ECSs support GRID and Tesla drivers.

-  To use graphics acceleration, such as OpenGL, DirectX, or Vulkan, install a GRID driver and separately purchase and configure a GRID license. The GRID driver with a vDWS license also supports CUDA for both computing and graphics acceleration.

   -  A graphics-accelerated (G series) ECS created using a Windows public image has had a GRID driver of a specified version installed by default, but the GRID license must be purchased and configured separately. Before using such an ECS, check whether the desired driver has been installed on it and whether the version of the installed driver meets service requirements.
   -  A graphics-accelerated (G series) ECS created using a Linux public image does not have a GRID driver installed by default. To install a GRID driver, see `Installing a GRID Driver on a GPU-accelerated ECS <../../instances/optional_installing_a_driver_and_toolkit/installing_a_grid_driver_on_a_gpu-accelerated_ecs.html>`__.
   -  To install a GRID driver on a GPU-accelerated ECS created using a private image, see `Installing a GRID Driver on a GPU-accelerated ECS <../../instances/optional_installing_a_driver_and_toolkit/installing_a_grid_driver_on_a_gpu-accelerated_ecs.html>`__.

-  To use computing acceleration, install a Tesla driver.

   -  A computing-accelerated (P series) ECS created using a Windows public image has had a Tesla driver of a specified version installed by default.
   -  A computing-accelerated (P series) ECS created using a Linux public image does not have a Tesla driver installed by default. To install a Tesla driver, see `Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <../../instances/optional_installing_a_driver_and_toolkit/installing_a_tesla_driver_and_cuda_toolkit_on_a_gpu-accelerated_ecs.html>`__.
   -  To install a Tesla driver on a GPU-accelerated ECS created using a private image, see `Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <../../instances/optional_installing_a_driver_and_toolkit/installing_a_tesla_driver_and_cuda_toolkit_on_a_gpu-accelerated_ecs.html>`__.



.. _ENUSTOPIC0234802636table13621791684:

.. table:: **Table 1** Acceleration supported by GPU drivers

   +--------+--------------+-----------+---------------+---------------+---------------+-------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | Driver | License      | CUDA      | OpenGL        | DirectX       | Vulkan        | Application Scenario                                        | Description                                                                                                                        |
   +========+==============+===========+===============+===============+===============+=============================================================+====================================================================================================================================+
   | GRID   | Required     | Supported | Supported     | Supported     | Supported     | 3D rendering, graphics workstation, and game acceleration   | The GRID driver must be paid and requires a license to accelerate graphics and image applications.                                 |
   +--------+--------------+-----------+---------------+---------------+---------------+-------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | Tesla  | Not required | Supported | Not supported | Not supported | Not supported | Scientific computing, deep learning training, and inference | The Tesla driver is downloaded free of charge and usually used with NVIDIA CUDA SDKs to accelerate general computing applications. |
   +--------+--------------+-----------+---------------+---------------+---------------+-------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------+


