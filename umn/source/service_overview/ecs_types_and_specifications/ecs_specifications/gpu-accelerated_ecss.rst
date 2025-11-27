:original_name: en-us_topic_0097289624.html

.. _en-us_topic_0097289624:

GPU-accelerated ECSs
====================

GPU-accelerated ECSs provide outstanding floating-point computing capabilities. They are suitable for applications that require real-time, highly concurrent massive computing.

GPU-accelerated ECSs are classified as G series and P series of ECSs.

-  G series: Graphics-accelerated ECSs, which are suitable for 3D animation rendering and CAD
-  P series: Computing-accelerated or inference-accelerated ECSs, which are suitable for deep learning, scientific computing, and CAE


GPU-accelerated ECSs
--------------------

Recommended: :ref:`Computing-accelerated P2s <en-us_topic_0097289624__section1454714546567>`, :ref:`Inference-accelerated Pi2 <en-us_topic_0097289624__section1846114713182>`, and :ref:`Graphics-accelerated Enhancement G6 <en-us_topic_0097289624__section131302034104515>`

Available now: All GPU models except the recommended ones. If available ECSs are sold out, use the recommended ones.

-  G series

   -  :ref:`Graphics-accelerated Enhancement G7v <en-us_topic_0097289624__section168054357432>`
   -  :ref:`Graphics-accelerated Enhancement G7 <en-us_topic_0097289624__section2325028104711>`
   -  :ref:`Graphics-accelerated Enhancement G6 <en-us_topic_0097289624__section131302034104515>`

-  P series

   -  :ref:`Computing-accelerated P5s <en-us_topic_0097289624__section453311473114>`
   -  :ref:`Computing-accelerated P3 <en-us_topic_0097289624__section48861652193>`
   -  :ref:`Computing-accelerated P2s <en-us_topic_0097289624__section1454714546567>` (recommended)
   -  :ref:`Computing-accelerated P2v <en-us_topic_0097289624__section208472383415>`
   -  :ref:`Inference-accelerated Pi5e <en-us_topic_0097289624__section3135224614>`
   -  :ref:`Inference-accelerated Pi2 <en-us_topic_0097289624__section1846114713182>` (recommended)

Helpful links:

-  :ref:`Manually Installing a GRID Driver on a GPU-accelerated ECS <en-us_topic_0149610914>`
-  :ref:`Manually Installing a Tesla Driver on a GPU-accelerated ECS <en-us_topic_0149470468>`

Images Supported by GPU-accelerated ECSs
----------------------------------------

.. table:: **Table 1** Images supported by GPU-accelerated ECSs

   +-----------------------+-----------------------+------------------------------------------+
   | Type                  | Series                | Supported Image                          |
   +=======================+=======================+==========================================+
   | Graphics-accelerated  | G7v                   | -  CentOS 8.2 64bit                      |
   |                       |                       | -  CentOS 7.6 64bit                      |
   |                       |                       | -  Ubuntu 20.04 server 64bit             |
   |                       |                       | -  Ubuntu 18.04 server 64bit             |
   |                       |                       | -  Windows Server 2019 Standard 64bit    |
   |                       |                       | -  Windows Server 2016 Standard 64bit    |
   +-----------------------+-----------------------+------------------------------------------+
   | Graphics-accelerated  | G7                    | -  CentOS 8.2 64bit                      |
   |                       |                       | -  CentOS 7.6 64bit                      |
   |                       |                       | -  Ubuntu 20.04 server 64bit             |
   |                       |                       | -  Ubuntu 18.04 server 64bit             |
   |                       |                       | -  Windows Server 2019 Standard 64bit    |
   |                       |                       | -  Windows Server 2016 Standard 64bit    |
   +-----------------------+-----------------------+------------------------------------------+
   | Graphics-accelerated  | G6                    | -  EulerOS 2.5 64bit                     |
   |                       |                       | -  Windows Server 2019 Standard 64bit    |
   |                       |                       | -  Windows Server 2016 Standard 64bit    |
   |                       |                       | -  Windows Server 2012 R2 Standard 64bit |
   +-----------------------+-----------------------+------------------------------------------+
   | Computing-accelerated | P5s                   | -  CentOS 7.9 64bit                      |
   |                       |                       | -  CentOS 7.8 64bit                      |
   |                       |                       | -  CentOS 7.7 64bit                      |
   |                       |                       | -  CentOS 7.6 64bit                      |
   |                       |                       | -  Ubuntu 22.04 64bit                    |
   |                       |                       | -  Ubuntu 20.04 64bit                    |
   |                       |                       | -  Ubuntu 18.04 64bit                    |
   |                       |                       | -  Ubuntu 16.04 64bit                    |
   +-----------------------+-----------------------+------------------------------------------+
   | Computing-accelerated | P3                    | -  CentOS 8.2 64bit                      |
   |                       |                       | -  CentOS 8.1 64bit                      |
   |                       |                       | -  CentOS 8.0 64bit                      |
   |                       |                       | -  CentOS 7.9 64bit                      |
   |                       |                       | -  CentOS 7.8 64bit                      |
   |                       |                       | -  CentOS 7.7 64bit                      |
   |                       |                       | -  CentOS 7.6 64bit                      |
   |                       |                       | -  Ubuntu 20.04 server 64bit             |
   |                       |                       | -  Ubuntu 18.04 server 64bit             |
   +-----------------------+-----------------------+------------------------------------------+
   | Computing-accelerated | P2s                   | -  CentOS 7.9 64bit                      |
   |                       |                       | -  EulerOS 2.5 64bit                     |
   |                       |                       | -  Oracle Linux Server release 7.6 64bit |
   |                       |                       | -  Ubuntu 20.04 server 64bit             |
   |                       |                       | -  Ubuntu 18.04 server 64bit             |
   |                       |                       | -  Windows Server 2019 Standard 64bit    |
   |                       |                       | -  Windows Server 2016 Standard 64bit    |
   |                       |                       | -  Windows Server 2012 R2 Standard 64bit |
   +-----------------------+-----------------------+------------------------------------------+
   | Computing-accelerated | P2v                   | -  CentOS 7.9 64bit                      |
   |                       |                       | -  EulerOS 2.5 64bit                     |
   |                       |                       | -  Oracle Linux Server release 7.6 64bit |
   |                       |                       | -  Ubuntu 20.04 server 64bit             |
   |                       |                       | -  Ubuntu 18.04 server 64bit             |
   |                       |                       | -  Windows Server 2019 Standard 64bit    |
   |                       |                       | -  Windows Server 2016 Standard 64bit    |
   |                       |                       | -  Windows Server 2012 R2 Standard 64bit |
   +-----------------------+-----------------------+------------------------------------------+
   | Inference-accelerated | Pi5e                  | -  Ubuntu 24.04 server 64bit             |
   |                       |                       | -  Windows Server 2025 Standard 64bit    |
   |                       |                       | -  Windows Server 2022 Standard 64bit    |
   |                       |                       | -  Windows Server 2019 Standard 64bit    |
   +-----------------------+-----------------------+------------------------------------------+
   | Inference-accelerated | Pi2                   | -  CentOS 7.9 64bit                      |
   |                       |                       | -  Oracle Linux Server release 7.6 64bit |
   |                       |                       | -  Ubuntu 20.04 server 64bit             |
   |                       |                       | -  Ubuntu 18.04 server 64bit             |
   |                       |                       | -  Windows Server 2019 Standard 64bit    |
   |                       |                       | -  Windows Server 2016 Standard 64bit    |
   |                       |                       | -  Windows Server 2012 R2 Standard 64bit |
   +-----------------------+-----------------------+------------------------------------------+

