:original_name: en-us_topic_0097289624.html

.. _en-us_topic_0097289624:

GPU-accelerated ECSs
====================

GPU-accelerated ECSs provide outstanding floating-point computing capabilities. They are suitable for applications that require real-time, highly concurrent massive computing.

GPU-accelerated ECSs are classified as G series and P series of ECSs.

-  G series: Graphics-accelerated ECSs, which are suitable for 3D animation rendering and CAD
-  P series: Computing-accelerated or inference-accelerated ECSs, which are suitable for deep learning, scientific computing, and CAE

GPU-accelerated ECS Types
-------------------------

Recommended: :ref:`Computing-accelerated P2s <en-us_topic_0097289624__section1454714546567>`, :ref:`Inference-accelerated Pi2 <en-us_topic_0097289624__section1846114713182>`, and :ref:`Graphics-accelerated Enhancement G6 <en-us_topic_0097289624__section131302034104515>`

Available now: All GPU models except the recommended ones. If available ECSs are sold out, use the recommended ones.

-  G series

   -  :ref:`Graphics-accelerated Enhancement G7 <en-us_topic_0097289624__section2325028104711>`
   -  :ref:`Graphics-accelerated Enhancement G6 <en-us_topic_0097289624__section131302034104515>`

-  P series

   -  :ref:`Computing-accelerated P3 <en-us_topic_0097289624__section48861652193>`
   -  :ref:`Computing-accelerated P2s <en-us_topic_0097289624__section1454714546567>` (recommended)
   -  :ref:`Computing-accelerated P2v <en-us_topic_0097289624__section208472383415>`
   -  :ref:`Computing-accelerated P2 <en-us_topic_0097289624__section5477185118234>`
   -  :ref:`Computing-accelerated P1 <en-us_topic_0097289624__section1124594913391>`
   -  :ref:`Inference-accelerated Pi2 <en-us_topic_0097289624__section1846114713182>` (recommended)

Helpful links:

