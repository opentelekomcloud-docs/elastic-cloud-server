GPU Driver
==========

Overview
--------

Before using a GPU-accelerated ECS, make sure that a GPU driver has been installed on the ECS for GPU acceleration.

GPU-accelerated ECSs support GRID and Tesla drivers.

-  To use graphics acceleration, such as OpenGL, DirectX, or Vulkan, install a GRID driver and separately purchase and configure a GRID license. The GRID driver with a vDWS license also supports CUDA for both computing and graphics acceleration.

   -  A graphics-accelerated (G series) ECS created using a Windows public image has had a GRID driver of a specified version installed by default, but the GRID license must be purchased and configured separately. Before using such an ECS, check whether the desired driver has been installed on it and whether the version of the installed driver meets service requirements.
   -  A graphics-accelerated (G series) ECS created using a Linux public image does not have a GRID driver installed by default. To install a GRID driver, see `Installing a GRID Driver on a GPU-accelerated ECS <en-us_topic_0149610914.html>`__.
   -  To install a GRID driver on a GPU-accelerated ECS created using a private image, see `Installing a GRID Driver on a GPU-accelerated ECS <en-us_topic_0149610914.html>`__.

-  To use computing acceleration, install a Tesla driver.

   -  A computing-accelerated (P series) ECS created using a Windows public image has had a Tesla driver of a specified version installed by default.
   -  A computing-accelerated (P series) ECS created using a Linux public image does not have a Tesla driver installed by default. To install a Tesla driver, see `Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468.html>`__.
   -  To install a Tesla driver on a GPU-accelerated ECS created using a private image, see `Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468.html>`__.



.. _EN-US_TOPIC_0234802636__table13621791684:

.. table:: **Table 1** Acceleration supported by GPU drivers

   +--------+--------------+-----------+--------------+--------------+--------------+--------------+--------------+
   | Driver | License      | CUDA      | OpenGL       | DirectX      | Vulkan       | Application  | Description  |
   |        |              |           |              |              |              | Scenario     |              |
   +========+==============+===========+==============+==============+==============+==============+==============+
   | GRID   | Required     | Supported | Supported    | Supported    | Supported    | 3D           | The GRID     |
   |        |              |           |              |              |              | rendering,   | driver must  |
   |        |              |           |              |              |              | graphics     | be paid and  |
   |        |              |           |              |              |              | workstation, | requires a   |
   |        |              |           |              |              |              | and game     | license to   |
   |        |              |           |              |              |              | acceleration | accelerate   |
   |        |              |           |              |              |              |              | graphics and |
   |        |              |           |              |              |              |              | image        |
   |        |              |           |              |              |              |              | a            |
   |        |              |           |              |              |              |              | pplications. |
   +--------+--------------+-----------+--------------+--------------+--------------+--------------+--------------+
   | Tesla  | Not required | Supported | Not          | Not          | Not          | Scientific   | The Tesla    |
   |        |              |           | supported    | supported    | supported    | computing,   | driver is    |
   |        |              |           |              |              |              | deep         | downloaded   |
   |        |              |           |              |              |              | learning     | free of      |
   |        |              |           |              |              |              | training,    | charge and   |
   |        |              |           |              |              |              | and          | usually used |
   |        |              |           |              |              |              | inference    | with NVIDIA  |
   |        |              |           |              |              |              |              | CUDA SDKs to |
   |        |              |           |              |              |              |              | accelerate   |
   |        |              |           |              |              |              |              | general      |
   |        |              |           |              |              |              |              | computing    |
   |        |              |           |              |              |              |              | a            |
   |        |              |           |              |              |              |              | pplications. |
   +--------+--------------+-----------+--------------+--------------+--------------+--------------+--------------+