.. _en-us_topic_0097289624__section168054357432:

Graphics-accelerated Enhancement G7v
------------------------------------

**Overview**

G7v ECSs use NVIDIA A40 GPUs and support DirectX, Shader Model, OpenGL, and Vulkan. Each GPU provides 48 GiB of GPU memory. Theoretically, the peak FP32 is 37.4 TFLOPS and the peak TF32 tensor is 74.8 TFLOPS \| 149.6 TFLOPS (sparsity enabled). They deliver two times the rendering performance and 1.4 times the graphics processing performance of RTX6000 GPUs to meet professional graphics processing requirements.

Select your desired GPU-accelerated ECS type and specifications.

**Specifications**

.. table:: **Table 2** G7v ECS specifications

   +---------------+-------+--------+--------------------------------+------------------+-----------------+-----------+--------------------+------------+----------------+
   | Flavor        | vCPUs | Memory | Max./Assured Network Bandwidth | Max. Network PPS | Max. NIC Queues | Max. NICs | GPUs               | GPU Memory | Virtualization |
   |               |       |        |                                |                  |                 |           |                    |            |                |
   |               |       | (GiB)  | (Gbit/s)                       | (10,000)         |                 |           |                    | (GiB)      |                |
   +===============+=======+========+================================+==================+=================+===========+====================+============+================+
   | g7v.2xlarge.8 | 8     | 64     | 15/3                           | 100              | 4               | 4         | 1 x NVIDIA-A40-8Q  | 8          | KVM            |
   +---------------+-------+--------+--------------------------------+------------------+-----------------+-----------+--------------------+------------+----------------+
   | g7v.4xlarge.8 | 16    | 128    | 20/6                           | 150              | 8               | 8         | 1 x NVIDIA-A40-16Q | 16         | KVM            |
   +---------------+-------+--------+--------------------------------+------------------+-----------------+-----------+--------------------+------------+----------------+
   | g7v.6xlarge.8 | 24    | 192    | 25/9                           | 200              | 8               | 8         | 1 x NVIDIA-A40-24Q | 24         | KVM            |
   +---------------+-------+--------+--------------------------------+------------------+-----------------+-----------+--------------------+------------+----------------+

**G7v ECS Features**

-  CPU: 3rd Generation Intel® Xeon® Scalable 6348 processors (3.0 GHz of basic frequency and 3.5 GHz of turbo frequency)
-  Graphics acceleration APIs

   -  DirectX 12.07, Direct2D, DirectX Video Acceleration (DXVA)
   -  Shader Model 5.17
   -  OpenGL 4.68
   -  Vulkan 1.18

-  CUDA, DirectCompute, OpenACC, and OpenCL
-  A single card is equipped with 10,752 CUDA cores, 84 second-generation RT cores, and 336 third-generation Tensor cores.
-  Graphics applications accelerated
-  Heavy-load CPU inference
-  Application flow identical to common ECSs
-  Automatic scheduling of G7v ECSs to AZs where NVIDIA A40 GPUs are used
-  One NVENC (encoding) engine and two NVDEC (decoding) engines (including AV1 decoding) embedded

**Supported Common Software**

G7v ECSs are used in graphics acceleration scenarios, such as video rendering, cloud desktop, and 3D visualization. If the software relies on GPU DirectX and OpenGL hardware acceleration, use G7v ECSs. G7v ECSs support the following commonly used graphics processing software:

-  AutoCAD
-  3ds Max
-  MAYA
-  Agisoft PhotoScan
-  ContextCapture
-  Adobe Premiere Pro
-  Solidworks
-  Unreal Engine
-  Blender
-  Vray

**Notes**

-  After a G7v ECS is stopped, basic resources (including vCPUs, memory, image, and GPUs) are not billed, but its system disk is billed based on the disk capacity. If other products, such as EVS disks, EIP, and bandwidth are associated with the ECS, these products are billed separately.

   .. note::

      Resources will be released after a G7v ECS is stopped. If resources are insufficient at the next start, the start may fail. If you want to use such an ECS for a long period of time, do not stop the ECS.

-  G7v ECSs created using a public image have had the GRID driver of a specific version installed by default. However, you need to purchase and configure a GRID license by yourself. Ensure that the GRID driver version meets service requirements.

   For details about how to configure a GRID license, see :ref:`Manually Installing a GRID Driver on a GPU-accelerated ECS <en-us_topic_0149610914>`.

-  If a G7v ECS is created using a private image, make sure that the GRID driver was installed during the private image creation. If the GRID driver has not been installed, install the driver for graphics acceleration after the ECS is created.

   For details, see :ref:`Manually Installing a GRID Driver on a GPU-accelerated ECS <en-us_topic_0149610914>`.

-  GPU-accelerated ECSs differ greatly in general-purpose and heterogeneous computing power. Their specifications can only be changed to other specifications of the same instance type.

-  GPU-accelerated ECSs do not support live migration.