-  :ref:`Installing a GRID Driver on a GPU-accelerated ECS <en-us_topic_0149610914>`
-  :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`

.. _en-us_topic_0097289624__section2325028104711:

Graphics-accelerated Enhancement G7
-----------------------------------

**Overview**

G7 ECSs use NVIDIA A40 GPUs and support DirectX, Shader Model, OpenGL, and Vulkan. Each GPU provides 48 GiB of GPU memory. Theoretically, G7 ECSs provide 37.4 TFLOPS of FP32 peak performance and 74.8 TFLOPS (sparsity disabled) or 149.6 TFLOPS (sparsity enabled) of TF32 peak tensor performance. They deliver two times the rendering performance and 1.4 times the graphics processing performance of RTX6000 GPUs to meet professional graphics processing requirements.

Select your desired GPU-accelerated ECS type and specifications.

**Specifications**

.. table:: **Table 1** G7 ECS specifications

   +---------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+------------+----------------+
   | Flavor        | vCPUs | Memory | Max./Assured Bandwidth | Max. PPS | Max. NIC Queues | Max. NICs | GPUs           | GPU Memory | Virtualization |
   |               |       |        |                        |          |                 |           |                |            |                |
   |               |       | (GiB)  | (Gbit/s)               | (10,000) |                 |           |                | (GiB)      |                |
   +===============+=======+========+========================+==========+=================+===========+================+============+================+
   | g7.12xlarge.8 | 48    | 384    | 35/18                  | 750      | 16              | 8         | 1 x NVIDIA-A40 | 1 x 48     | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+------------+----------------+
   | g7.24xlarge.8 | 96    | 768    | 40/36                  | 850      | 16              | 8         | 2 x NVIDIA-A40 | 2 x 48     | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+----------------+------------+----------------+

**G7 ECS Features**

-  CPU: 3rd Generation Intel® Xeon® Scalable 8378A processors (3.0 GHz of base frequency and 3.5 GHz of turbo frequency)
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
-  3DS MAX
-  MAYA
-  Agisoft PhotoScan
-  ContextCapture
-  Adobe Premiere Pro
-  Solidworks
-  Unreal Engine
-  Blender
-  Vray

**Notes**

-  G7 ECSs support the following OSs:

   -  Windows Server 2019 Standard 64bit
   -  Windows Server 2016 Standard 64bit
   -  CentOS 8.2 64bit
   -  CentOS 7.6 64bit
   -  Ubuntu Server 20.04 64bit
   -  Ubuntu Server 18.04 64bit

-  G7 ECSs created using a public image have had the GRID driver of a specific version installed by default. However, you need to purchase and configure a GRID license by yourself. Ensure that the GRID driver version meets service requirements.
-  If a G7 ECS is created using a private image, make sure that the GRID driver was installed during the private image creation. If the GRID driver has not been installed, install the driver for graphics acceleration after the ECS is created.

.. _en-us_topic_0097289624__section131302034104515:

Graphics-accelerated Enhancement G6
-----------------------------------

**Overview**

G6 ECSs use NVIDIA Tesla T4 GPUs to support DirectX, OpenGL, and Vulkan and provide 16 GiB of GPU memory. The theoretical Pixel rate is 101.8 Gpixel/s and Texture rate 254.4 GTexel/s, meeting professional graphics processing requirements.

Select your desired GPU-accelerated ECS type and specifications.

**Specifications**

.. table:: **Table 2** G6 ECS specifications

   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------+------------+----------------+
   | Flavor        | vCPUs | Memory | Max./Assured Bandwidth | Max. PPS | Max. NIC Queues | Max. NICs | GPUs   | GPU Memory | Virtualization |
   |               |       |        |                        |          |                 |           |        |            |                |
   |               |       | (GiB)  | (Gbit/s)               | (10,000) |                 |           |        | (GiB)      |                |
   +===============+=======+========+========================+==========+=================+===========+========+============+================+
   | g6.4xlarge.4  | 16    | 64     | 25/15                  | 200      | 8               | 8         | 1 x T4 | 16         | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------+------------+----------------+
   | g6.10xlarge.7 | 40    | 280    | 25/15                  | 200      | 16              | 8         | 1 x T4 | 16         | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------+------------+----------------+
   | g6.20xlarge.7 | 80    | 560    | 30/30                  | 400      | 32              | 16        | 2 x T4 | 32         | KVM            |
   +---------------+-------+--------+------------------------+----------+-----------------+-----------+--------+------------+----------------+

.. note::

   A G6.10xlarge.7 ECS exclusively uses a T4 GPU for professional graphics acceleration. Such an ECS can be used for heavy-load CPU inference.

**G6 ECS Features**

-  CPU: 2nd Generation Intel® Xeon® Scalable 6266 processors (3.0 GHz of base frequency and 3.4 GHz of turbo frequency)
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
-  3DS MAX
-  MAYA
-  Agisoft PhotoScan
-  ContextCapture

**Notes**

-  :ref:`Table 3 <en-us_topic_0097289624__table192771727112217>` lists the OSs supported by G6 ECSs.

   .. _en-us_topic_0097289624__table192771727112217:

   .. table:: **Table 3** Supported OS versions

      +-----------------------------------+------------------------------------------+
      | OS                                | Version                                  |
      +===================================+==========================================+
      | EulerOS                           | EulerOS 2.5 64bit                        |
      +-----------------------------------+------------------------------------------+
      | Windows                           | -  Windows Server 2019 Standard 64bit    |
      |                                   | -  Windows Server 2016 Standard 64bit    |
      |                                   | -  Windows Server 2012 R2 Standard 64bit |
      +-----------------------------------+------------------------------------------+

-  G6 ECSs created using a public image have had the GRID driver of a specific version installed by default. However, you need to purchase and configure a GRID license by yourself. Ensure that the GRID driver version meets service requirements.

-  If a G6 ECS is created using a private image, make sure that the GRID driver was installed during the private image creation. If not, install the driver for graphics acceleration after the ECS is created.

.. _en-us_topic_0097289624__section48861652193:

Computing-accelerated P3
------------------------

**Overview**

P3 ECSs use NVIDIA A100 GPUs and provide flexibility and ultra-high-performance computing. P3 ECSs have strengths in AI-based deep learning, scientific computing, Computational Fluid Dynamics (CFD), computing finance, seismic analysis, molecular modeling, and genomics. Theoretically, P3 ECSs provide 19.5 TFLOPS of FP32 single-precision performance and 156 TFLOPS (sparsity disabled) or 312 TFLOPS (sparsity enabled) of TF32 peak tensor performance.

**Specifications**

.. table:: **Table 4** P3 ECS specifications

   +---------------+-------+--------+---------------------------------+----------+-----------------+-----------+----------------------+------------+----------------+
   | Flavor        | vCPUs | Memory | Max./Assured Bandwidth (Gbit/s) | Max. PPS | Max. NIC Queues | Max. NICs | GPUs                 | GPU Memory | Virtualization |
   |               |       |        |                                 |          |                 |           |                      |            |                |
   |               |       | (GiB)  |                                 | (10,000) |                 |           |                      | (GiB)      |                |
   +===============+=======+========+=================================+==========+=================+===========+======================+============+================+
   | p3.2xlarge.8  | 8     | 64     | 10/4                            | 100      | 4               | 4         | 1 x NVIDIA A100 80GB | 80         | KVM            |
   +---------------+-------+--------+---------------------------------+----------+-----------------+-----------+----------------------+------------+----------------+
   | p3.4xlarge.8  | 16    | 128    | 15/8                            | 200      | 8               | 8         | 2 x NVIDIA A100 80GB | 160        | KVM            |
   +---------------+-------+--------+---------------------------------+----------+-----------------+-----------+----------------------+------------+----------------+
   | p3.8xlarge.8  | 32    | 256    | 25/15                           | 350      | 16              | 8         | 4 x NVIDIA A100 80GB | 320        | KVM            |
   +---------------+-------+--------+---------------------------------+----------+-----------------+-----------+----------------------+------------+----------------+
   | p3.16xlarge.8 | 64    | 512    | 36/30                           | 700      | 32              | 8         | 8 x NVIDIA A100 80GB | 640        | KVM            |
   +---------------+-------+--------+---------------------------------+----------+-----------------+-----------+----------------------+------------+----------------+

**P3 ECS Features**

-  CPU: 2nd Generation Intel® Xeon® Scalable 6248R processors and 3.0 GHz of base frequency

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

-  Common deep learning frameworks, such as TensorFlow, Spark, PyTorch, MXNet, and Caffee
-  CUDA GPU rendering supported by RedShift for Autodesk 3dsMax and V-Ray for 3ds Max
-  Agisoft PhotoScan
-  MapD
-  More than 2,000 GPU-accelerated applications such as Amber, NAMD, and VASP

**Notes**

-  P3 ECSs support the following OSs:

   -  Ubuntu 20.04 server 64bit
   -  Ubuntu 18.04 server 64bit
   -  CentOS 8.2 64bit
   -  CentOS 8.1 64bit
   -  CentOS 8.0 64bit
   -  CentOS 7.9 64bit
   -  CentOS 7.8 64bit
   -  CentOS 7.7 64bit
   -  CentOS 7.6 64bit

-  If a P3 ECS is created using a private image, make sure that the Tesla driver has been installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.

.. _en-us_topic_0097289624__section1454714546567:

Computing-accelerated P2s
-------------------------

**Overview**

P2s ECSs use NVIDIA Tesla V100 GPUs to provide flexibility, high-performance computing, and cost-effectiveness. P2s ECSs provide outstanding general computing capabilities and have strengths in AI-based deep learning, scientific computing, Computational Fluid Dynamics (CFD), computing finance, seismic analysis, molecular modeling, and genomics.

**Specifications**

.. table:: **Table 5** P2s ECS specifications

   +----------------+-------+--------+---------------------------------+-------------------+-----------------+-----------+----------+----------------+------------------+----------------+----------------------------------------------------------+
   | Flavor         | vCPUs | Memory | Max./Assured Bandwidth (Gbit/s) | Max. PPS (10,000) | Max. NIC Queues | Max. NICs | GPUs     | GPU Connection | GPU Memory (GiB) | Virtualization | Hardware                                                 |
   |                |       |        |                                 |                   |                 |           |          |                |                  |                |                                                          |
   |                |       | (GiB)  |                                 |                   |                 |           |          |                |                  |                |                                                          |
   +================+=======+========+=================================+===================+=================+===========+==========+================+==================+================+==========================================================+
   | p2s.2xlarge.8  | 8     | 64     | 10/4                            | 50                | 4               | 4         | 1 x V100 | PCIe Gen3      | 1 x 32 GiB       | KVM            | CPU: 2nd Generation Intel® Xeon® Scalable Processor 6278 |
   +----------------+-------+--------+---------------------------------+-------------------+-----------------+-----------+----------+----------------+------------------+----------------+----------------------------------------------------------+
   | p2s.4xlarge.8  | 16    | 128    | 15/8                            | 100               | 8               | 8         | 2 x V100 | PCIe Gen3      | 2 x 32 GiB       | KVM            |                                                          |
   +----------------+-------+--------+---------------------------------+-------------------+-----------------+-----------+----------+----------------+------------------+----------------+----------------------------------------------------------+
   | p2s.8xlarge.8  | 32    | 256    | 25/15                           | 200               | 16              | 8         | 4 x V100 | PCIe Gen3      | 4 x 32 GiB       | KVM            |                                                          |
   +----------------+-------+--------+---------------------------------+-------------------+-----------------+-----------+----------+----------------+------------------+----------------+----------------------------------------------------------+
   | p2s.16xlarge.8 | 64    | 512    | 30/30                           | 400               | 32              | 8         | 8 x V100 | PCIe Gen3      | 8 x 32 GiB       | KVM            |                                                          |
   +----------------+-------+--------+---------------------------------+-------------------+-----------------+-----------+----------+----------------+------------------+----------------+----------------------------------------------------------+

**P2s ECS Features**

-  CPU: 2nd Generation Intel® Xeon® Scalable 6278 processors (2.6 GHz of base frequency and 3.5 GHz of turbo frequency), or Intel® Xeon® Scalable 6151 processors (3.0 GHz of base frequency and 3.4 GHz of turbo frequency)

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
-  CUDA GPU rendering supported by RedShift for Autodesk 3dsMax and V-Ray for 3ds Max
-  Agisoft PhotoScan
-  MapD

**Notes**

-  :ref:`Table 6 <en-us_topic_0097289624__table1613585194612>` lists the OSs supported by P2s ECSs.

   .. _en-us_topic_0097289624__table1613585194612:

   .. table:: **Table 6** Supported OS versions

      +-----------------------------------+------------------------------------------+
      | OS                                | Version                                  |
      +===================================+==========================================+
      | CentOS                            | CentOS 7.9 64bit                         |
      +-----------------------------------+------------------------------------------+
      | EulerOS                           | EulerOS 2.5 64bit                        |
      +-----------------------------------+------------------------------------------+
      | Oracle Linux                      | Oracle Linux Server release 7.6 64bit    |
      +-----------------------------------+------------------------------------------+
      | Ubuntu                            | -  Ubuntu 20.04 server 64bit             |
      |                                   | -  Ubuntu 18.04 server 64bit             |
      +-----------------------------------+------------------------------------------+
      | Windows                           | -  Windows Server 2019 Standard 64bit    |
      |                                   | -  Windows Server 2016 Standard 64bit    |
      |                                   | -  Windows Server 2012 R2 Standard 64bit |
      +-----------------------------------+------------------------------------------+

-  By default, P2s ECSs created using a Windows public image have the Tesla driver installed.

-  If a P2s ECS is created using a private image, make sure that the Tesla driver was installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.

.. _en-us_topic_0097289624__section208472383415:

Computing-accelerated P2v
-------------------------

**Overview**

P2v ECSs use NVIDIA Tesla V100 GPUs and deliver high flexibility, high-performance computing, and high cost-effectiveness. These ECSs use GPU NVLink for direct communication between GPUs, improving data transmission efficiency. P2v ECSs provide outstanding general computing capabilities and have strengths in AI-based deep learning, scientific computing, Computational Fluid Dynamics (CFD), computing finance, seismic analysis, molecular modeling, and genomics.

**Specifications**

.. table:: **Table 7** P2v ECS specifications

   +----------------+-------+--------+---------------------------------+-------------------+-----------------+-----------+----------+----------------+------------+----------------+-------------------------------------------+
   | Flavor         | vCPUs | Memory | Max./Assured Bandwidth (Gbit/s) | Max. PPS (10,000) | Max. NIC Queues | Max. NICs | GPUs     | GPU Connection | GPU Memory | Virtualization | Hardware                                  |
   |                |       |        |                                 |                   |                 |           |          |                |            |                |                                           |
   |                |       | (GiB)  |                                 |                   |                 |           |          |                | (GiB)      |                |                                           |
   +================+=======+========+=================================+===================+=================+===========+==========+================+============+================+===========================================+
   | p2v.2xlarge.8  | 8     | 64     | 10/4                            | 50                | 4               | 4         | 1 x V100 | N/A            | 1 x 16 GiB | KVM            | CPU: Intel® Xeon® Skylake-SP Gold 6151 v5 |
   +----------------+-------+--------+---------------------------------+-------------------+-----------------+-----------+----------+----------------+------------+----------------+-------------------------------------------+
   | p2v.4xlarge.8  | 16    | 128    | 15/8                            | 100               | 8               | 8         | 2 x V100 | NVLink         | 2 x 16 GiB | KVM            |                                           |
   +----------------+-------+--------+---------------------------------+-------------------+-----------------+-----------+----------+----------------+------------+----------------+-------------------------------------------+
   | p2v.8xlarge.8  | 32    | 256    | 25/15                           | 200               | 16              | 8         | 4 x V100 | NVLink         | 4 x 16 GiB | KVM            |                                           |
   +----------------+-------+--------+---------------------------------+-------------------+-----------------+-----------+----------+----------------+------------+----------------+-------------------------------------------+
   | p2v.16xlarge.8 | 64    | 512    | 30/30                           | 400               | 32              | 8         | 8 x V100 | NVLink         | 8 x 16 GiB | KVM            |                                           |
   +----------------+-------+--------+---------------------------------+-------------------+-----------------+-----------+----------+----------------+------------+----------------+-------------------------------------------+

**P2v ECS Features**

-  CPU: Intel® Xeon® Scalable 6151 processors (3.0 GHz of base frequency and 3.4 GHz of turbo frequency).

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
-  CUDA GPU rendering supported by RedShift for Autodesk 3dsMax and V-Ray for 3ds Max
-  Agisoft PhotoScan
-  MapD

**Notes**

-  :ref:`Table 8 <en-us_topic_0097289624__table1793214116522>` lists the OSs supported by P2v ECSs.

   .. _en-us_topic_0097289624__table1793214116522:

   .. table:: **Table 8** Supported OS versions

      +-----------------------------------+------------------------------------------+
      | OS                                | Version                                  |
      +===================================+==========================================+
      | CentOS                            | CentOS 7.9 64bit                         |
      +-----------------------------------+------------------------------------------+
      | EulerOS                           | EulerOS 2.5 64bit                        |
      +-----------------------------------+------------------------------------------+
      | Oracle Linux                      | Oracle Linux Server release 7.6 64bit    |
      +-----------------------------------+------------------------------------------+
      | Ubuntu                            | -  Ubuntu 20.04 server 64bit             |
      |                                   | -  Ubuntu 18.04 server 64bit             |
      +-----------------------------------+------------------------------------------+
      | Windows                           | -  Windows Server 2019 Standard 64bit    |
      |                                   | -  Windows Server 2016 Standard 64bit    |
      |                                   | -  Windows Server 2012 R2 Standard 64bit |
      +-----------------------------------+------------------------------------------+

-  By default, P2v ECSs created using a Windows public image have the Tesla driver installed.

-  By default, P2v ECSs created using a Linux public image do not have a Tesla driver installed. After the ECS is created, install a driver on it for computing acceleration. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.

-  If a P2v ECS is created using a private image, make sure that the Tesla driver was installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.

.. _en-us_topic_0097289624__section5477185118234:

Computing-accelerated P2
------------------------

**Overview**

Compared with P1 ECSs, P2 ECSs use NVIDIA Tesla V100 GPUs, which have improved both single- and double-precision computing capabilities by 50% and offer 112 TFLOPS of deep learning.

**Specifications**

.. table:: **Table 9** P2 ECS specifications

   +--------------+-------+--------+------------------------+----------+-----------------+-----------+----------+------------+------------------+----------------+----------------------------------------+
   | Flavor       | vCPUs | Memory | Max./Assured Bandwidth | Max. PPS | Max. NIC Queues | Max. NICs | GPUs     | GPU Memory | Local Disks      | Virtualization | Hardware                               |
   |              |       |        |                        |          |                 |           |          |            |                  |                |                                        |
   |              |       | (GiB)  | (Gbit/s)               | (10,000) |                 |           |          | (GiB)      |                  |                |                                        |
   +==============+=======+========+========================+==========+=================+===========+==========+============+==================+================+========================================+
   | p2.2xlarge.8 | 8     | 64     | 5/1.6                  | 35       | 2               | 12        | 1 x V100 | 1 x 16     | 1 x 800 GiB NVMe | KVM            | CPU: Intel® Xeon® Processor E5-2690 v4 |
   +--------------+-------+--------+------------------------+----------+-----------------+-----------+----------+------------+------------------+----------------+----------------------------------------+
   | p2.4xlarge.8 | 16    | 128    | 8/3.2                  | 70       | 4               | 12        | 2 x V100 | 2 x 16     | 2 x 800 GiB NVMe | KVM            |                                        |
   +--------------+-------+--------+------------------------+----------+-----------------+-----------+----------+------------+------------------+----------------+----------------------------------------+
   | p2.8xlarge.8 | 32    | 256    | 10/6.5                 | 140      | 8               | 12        | 4 x V100 | 4 x 16     | 4 x 800 GiB NVMe | KVM            |                                        |
   +--------------+-------+--------+------------------------+----------+-----------------+-----------+----------+------------+------------------+----------------+----------------------------------------+

**P2 ECS Features**

-  CPU: Intel® Xeon® Processor E5-2690 v4 (2.6 GHz)

-  NVIDIA Tesla V100 GPUs

-  GPU hardware passthrough

-  14 TFLOPS of single-precision computing, 7 TFLOPS of double-precision computing, and 112 TFLOPS of deep learning

-  Maximum network bandwidth of 12 Gbit/s

-  16 GiB of HBM2 GPU memory with a bandwidth of 900 Gbit/s

-  800 GiB NVMe SSDs for temporary local storage

-  Comprehensive basic capabilities

   -  User-defined network with flexible subnet division and network access policy configuration
   -  Mass storage, elastic expansion, and backup and restoration
   -  Elastic scaling

-  Flexibility

   Similar to other types of ECSs, P2 ECSs can be provisioned in a few minutes.

-  Excellent supercomputing ecosystem

   The supercomputing ecosystem allows you to build up a flexible, high-performance, cost-effective computing platform. A large number of HPC applications and deep-learning frameworks can run on P2 ECSs.

**Supported Common Software**

P2 ECSs are used in computing acceleration scenarios, such as deep learning training, inference, scientific computing, molecular modeling, and seismic analysis. If the software requires GPU CUDA parallel computing, use P2 ECSs. P2 ECSs support the following commonly used software:

-  Common deep learning frameworks, such as TensorFlow, Caffe, PyTorch, and MXNet
-  CUDA GPU rendering supported by RedShift for Autodesk 3dsMax and V-Ray for 3ds Max
-  Agisoft PhotoScan
-  MapD

**Notes**

-  The system disk of a P2 ECS must be greater than or equal to 15 GiB. It is recommended that the system disk be greater than 40 GiB.

-  The local NVMe SSDs attached to P2 ECSs are dedicated for services with strict requirements on storage I/O performance, such as deep learning training and HPC. Local disks are attached to the ECSs of specified flavors and cannot be separately bought. In addition, you are not allowed to detach a local disk and then attach it to another ECS.

   .. note::

      Data may be lost on the local NVMe SSDs attached to P2 ECSs due to a fault, for example, due to a disk or host fault. Therefore, you are suggested to store only temporary data in local NVMe SSDs. If you store important data in such a disk, securely back up the data.

-  P2 ECSs do not support specifications modification.

-  :ref:`Table 10 <en-us_topic_0097289624__table3436728145315>` lists the OSs supported by P2 ECSs.

   .. _en-us_topic_0097289624__table3436728145315:

   .. table:: **Table 10** Supported OS versions

      +-----------------------------------+------------------------------------------+
      | OS                                | Version                                  |
      +===================================+==========================================+
      | CentOS                            | CentOS 7.9 64bit                         |
      +-----------------------------------+------------------------------------------+
      | EulerOS                           | EulerOS 2.5 64bit                        |
      +-----------------------------------+------------------------------------------+
      | Oracle Linux                      | Oracle Linux Server release 7.6 64bit    |
      +-----------------------------------+------------------------------------------+
      | Ubuntu                            | -  Ubuntu 20.04 server 64bit             |
      |                                   | -  Ubuntu 18.04 server 64bit             |
      +-----------------------------------+------------------------------------------+
      | Windows                           | -  Windows Server 2019 Standard 64bit    |
      |                                   | -  Windows Server 2016 Standard 64bit    |
      |                                   | -  Windows Server 2012 R2 Standard 64bit |
      +-----------------------------------+------------------------------------------+

-  After you delete a P2 ECS, the data stored in local NVMe SSDs is automatically cleared.

-  By default, P2 ECSs created using a Linux public image do not have a Tesla driver installed. After the ECS is created, install a driver on it for computing acceleration. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.

-  If a P2 ECS is created using a private image, make sure that the Tesla driver was installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.

.. _en-us_topic_0097289624__section1124594913391:

Computing-accelerated P1
------------------------

**Overview**

P1 ECSs use NVIDIA Tesla P100 GPUs and provide flexibility, high performance, and cost-effectiveness. These ECSs support GPU Direct for direct communication between GPUs, improving data transmission efficiency. P1 ECSs provide outstanding general computing capabilities and have strengths in deep learning, graphic databases, high-performance databases, Computational Fluid Dynamics (CFD), computing finance, seismic analysis, molecular modeling, and genomics. They are designed for scientific computing.

**Specifications**

.. table:: **Table 11** P1 ECS specifications

   +--------------+-------+--------+------------------------+----------+-----------------+-----------+----------+------------+-------------+----------------+----------------------------------------+
   | Flavor       | vCPUs | Memory | Max./Assured Bandwidth | Max. PPS | Max. NIC Queues | Max. NICs | GPUs     | GPU Memory | Local Disks | Virtualization | Hardware                               |
   |              |       |        |                        |          |                 |           |          |            |             |                |                                        |
   |              |       | (GiB)  | (Gbit/s)               | (10,000) |                 |           |          | (GiB)      | (GiB)       |                |                                        |
   +==============+=======+========+========================+==========+=================+===========+==========+============+=============+================+========================================+
   | p1.2xlarge.8 | 8     | 64     | 5/1.6                  | 35       | 2               | 12        | 1 x P100 | 1 x 16     | 1 x 800     | KVM            | CPU: Intel® Xeon® Processor E5-2690 v4 |
   +--------------+-------+--------+------------------------+----------+-----------------+-----------+----------+------------+-------------+----------------+----------------------------------------+
   | p1.4xlarge.8 | 16    | 128    | 8/3.2                  | 70       | 4               | 12        | 2 x P100 | 2 x 16     | 2 x 800     | KVM            |                                        |
   +--------------+-------+--------+------------------------+----------+-----------------+-----------+----------+------------+-------------+----------------+----------------------------------------+
   | p1.8xlarge.8 | 32    | 256    | 10/6.5                 | 140      | 8               | 12        | 4 x P100 | 4 x 16     | 4 x 800     | KVM            |                                        |
   +--------------+-------+--------+------------------------+----------+-----------------+-----------+----------+------------+-------------+----------------+----------------------------------------+

**P1 ECS Features**

-  CPU: Intel® Xeon® E5-2690 v4 processors (2.6 GHz of base frequency and 3.5 GHz of turbo frequency)

-  Up to four NVIDIA Tesla P100 GPUs on a P1 ECS (If eight P100 GPUs are required on an instance, use BMS.)

-  GPU hardware passthrough

-  9.3 TFLOPS of single-precision computing and 4.7 TFLOPS of double-precision computing

-  Maximum network bandwidth of 10 Gbit/s

-  16 GiB of HBM2 GPU memory with a bandwidth of 732 Gbit/s

-  800 GiB NVMe SSDs for temporary local storage

-  Comprehensive basic capabilities

   -  User-defined network with flexible subnet division and network access policy configuration
   -  Mass storage, elastic expansion, and backup and restoration
   -  Elastic scaling

-  Flexibility

   Similar to other types of ECSs, P1 ECSs can be provisioned in a few minutes. You can configure specifications as needed. P1 ECSs with two, four, and eight GPUs will be supported later.

-  Excellent supercomputing ecosystem

   The supercomputing ecosystem allows you to build up a flexible, high-performance, cost-effective computing platform. A large number of HPC applications and deep-learning frameworks can run on P1 ECSs.

**Supported Common Software**

P1 ECSs are used in computing acceleration scenarios, such as deep learning training, inference, scientific computing, molecular modeling, and seismic analysis. If the software requires GPU CUDA parallel computing, use P1 ECSs. P1 ECSs support the following commonly used software:

-  Deep learning frameworks, such as TensorFlow, Caffe, PyTorch, and MXNet
-  RedShift for Autodesk 3dsMax, V-Ray for 3ds Max
-  Agisoft PhotoScan
-  MapD

**Notes**

-  It is recommended that the system disk of a P1 ECS be greater than 40 GiB.

-  The local NVMe SSDs attached to P1 ECSs are dedicated for services with strict requirements on storage I/O performance, such as deep learning training and HPC. Local disks are attached to the ECSs of specified flavors and cannot be separately bought. In addition, you are not allowed to detach a local disk and then attach it to another ECS.

   .. note::

      Data may be lost on the local NVMe SSDs attached to P1 ECSs due to a fault, for example, due to a disk or host fault. Therefore, you are suggested to store only temporary data in local NVMe SSDs. If you store important data in such a disk, securely back up the data.

-  After a P1 ECS is created, you must install the NVIDIA driver for computing acceleration. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.

-  P1 ECSs do not support specifications change.

-  P1 ECSs do not support automatic recovery.

   -  If the host is faulty or subhealthy, you need to stop the ECS for hardware repair.
   -  In case of system maintenance or hardware faults, the ECS will be redeployed (to ensure HA) and cold migrated to another host. The local disk data of the ECS will not be retained.

-  :ref:`Table 12 <en-us_topic_0097289624__table8704181020556>` lists the OSs supported by P1 ECSs.

   .. _en-us_topic_0097289624__table8704181020556:

   .. table:: **Table 12** Supported OS versions

      +-----------------------------------+---------------------------------------+
      | OS                                | Version                               |
      +===================================+=======================================+
      | CentOS                            | CentOS 7.9 64bit                      |
      +-----------------------------------+---------------------------------------+
      | Debian                            | -  Debian GNU/Linux 11 64bit          |
      |                                   | -  Debian GNU/Linux 10 64bit          |
      +-----------------------------------+---------------------------------------+
      | Oracle Linux                      | Oracle Linux Server release 7.6 64bit |
      +-----------------------------------+---------------------------------------+
      | Ubuntu                            | -  Ubuntu 20.04 server 64bit          |
      |                                   | -  Ubuntu 18.04 server 64bit          |
      +-----------------------------------+---------------------------------------+

-  After you delete a P1 ECS, the data stored in local NVMe SSDs is automatically cleared.

-  By default, P1 ECSs created using a Windows public image have the Tesla driver installed.

-  By default, P1 ECSs created using a Linux public image do not have a Tesla driver installed. After the ECS is created, install a driver on it for computing acceleration. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.

-  If a P1 ECS is created using a private image, make sure that the Tesla driver was installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.

.. _en-us_topic_0097289624__section1846114713182:

Inference-accelerated Pi2
-------------------------

**Overview**

Pi2 ECSs use NVIDIA Tesla T4 GPUs dedicated for real-time AI inference. These ECSs use the T4 INT8 calculator for up to 130 TOPS of INT8 computing. The Pi2 ECSs can also be used for light-load training.

**Specifications**

.. table:: **Table 13** Pi2 ECS specifications

   +----------------+-------+--------+------------------------+----------+-----------------+-----------+--------+------------+-------------+----------------+----------------------------------------------------------------------------------+
   | Flavor         | vCPUs | Memory | Max./Assured Bandwidth | Max. PPS | Max. NIC Queues | Max. NICs | GPUs   | GPU Memory | Local Disks | Virtualization | Hardware                                                                         |
   |                |       |        |                        |          |                 |           |        |            |             |                |                                                                                  |
   |                |       | (GiB)  | (Gbit/s)               | (10,000) |                 |           |        | (GiB)      |             |                |                                                                                  |
   +================+=======+========+========================+==========+=================+===========+========+============+=============+================+==================================================================================+
   | pi2.2xlarge.4  | 8     | 32     | 10/4                   | 50       | 4               | 4         | 1 x T4 | 1 x 16 GiB | N/A         | KVM            | CPU: Intel® Xeon® Skylake 6151 3.0 GHz or Intel® Xeon® Cascade Lake 6278 2.6 GHz |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+--------+------------+-------------+----------------+----------------------------------------------------------------------------------+
   | pi2.4xlarge.4  | 16    | 64     | 15/8                   | 100      | 8               | 8         | 2 x T4 | 2 x 16 GiB | N/A         | KVM            |                                                                                  |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+--------+------------+-------------+----------------+----------------------------------------------------------------------------------+
   | pi2.8xlarge.4  | 32    | 128    | 25/15                  | 200      | 16              | 8         | 4 x T4 | 4 x 16 GiB | N/A         | KVM            |                                                                                  |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+--------+------------+-------------+----------------+----------------------------------------------------------------------------------+
   | pi2.16xlarge.4 | 64    | 256    | 30/30                  | 400      | 32              | 8         | 8 x T4 | 8 x 16 GiB | N/A         | KVM            |                                                                                  |
   +----------------+-------+--------+------------------------+----------+-----------------+-----------+--------+------------+-------------+----------------+----------------------------------------------------------------------------------+

**Pi2 ECS Features**

-  CPU: 2nd Generation Intel® Xeon® Scalable 6278 processors (2.6 GHz of base frequency and 3.5 GHz of turbo frequency), or Intel® Xeon® Scalable 6151 processors (3.0 GHz of base frequency and 3.4 GHz of turbo frequency)
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

-  After a Pi2 ECS is stopped, basic resources including vCPUs, memory, image, and GPUs are not billed, but its system disk is billed based on the disk capacity. If other products, such as EVS disks, EIP, and bandwidth are associated with the ECS, these products are billed separately.

   .. note::

      Resources are released after a Pi2 ECS is stopped. If resources are insufficient when the Pi2 ECS is started after being stopped, starting the ECS might fail. Therefore, if you need to use a Pi2 ECS for a long time, keep the ECS running.

-  :ref:`Table 14 <en-us_topic_0097289624__table576493295720>` lists the OSs supported by Pi2 ECSs.

   .. _en-us_topic_0097289624__table576493295720:

   .. table:: **Table 14** Supported OS versions

      +-----------------------------------+------------------------------------------+
      | OS                                | Version                                  |
      +===================================+==========================================+
      | CentOS                            | CentOS 7.9 64bit                         |
      +-----------------------------------+------------------------------------------+
      | Oracle Linux                      | Oracle Linux Server release 7.6 64bit    |
      +-----------------------------------+------------------------------------------+
      | Ubuntu                            | -  Ubuntu 20.04 server 64bit             |
      |                                   | -  Ubuntu 18.04 server 64bit             |
      +-----------------------------------+------------------------------------------+
      | Windows                           | -  Windows Server 2019 Standard 64bit    |
      |                                   | -  Windows Server 2016 Standard 64bit    |
      |                                   | -  Windows Server 2012 R2 Standard 64bit |
      +-----------------------------------+------------------------------------------+

-  Pi2 ECSs support automatic recovery when the hosts accommodating such ECSs become faulty.

-  By default, Pi2 ECSs created using a Windows public image have the Tesla driver installed.

-  By default, Pi2 ECSs created using a Linux public image do not have a Tesla driver installed. After the ECS is created, install a driver on it for computing acceleration. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.

-  If a Pi2 ECS is created using a private image, make sure that the Tesla driver was installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.