.. _en-us_topic_0097289624__section2325028104711:

Graphics-accelerated Enhancement G7
-----------------------------------

**Overview**

G7 ECSs use NVIDIA A40 GPUs and support DirectX, Shader Model, OpenGL, and Vulkan. Each GPU provides 48 GiB of GPU memory. Theoretically, the peak FP32 is 37.4 TFLOPS and the peak TF32 tensor is 74.8 TFLOPS \| 149.6 TFLOPS (sparsity enabled). They deliver two times the rendering performance and 1.4 times the graphics processing performance of RTX6000 GPUs to meet professional graphics processing requirements.

Select your desired GPU-accelerated ECS type and specifications.

**Specifications**

.. table:: **Table 3** G7 ECS specifications

   +---------------+-------+--------+--------------------------------+------------------+-----------------+-----------+----------------+------------+----------------+
   | Flavor        | vCPUs | Memory | Max./Assured Network Bandwidth | Max. Network PPS | Max. NIC Queues | Max. NICs | GPUs           | GPU Memory | Virtualization |
   |               |       |        |                                |                  |                 |           |                |            |                |
   |               |       | (GiB)  | (Gbit/s)                       | (10,000)         |                 |           |                | (GiB)      |                |
   +===============+=======+========+================================+==================+=================+===========+================+============+================+
   | g7.12xlarge.8 | 48    | 384    | 35/18                          | 750              | 16              | 8         | 1 x NVIDIA-A40 | 1 x 48     | KVM            |
   +---------------+-------+--------+--------------------------------+------------------+-----------------+-----------+----------------+------------+----------------+
   | g7.24xlarge.8 | 96    | 768    | 40/36                          | 850              | 16              | 8         | 2 x NVIDIA-A40 | 2 x 48     | KVM            |
   +---------------+-------+--------+--------------------------------+------------------+-----------------+-----------+----------------+------------+----------------+

**G7 ECS Features**

-  CPU: 3rd Generation Intel® Xeon® Scalable 8378A processors (3.0 GHz of basic frequency and 3.5 GHz of turbo frequency)
-  Graphics acceleration APIs

   -  DirectX 12.07, Direct2D, DirectX Video Acceleration (DXVA)
   -  Shader Model 5.17
   -  OpenGL 4.68
   -  Vulkan 1.18

-  CUDA, DirectCompute, OpenACC, and OpenCL
-  A single card is equipped with 10,752 CUDA cores, 84 second-generation RT cores, and 336 third-generation Tensor cores.
-  Graphics applications accelerated
-  Heavy-load CPU inference
-  Application flow identical to common ECSs
-  Automatic scheduling of G7 ECSs to AZs where NVIDIA A40 GPUs are used
-  One NVENC (encoding) engine and two NVDEC (decoding) engines (including AV1 decoding) embedded

**Supported Common Software**

G7 ECSs are used in graphics acceleration scenarios, such as video rendering, cloud desktop, and 3D visualization. If the software relies on GPU DirectX and OpenGL hardware acceleration, use G7 ECSs. G7 ECSs support the following commonly used graphics processing software:

-  AutoCAD
-  3ds Max
-  MAYA
-  Agisoft PhotoScan
-  ContextCapture
-  Adobe Premiere Pro
-  Solidworks
-  Unreal Engine
-  Blender
-  Vray

**Notes**

-  After a G7 ECS is stopped, basic resources (including vCPUs, memory, image, and GPUs) are not billed, but its system disk is billed based on the disk capacity. If other products, such as EVS disks, EIP, and bandwidth are associated with the ECS, these products are billed separately.

   .. note::

      Resources will be released after a G7 ECS is stopped. If resources are insufficient at the next start, the start may fail. If you want to use such an ECS for a long period of time, do not stop the ECS.

-  G7 ECSs created using a public image have had the GRID driver of a specific version installed by default. However, you need to purchase and configure a GRID license by yourself. Ensure that the GRID driver version meets service requirements.
-  If a G7 ECS is created using a private image, make sure that the GRID driver was installed during the private image creation. If the GRID driver has not been installed, install the driver for graphics acceleration after the ECS is created.
-  GPU-accelerated ECSs differ greatly in general-purpose and heterogeneous compute. Their specifications can only be changed to other specifications of the same instance type.
-  GPU-accelerated ECSs do not support live migration.

.. _en-us_topic_0097289624__section131302034104515:

Graphics-accelerated Enhancement G6
-----------------------------------

**Overview**

G6 ECSs use NVIDIA Tesla T4 GPUs to support DirectX, OpenGL, and Vulkan and provide 16 GiB of GPU memory. The theoretical Pixel rate is 101.8 Gpixel/s and Texture rate 254.4 GTexel/s, meeting professional graphics processing requirements.

Select your desired GPU-accelerated ECS type and specifications.

**Specifications**

.. table:: **Table 4** G6 ECS specifications

   +---------------+-------+--------+--------------------------------+------------------+-----------------+-----------+--------+------------+----------------+
   | Flavor        | vCPUs | Memory | Max./Assured Network Bandwidth | Max. Network PPS | Max. NIC Queues | Max. NICs | GPUs   | GPU Memory | Virtualization |
   |               |       |        |                                |                  |                 |           |        |            |                |
   |               |       | (GiB)  | (Gbit/s)                       | (10,000)         |                 |           |        | (GiB)      |                |
   +===============+=======+========+================================+==================+=================+===========+========+============+================+
   | g6.4xlarge.4  | 16    | 64     | 25/15                          | 200              | 8               | 8         | 1 x T4 | 16         | KVM            |
   +---------------+-------+--------+--------------------------------+------------------+-----------------+-----------+--------+------------+----------------+
   | g6.10xlarge.7 | 40    | 280    | 25/15                          | 200              | 16              | 8         | 1 x T4 | 16         | KVM            |
   +---------------+-------+--------+--------------------------------+------------------+-----------------+-----------+--------+------------+----------------+
   | g6.20xlarge.7 | 80    | 560    | 30/30                          | 400              | 32              | 16        | 2 x T4 | 32         | KVM            |
   +---------------+-------+--------+--------------------------------+------------------+-----------------+-----------+--------+------------+----------------+

.. note::

   A G6.10xlarge.7 ECS exclusively uses a T4 GPU for professional graphics acceleration. Such an ECS can be used for heavy-load CPU inference.

**G6 ECS Features**

-  CPU: 2nd Generation Intel® Xeon® Scalable 6266 processors (3.0 GHz of basic frequency and 3.4 GHz of turbo frequency)
-  Graphics acceleration APIs

   -  DirectX 12, Direct2D, and DirectX Video Acceleration (DXVA)
   -  OpenGL 4.5
   -  Vulkan 1.0

-  CUDA and OpenCL
-  NVIDIA T4 GPUs
-  Graphics applications accelerated
-  Heavy-load CPU inference
-  Automatic scheduling of G6 ECSs to AZs where NVIDIA T4 GPUs are used
-  One NVENC engine and two NVDEC engines embedded

**Supported Common Software**

G6 ECSs are used in graphics acceleration scenarios, such as video rendering, cloud desktop, and 3D visualization. If the software relies on GPU DirectX and OpenGL hardware acceleration, use G6 ECSs. G6 ECSs support the following commonly used graphics processing software:

-  AutoCAD
-  3ds Max
-  MAYA
-  Agisoft PhotoScan
-  ContextCapture

**Notes**

-  After a G6 ECS is stopped, basic resources (including vCPUs, memory, image, and GPUs) are not billed, but its system disk is billed based on the disk capacity. If other products, such as EVS disks, EIP, and bandwidth are associated with the ECS, these products are billed separately.

   .. note::

      Resources will be released after a G6 ECS is stopped. If resources are insufficient at the next start, the start may fail. If you want to use such an ECS for a long period of time, do not stop the ECS.

-  G6 ECSs created using a public image have had the GRID driver of a specific version installed by default. However, you need to purchase and configure a GRID license by yourself. Ensure that the GRID driver version meets service requirements.

-  If a G6 ECS is created using a private image, make sure that the GRID driver was installed during the private image creation. If not, install the driver for graphics acceleration after the ECS is created.

-  GPU-accelerated ECSs differ greatly in general-purpose and heterogeneous compute. Their specifications can only be changed to other specifications of the same instance type.

-  GPU-accelerated ECSs do not support live migration.

.. _en-us_topic_0097289624__section453311473114:

Computing-accelerated P5s
-------------------------

**Overview**

P5s ECSs use high-performance NVIDIA Tesla H100 PCIe to provide outstanding real-time inference.

**Specifications**

.. table:: **Table 5** P5s ECS specifications

   +-----------------+-------+--------------+-----------------------------------------+---------------------------+-----------------+-----------+----------------+------------------+----------------+
   | Flavor          | vCPUs | Memory (GiB) | Max./Assured Network Bandwidth (Gbit/s) | Max. Network PPS (10,000) | Max. NIC Queues | Max. NICs | GPUs           | GPU Memory (GiB) | Virtualization |
   +=================+=======+==============+=========================================+===========================+=================+===========+================+==================+================+
   | p5s.5xlarge.12  | 20    | 240          | 16/4.5                                  | 280                       | 8               | 4         | 1 \* H100 PCIe | 80               | KVM            |
   +-----------------+-------+--------------+-----------------------------------------+---------------------------+-----------------+-----------+----------------+------------------+----------------+
   | p5s.10xlarge.12 | 40    | 480          | 24/9                                    | 550                       | 16              | 8         | 2 \* H100 PCIe | 160              | KVM            |
   +-----------------+-------+--------------+-----------------------------------------+---------------------------+-----------------+-----------+----------------+------------------+----------------+
   | p5s.20xlarge.12 | 80    | 960          | 32/18                                   | 750                       | 32              | 8         | 4 \* H100 PCIe | 320              | KVM            |
   +-----------------+-------+--------------+-----------------------------------------+---------------------------+-----------------+-----------+----------------+------------------+----------------+
   | p5s.40xlarge.12 | 160   | 1920         | 40/36                                   | 850                       | 32              | 8         | 8 \* H100 PCIe | 640              | KVM            |
   +-----------------+-------+--------------+-----------------------------------------+---------------------------+-----------------+-----------+----------------+------------------+----------------+

**P5s ECS Features**

-  1:12 ratio of vCPUs to memory
-  CPU: 4th Generation Intel® Xeon® Scalable 8458P processors (2.7 GHz of basic frequency and 3.8 GHz of turbo frequency)
-  Each GPU provides 80 GiB of GPU memory and 3,026 TFLOPS INT8 compute.
-  The GPU memory bandwidth can reach up to 2,000 GB/s.

**Supported Common Software**

P5s ECSs are used in computing acceleration scenarios, such as deep learning training, inference, scientific computing, molecular modeling, and seismic analysis. If the software is required to support GPU CUDA, use P5s ECSs. The following commonly used software is supported:

-  Common deep learning frameworks, such as TensorFlow, Spark, PyTorch, MXNet, and Caffe
-  CUDA GPU rendering supported by RedShift for Autodesk 3ds Max and V-Ray for 3ds Max
-  Agisoft PhotoScan
-  MapD
-  More than 2,000 GPU-accelerated applications such as Amber, NAMD, and VASP

**Notes**

-  P5s ECSs support automatic recovery when the hosts accommodating such ECSs become faulty.
-  After a P5s ECS is stopped, basic resources (vCPUs, memory, image, and encoding cards) are not billed, but its system disk is billed based on the disk capacity. If other service resources, such as EVS disks, EIPs, and bandwidth are associated with the ECS, these resources are billed separately.
-  Specifications of P5s ECSs can only be changed to other specifications of the same instance type.
-  If you have attached a data disk to a P5s ECS during ECS creation, do not detach the data disk upon creation, or the detachment will fail.

.. _en-us_topic_0097289624__section48861652193:

Computing-accelerated P3
------------------------

**Overview**

P3 ECSs use NVIDIA A100 GPUs and provide flexibility and ultra-high-performance computing. P3 ECSs have strengths in AI-based deep learning, scientific computing, Computational Fluid Dynamics (CFD), computing finance, seismic analysis, molecular modeling, and genomics. Theoretically, the FP32 is 19.5 TFLOPS, and the TF32 tensor core is 156 TFLOPS \| 312 TFLOPS (sparsity enabled).

**Specifications**

.. table:: **Table 6** P3 ECS specifications

   +---------------+-------+--------+-----------------------------------------+------------------+-----------------+-----------+-----------------------+------------+----------------+
   | Flavor        | vCPUs | Memory | Max./Assured Network Bandwidth (Gbit/s) | Max. Network PPS | Max. NIC Queues | Max. NICs | GPUs                  | GPU Memory | Virtualization |
   |               |       |        |                                         |                  |                 |           |                       |            |                |
   |               |       | (GiB)  |                                         | (10,000)         |                 |           |                       | (GiB)      |                |
   +===============+=======+========+=========================================+==================+=================+===========+=======================+============+================+
   | p3.2xlarge.8  | 8     | 64     | 10/4                                    | 100              | 4               | 4         | 1 x NVIDIA A100 80 GB | 80         | KVM            |
   +---------------+-------+--------+-----------------------------------------+------------------+-----------------+-----------+-----------------------+------------+----------------+
   | p3.4xlarge.8  | 16    | 128    | 15/8                                    | 200              | 8               | 8         | 2 x NVIDIA A100 80 GB | 160        | KVM            |
   +---------------+-------+--------+-----------------------------------------+------------------+-----------------+-----------+-----------------------+------------+----------------+
   | p3.8xlarge.8  | 32    | 256    | 25/15                                   | 350              | 16              | 8         | 4 x NVIDIA A100 80 GB | 320        | KVM            |
   +---------------+-------+--------+-----------------------------------------+------------------+-----------------+-----------+-----------------------+------------+----------------+
   | p3.16xlarge.8 | 64    | 512    | 36/30                                   | 700              | 32              | 8         | 8 x NVIDIA A100 80 GB | 640        | KVM            |
   +---------------+-------+--------+-----------------------------------------+------------------+-----------------+-----------+-----------------------+------------+----------------+

**P3 ECS Features**

-  CPU: 2nd Generation Intel® Xeon® Scalable 6248R processors and 3.0 GHz of basic frequency

-  Up to eight NVIDIA A100 GPUs on an ECS

-  NVIDIA CUDA parallel computing and common deep learning frameworks, such as TensorFlow, Caffe, PyTorch, and MXNet

-  19.5 TFLOPS of single-precision computing and 9.7 TFLOPS of double-precision computing on a single GPU

-  NVIDIA Tensor cores with 156 TFLOPS of single- and double-precision computing for deep learning

-  Up to 40 Gbit/s of network bandwidth on a single ECS

-  80 GB HBM2 GPU memory per graphics card, with a bandwidth of 1,935 Gbit/s

-  Comprehensive basic capabilities

   -  User-defined network with flexible subnet division and network access policy configuration
   -  Mass storage, elastic expansion, and backup and restoration
   -  Elastic scaling

-  Flexibility

   Similar to other types of ECSs, P3 ECSs can be provisioned in a few minutes.

-  Excellent supercomputing ecosystem

   The supercomputing ecosystem allows you to build up a flexible, high-performance, cost-effective computing platform. A large number of HPC applications and deep-learning frameworks can run on P3 ECSs.

**Supported Common Software**

P3 ECSs are used in computing acceleration scenarios, such as deep learning training, inference, scientific computing, molecular modeling, and seismic analysis. If the software is required to support GPU CUDA, use P3 ECSs. P3 ECSs support the following commonly used software:

-  Common deep learning frameworks, such as TensorFlow, Spark, PyTorch, MXNet, and Caffe
-  CUDA GPU rendering supported by RedShift for Autodesk 3ds Max and V-Ray for 3ds Max
-  Agisoft PhotoScan
-  MapD
-  More than 2,000 GPU-accelerated applications such as Amber, NAMD, and VASP

**Notes**

-  After a P3 ECS is stopped, basic resources (including vCPUs, memory, image, and GPUs) are not billed, but its system disk is billed based on the disk capacity. If other products, such as EVS disks, EIP, and bandwidth are associated with the ECS, these products are billed separately.

   .. note::

      Resources will be released after a P3 ECS is stopped. If resources are insufficient at the next start, the start may fail. If you want to use such an ECS for a long period of time, do not stop it.

-  If a P3 ECS is created using a private image, make sure that the Tesla driver was installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Manually Installing a Tesla Driver on a GPU-accelerated ECS <en-us_topic_0149470468>`.
-  GPU-accelerated ECSs differ greatly in general-purpose and heterogeneous computing power. Their specifications can only be changed to other specifications of the same instance type.
-  GPU-accelerated ECSs do not support live migration.

.. _en-us_topic_0097289624__section1454714546567:

Computing-accelerated P2s
-------------------------

**Overview**

P2s ECSs use NVIDIA Tesla V100 GPUs to provide flexibility, high-performance computing, and cost-effectiveness. P2s ECSs provide outstanding general computing capabilities and have strengths in AI-based deep learning, scientific computing, Computational Fluid Dynamics (CFD), computing finance, seismic analysis, molecular modeling, and genomics.

**Specifications**

.. table:: **Table 7** P2s ECS specifications

   +----------------+-------+--------+-----------------------------------------+---------------------------+-----------------+-----------+----------+----------------+------------------+----------------+----------------------------------------------------------+
   | Flavor         | vCPUs | Memory | Max./Assured Network Bandwidth (Gbit/s) | Max. Network PPS (10,000) | Max. NIC Queues | Max. NICs | GPUs     | GPU Connection | GPU Memory (GiB) | Virtualization | Hardware                                                 |
   |                |       |        |                                         |                           |                 |           |          |                |                  |                |                                                          |
   |                |       | (GiB)  |                                         |                           |                 |           |          |                |                  |                |                                                          |
   +================+=======+========+=========================================+===========================+=================+===========+==========+================+==================+================+==========================================================+
   | p2s.2xlarge.8  | 8     | 64     | 10/4                                    | 50                        | 4               | 4         | 1 x V100 | PCIe Gen3      | 1 x 32 GiB       | KVM            | CPU: 2nd Generation Intel® Xeon® Scalable Processor 6278 |
   +----------------+-------+--------+-----------------------------------------+---------------------------+-----------------+-----------+----------+----------------+------------------+----------------+----------------------------------------------------------+
   | p2s.4xlarge.8  | 16    | 128    | 15/8                                    | 100                       | 8               | 8         | 2 x V100 | PCIe Gen3      | 2 x 32 GiB       | KVM            |                                                          |
   +----------------+-------+--------+-----------------------------------------+---------------------------+-----------------+-----------+----------+----------------+------------------+----------------+----------------------------------------------------------+
   | p2s.8xlarge.8  | 32    | 256    | 25/15                                   | 200                       | 16              | 8         | 4 x V100 | PCIe Gen3      | 4 x 32 GiB       | KVM            |                                                          |
   +----------------+-------+--------+-----------------------------------------+---------------------------+-----------------+-----------+----------+----------------+------------------+----------------+----------------------------------------------------------+
   | p2s.16xlarge.8 | 64    | 512    | 30/30                                   | 400                       | 32              | 8         | 8 x V100 | PCIe Gen3      | 8 x 32 GiB       | KVM            |                                                          |
   +----------------+-------+--------+-----------------------------------------+---------------------------+-----------------+-----------+----------+----------------+------------------+----------------+----------------------------------------------------------+

**P2s ECS Features**

-  CPU: 2nd Generation Intel® Xeon® Scalable 6278 processors (2.6 GHz of basic frequency and 3.5 GHz of turbo frequency), or Intel® Xeon® Scalable 6151 processors (3.0 GHz of basic frequency and 3.4 GHz of turbo frequency)

-  Up to eight NVIDIA Tesla V100 GPUs on an ECS

-  NVIDIA CUDA parallel computing and common deep learning frameworks, such as TensorFlow, Caffe, PyTorch, and MXNet

-  14 TFLOPS of single-precision computing and 7 TFLOPS of double-precision computing

-  NVIDIA Tensor cores with 112 TFLOPS of single- and double-precision computing for deep learning

-  Up to 30 Gbit/s of network bandwidth on a single ECS

-  32 GiB of HBM2 GPU memory with a bandwidth of 900 Gbit/s

-  Comprehensive basic capabilities

   -  User-defined network with flexible subnet division and network access policy configuration
   -  Mass storage, elastic expansion, and backup and restoration
   -  Elastic scaling

-  Flexibility

   Similar to other types of ECSs, P2s ECSs can be provisioned in a few minutes.

-  Excellent supercomputing ecosystem

   The supercomputing ecosystem allows you to build up a flexible, high-performance, cost-effective computing platform. A large number of HPC applications and deep-learning frameworks can run on P2s ECSs.

**Supported Common Software**

P2s ECSs are used in computing acceleration scenarios, such as deep learning training, inference, scientific computing, molecular modeling, and seismic analysis. If the software is required to support GPU CUDA, use P2s ECSs. P2s ECSs support the following commonly used software:

-  Common deep learning frameworks, such as TensorFlow, Caffe, PyTorch, and MXNet
-  CUDA GPU rendering supported by RedShift for Autodesk 3ds Max and V-Ray for 3ds Max
-  Agisoft PhotoScan
-  MapD

**Notes**

-  After a P2s ECS is stopped, basic resources (including vCPUs, memory, image, and GPUs) are not billed, but its system disk is billed based on the disk capacity. If other products, such as EVS disks, EIP, and bandwidth are associated with the ECS, these products are billed separately.

   .. note::

      Resources will be released after a P2s ECS is stopped. If resources are insufficient at the next start, the start may fail. If you want to use such an ECS for a long period of time, do not stop the ECS.

-  By default, P2s ECSs created using a Windows public image have the Tesla driver installed.
-  If a P2s ECS is created using a private image, make sure that the Tesla driver was installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Manually Installing a Tesla Driver on a GPU-accelerated ECS <en-us_topic_0149470468>`.
-  GPU-accelerated ECSs differ greatly in general-purpose and heterogeneous computing power. Their specifications can only be changed to other specifications of the same instance type.
-  GPU-accelerated ECSs do not support live migration.

.. _en-us_topic_0097289624__section208472383415:

Computing-accelerated P2v
-------------------------

**Overview**

P2v ECSs use NVIDIA Tesla V100 GPUs and deliver high flexibility, high-performance computing, and high cost-effectiveness. These ECSs use GPU NVLink for direct communication between GPUs, improving data transmission efficiency. P2v ECSs provide outstanding general computing capabilities and have strengths in AI-based deep learning, scientific computing, Computational Fluid Dynamics (CFD), computing finance, seismic analysis, molecular modeling, and genomics.

**Specifications**

.. table:: **Table 8** P2v ECS specifications

   +----------------+-------+--------+-----------------------------------------+---------------------------+-----------------+-----------+----------+----------------+------------+----------------+-------------------------------------------+
   | Flavor         | vCPUs | Memory | Max./Assured Network Bandwidth (Gbit/s) | Max. Network PPS (10,000) | Max. NIC Queues | Max. NICs | GPUs     | GPU Connection | GPU Memory | Virtualization | Hardware                                  |
   |                |       |        |                                         |                           |                 |           |          |                |            |                |                                           |
   |                |       | (GiB)  |                                         |                           |                 |           |          |                | (GiB)      |                |                                           |
   +================+=======+========+=========================================+===========================+=================+===========+==========+================+============+================+===========================================+
   | p2v.2xlarge.8  | 8     | 64     | 10/4                                    | 50                        | 4               | 4         | 1 x V100 | N/A            | 1 x 16 GiB | KVM            | CPU: Intel® Xeon® Skylake-SP Gold 6151 v5 |
   +----------------+-------+--------+-----------------------------------------+---------------------------+-----------------+-----------+----------+----------------+------------+----------------+-------------------------------------------+
   | p2v.4xlarge.8  | 16    | 128    | 15/8                                    | 100                       | 8               | 8         | 2 x V100 | NVLink         | 2 x 16 GiB | KVM            |                                           |
   +----------------+-------+--------+-----------------------------------------+---------------------------+-----------------+-----------+----------+----------------+------------+----------------+-------------------------------------------+
   | p2v.8xlarge.8  | 32    | 256    | 25/15                                   | 200                       | 16              | 8         | 4 x V100 | NVLink         | 4 x 16 GiB | KVM            |                                           |
   +----------------+-------+--------+-----------------------------------------+---------------------------+-----------------+-----------+----------+----------------+------------+----------------+-------------------------------------------+
   | p2v.16xlarge.8 | 64    | 512    | 30/30                                   | 400                       | 32              | 8         | 8 x V100 | NVLink         | 8 x 16 GiB | KVM            |                                           |
   +----------------+-------+--------+-----------------------------------------+---------------------------+-----------------+-----------+----------+----------------+------------+----------------+-------------------------------------------+

**P2v ECS Features**

-  CPU: Intel® Xeon® Scalable 6151 processors (3.0 GHz of basic frequency and 3.4 GHz of turbo frequency).

-  Up to eight NVIDIA Tesla V100 GPUs on an ECS

-  NVIDIA CUDA parallel computing and common deep learning frameworks, such as TensorFlow, Caffe, PyTorch, and MXNet

-  15.7 TFLOPS of single-precision computing and 7.8 TFLOPS of double-precision computing

-  NVIDIA Tensor cores with 125 TFLOPS of single- and double-precision computing for deep learning

-  Up to 30 Gbit/s of network bandwidth on a single ECS

-  16 GiB of HBM2 GPU memory with a bandwidth of 900 Gbit/s

-  Comprehensive basic capabilities

   -  User-defined network with flexible subnet division and network access policy configuration
   -  Mass storage, elastic expansion, and backup and restoration
   -  Elastic scaling

-  Flexibility

   Similar to other types of ECSs, P2v ECSs can be provisioned in a few minutes.

-  Excellent supercomputing ecosystem

   The supercomputing ecosystem allows you to build up a flexible, high-performance, cost-effective computing platform. A large number of HPC applications and deep-learning frameworks can run on P2v ECSs.

**Supported Common Software**

P2v ECSs are used in computing acceleration scenarios, such as deep learning training, inference, scientific computing, molecular modeling, and seismic analysis. If the software is required to support GPU CUDA, use P2v ECSs. P2v ECSs support the following commonly used software:

-  Common deep learning frameworks, such as TensorFlow, Caffe, PyTorch, and MXNet
-  CUDA GPU rendering supported by RedShift for Autodesk 3ds Max and V-Ray for 3ds Max
-  Agisoft PhotoScan
-  MapD

**Notes**

-  After a P2v ECS is stopped, basic resources (including vCPUs, memory, image, and GPUs) are not billed, but its system disk is billed based on the disk capacity. If other products, such as EVS disks, EIP, and bandwidth are associated with the ECS, these products are billed separately.

   .. note::

      Resources will be released after a P2v ECS is stopped. If resources are insufficient at the next start, the start may fail. If you want to use such an ECS for a long period of time, do not stop the ECS.

-  By default, P2v ECSs created using a Windows public image have the Tesla driver installed.
-  By default, P2v ECSs created using a Linux public image do not have a Tesla driver installed. After the ECS is created, install a driver on it for computing acceleration. For details, see :ref:`Manually Installing a Tesla Driver on a GPU-accelerated ECS <en-us_topic_0149470468>`.
-  If a P2v ECS is created using a private image, make sure that the Tesla driver was installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Manually Installing a Tesla Driver on a GPU-accelerated ECS <en-us_topic_0149470468>`.
-  GPU-accelerated ECSs differ greatly in general-purpose and heterogeneous computing power. Their specifications can only be changed to other specifications of the same instance type.
-  GPU-accelerated ECSs do not support live migration.

.. _en-us_topic_0097289624__section3135224614:

Inference-accelerated Pi5e
--------------------------

**Overview**

Pi5e ECSs use NVIDIA Ada Lovelace L4 Tensor Core GPUs that are dedicated for real-time AI inference. This series is the most efficient NVIDIA accelerator for mainstream applications. Servers equipped with L4 power up to 120x higher AI video performance and 2.7x more generative AI performance over CPU solutions, as well as over 4x more graphics performance than the previous GPU generation. NVIDIA L4's versatility and energy-efficient, single-slot, low-profile form factor make it ideal for global deployments, including edge locations.

**Specifications**

.. table:: **Table 9** Pi5e ECS specifications

   +-----------------+-------+--------+-----------------------------------------+------------------+-----------------+-----------+--------+------------+-------------+----------------+
   | Flavor          | vCPUs | Memory | Max./Assured Network Bandwidth (Gbit/s) | Max. Network PPS | Max. NIC Queues | Max. NICs | GPUs   | GPU Memory | Local Disks | Virtualization |
   |                 |       |        |                                         |                  |                 |           |        |            |             |                |
   |                 |       | (GiB)  |                                         | (10,000)         |                 |           |        | (GiB)      |             |                |
   +=================+=======+========+=========================================+==================+=================+===========+========+============+=============+================+
   | pi5e.2xlarge.4  | 8     | 32     | 15/3                                    | 150              | 4               | 4         | 1 x L4 | 24         | ``-``       | KVM            |
   +-----------------+-------+--------+-----------------------------------------+------------------+-----------------+-----------+--------+------------+-------------+----------------+
   | pi5e.4xlarge.4  | 16    | 64     | 20/6                                    | 280              | 8               | 8         | 1 x L4 | 24         | ``-``       | KVM            |
   +-----------------+-------+--------+-----------------------------------------+------------------+-----------------+-----------+--------+------------+-------------+----------------+
   | pi5e.8xlarge.4  | 32    | 128    | 30/12                                   | 550              | 8               | 8         | 2 x L4 | 48         | ``-``       | KVM            |
   +-----------------+-------+--------+-----------------------------------------+------------------+-----------------+-----------+--------+------------+-------------+----------------+
   | pi5e.12xlarge.4 | 48    | 192    | 35/18                                   | 750              | 16              | 8         | 4 x L4 | 96         | ``-``       | KVM            |
   +-----------------+-------+--------+-----------------------------------------+------------------+-----------------+-----------+--------+------------+-------------+----------------+
   | pi5e.16xlarge.4 | 64    | 256    | 36/24                                   | 800              | 16              | 8         | 4 x L4 | 96         | ``-``       | KVM            |
   +-----------------+-------+--------+-----------------------------------------+------------------+-----------------+-----------+--------+------------+-------------+----------------+
   | pi5e.24xlarge.4 | 96    | 384    | 40/36                                   | 850              | 32              | 8         | 6 x L4 | 144        | ``-``       | KVM            |
   +-----------------+-------+--------+-----------------------------------------+------------------+-----------------+-----------+--------+------------+-------------+----------------+

**Pi5e ECS features**:

-  1:4 ratio of vCPUs to memory
-  CPU: 3rd Generation Intel® Xeon® Scalable 6348 processors (2.6 GHz of basic frequency and 3.5 GHz of turbo frequency)
-  24 GiB of GPU memory per card
-  Up to 300 GB/s of GPU memory bandwidth
-  GPUDirect Peer to Peer (P2P)

**Notes**

-  Pi5e ECSs support automatic recovery when the hosts accommodating such ECSs become faulty.
-  After a Pi5e ECS is stopped, its basic resources (vCPUs, memory, image, and encoding cards) are not billed, but its system disk is billed based on the disk capacity. If other service resources, such as EVS disks, EIPs, and bandwidth are associated with the ECS, these resources are billed separately.
-  Specifications of Pi5e ECSs can only be changed to other specifications of the same instance type.
-  Pi5e ECSs support TPM.

.. _en-us_topic_0097289624__section1846114713182:

Inference-accelerated Pi2
-------------------------

**Overview**

Pi2 ECSs use NVIDIA Tesla T4 GPUs dedicated for real-time AI inference. These ECSs use the T4 INT8 calculator for up to 130 TOPS of INT8 computing. The Pi2 ECSs can also be used for light-load training.

**Specifications**

.. table:: **Table 10** Pi2 ECS specifications

   +----------------+-------+--------+--------------------------------+------------------+-----------------+-----------+--------+------------+-------------+----------------+----------------------------------------------------------------------------------+
   | Flavor         | vCPUs | Memory | Max./Assured Network Bandwidth | Max. Network PPS | Max. NIC Queues | Max. NICs | GPUs   | GPU Memory | Local Disks | Virtualization | Hardware                                                                         |
   |                |       |        |                                |                  |                 |           |        |            |             |                |                                                                                  |
   |                |       | (GiB)  | (Gbit/s)                       | (10,000)         |                 |           |        | (GiB)      |             |                |                                                                                  |
   +================+=======+========+================================+==================+=================+===========+========+============+=============+================+==================================================================================+
   | pi2.2xlarge.4  | 8     | 32     | 10/4                           | 50               | 4               | 4         | 1 x T4 | 1 x 16 GiB | N/A         | KVM            | CPU: Intel® Xeon® Skylake 6151 3.0 GHz or Intel® Xeon® Cascade Lake 6278 2.6 GHz |
   +----------------+-------+--------+--------------------------------+------------------+-----------------+-----------+--------+------------+-------------+----------------+----------------------------------------------------------------------------------+
   | pi2.3xlarge.4  | 12    | 48     | 12/6                           | 80               | 6               | 6         | 1 x T4 | 1 x 16 GiB | N/A         | KVM            |                                                                                  |
   +----------------+-------+--------+--------------------------------+------------------+-----------------+-----------+--------+------------+-------------+----------------+----------------------------------------------------------------------------------+
   | pi2.4xlarge.4  | 16    | 64     | 15/8                           | 100              | 8               | 8         | 2 x T4 | 2 x 16 GiB | N/A         | KVM            |                                                                                  |
   +----------------+-------+--------+--------------------------------+------------------+-----------------+-----------+--------+------------+-------------+----------------+----------------------------------------------------------------------------------+
   | pi2.8xlarge.4  | 32    | 128    | 25/15                          | 200              | 16              | 8         | 4 x T4 | 4 x 16 GiB | N/A         | KVM            |                                                                                  |
   +----------------+-------+--------+--------------------------------+------------------+-----------------+-----------+--------+------------+-------------+----------------+----------------------------------------------------------------------------------+
   | pi2.16xlarge.4 | 64    | 256    | 30/30                          | 400              | 32              | 8         | 8 x T4 | 8 x 16 GiB | N/A         | KVM            |                                                                                  |
   +----------------+-------+--------+--------------------------------+------------------+-----------------+-----------+--------+------------+-------------+----------------+----------------------------------------------------------------------------------+

**Pi2 ECS Features**

-  CPU: 2nd Generation Intel® Xeon® Scalable 6278 processors (2.6 GHz of basic frequency and 3.5 GHz of turbo frequency), or Intel® Xeon® Scalable 6151 processors (3.0 GHz of basic frequency and 3.4 GHz of turbo frequency)
-  Up to four NVIDIA Tesla T4 GPUs on an ECS
-  GPU hardware passthrough
-  Up to 8.1 TFLOPS of single-precision computing on a single GPU
-  Up to 130 TOPS of INT8 computing on a single GPU
-  16 GiB of GDDR6 GPU memory with a bandwidth of 320 GiB/s on a single GPU
-  One NVENC engine and two NVDEC engines embedded

**Supported Common Software**

Pi2 ECSs are used in GPU-based inference computing scenarios, such as image recognition, speech recognition, and natural language processing. The Pi2 ECSs can also be used for light-load training.

Pi2 ECSs support the following commonly used software:

-  Deep learning frameworks, such as TensorFlow, Caffe, PyTorch, and MXNet

**Notes**

-  After a Pi2 ECS is stopped, basic resources (including vCPUs, memory, image, and GPUs) are not billed, but its system disk is billed based on the disk capacity. If other products, such as EVS disks, EIP, and bandwidth are associated with the ECS, these products are billed separately.

   .. note::

      Resources will be released after a Pi2 ECS is stopped. If resources are insufficient at the next start, the start may fail. If you want to use such an ECS for a long period of time, do not stop the ECS.

-  Pi2 ECSs support automatic recovery when the hosts accommodating such ECSs become faulty.
-  By default, Pi2 ECSs created using a Windows public image have the Tesla driver installed.
-  By default, Pi2 ECSs created using a Linux public image do not have a Tesla driver installed. After the ECS is created, install a driver on it for computing acceleration. For details, see :ref:`Manually Installing a Tesla Driver on a GPU-accelerated ECS <en-us_topic_0149470468>`.
-  If a Pi2 ECS is created using a private image, make sure that the Tesla driver was installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Manually Installing a Tesla Driver on a GPU-accelerated ECS <en-us_topic_0149470468>`.
-  GPU-accelerated ECSs differ greatly in general-purpose and heterogeneous computing power. Their specifications can only be changed to other specifications of the same instance type.
-  GPU-accelerated ECSs do not support live migration.
