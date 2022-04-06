.. _en-us_topic_0097289624:

GPU-accelerated ECSs
====================

GPU-accelerated ECSs provide outstanding floating-point computing capabilities. They are suitable for applications that require real-time, highly concurrent massive computing.

GPU-accelerated ECSs are classified as G series and P series of ECSs.

-  G series: Graphics-accelerated ECSs, which are suitable for 3D animation rendering and CAD
-  P series: Computing-accelerated or inference-accelerated ECSs, which are suitable for deep learning, scientific computing, and CAE



.. _en-us_topic_0097289624__section106800321171:

GPU-accelerated ECS Types
-------------------------

GPU-accelerated ECSs are classified as graphics-accelerated (G series) and computing-accelerated (P series) ECSs.

Recommended:

:ref:`Inference-accelerated PI2 <en-us_topic_0097289624__section1846114713182>`

:ref:`Graphics-accelerated Enhancement G6 <en-us_topic_0097289624__section131302034104515>`

Available now: All GPU models except the recommended ones.

-  G series

   -  :ref:`Graphics-accelerated Enhancement G6 <en-us_topic_0097289624__section131302034104515>` (recommended)

-  P series

   -  :ref:`Computing-accelerated P2s <en-us_topic_0097289624__section1454714546567>` (recommended)
   -  :ref:`Computing-accelerated P2v <en-us_topic_0097289624__section208472383415>`
   -  :ref:`Computing-accelerated P2 <en-us_topic_0097289624__section5477185118234>`
   -  :ref:`Computing-accelerated P1 <en-us_topic_0097289624__section1124594913391>`
   -  :ref:`Inference-accelerated PI2 <en-us_topic_0097289624__section1846114713182>` (recommended)

Helpful links:

-  :ref:`Installing a GRID Driver on a GPU-accelerated ECS <en-us_topic_0149610914>`
-  :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`



.. _en-us_topic_0097289624__section131302034104515:

Graphics-accelerated Enhancement G6
-----------------------------------

**Overview**

G6 ECSs use NVIDIA Tesla T4 GPUs to support DirectX, OpenGL, and Vulkan and provide 16 GiB of GPU memory. The theoretical Pixel rate is 101.8 Gpixel/s and Texture rate 254.4 GTexel/s, meeting professional graphics processing requirements.

Select your desired GPU-accelerated ECS type and specifications.

**Specifications**



.. _en-us_topic_0097289624__table19812808468:

.. table:: **Table 1** G6 ECS specifications

   +---------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+--------+------------------+---------------------+-------------------------------------+
   | Flavor        | vCPUs | Memory (GiB) | Maximum/Assured Bandwidth (Gbit/s) | Max. PPS (10,000) | NIC Multi-Queue | Maximum NICs | GPUs   | GPU Memory (GiB) | Virtualization Type | Hardware                            |
   +===============+=======+==============+====================================+===================+=================+==============+========+==================+=====================+=====================================+
   | g6.10xlarge.7 | 40    | 280          | 25/15                              | 200               | 16              | 8            | 1 x T4 | 16               | KVM                 | CPU: Intel® Xeon® Cascade Lake 6266 |
   +---------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+--------+------------------+---------------------+-------------------------------------+
   | g6.20xlarge.7 | 80    | 560          | 30/30                              | 400               | 32              | 8            | 2 x T4 | 32               | KVM                 |                                     |
   +---------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+--------+------------------+---------------------+-------------------------------------+

.. note::

   A G6.10xlarge.7 ECS exclusively uses a T4 GPU for professional graphics acceleration. Such an ECS can be used for heavy-load CPU inference.

**G6 ECS Features**

-  CPU: 2nd Generation Intel® Xeon® Scalable 6266 processors (3.0 GHz of base frequency and 3.4 GHz of turbo frequency)
-  Graphics acceleration APIs

   -  DirectX 12, Direct2D, DirectX Video Acceleration (DXVA)
   -  OpenGL 4.5
   -  Vulkan 1.0

-  CUDA and OpenCL
-  NVIDIA T4 GPUs
-  Graphics acceleration applications
-  Heavy-load CPU inference
-  Application flow identical to common ECSs
-  Automatic scheduling of G6 ECSs to AZs where NVIDIA T4 GPUs are used
-  One built-in NVENC and two NVDEC GPUs

**Supported Common Software**

G6 ECSs are used in graphics acceleration scenarios, such as video rendering, cloud desktop, and 3D visualization. If the software relies on GPU DirectX and OpenGL hardware acceleration, use G6 ECSs. G6 ECSs support the following commonly used graphics processing software:

-  AutoCAD
-  3DS MAX
-  MAYA
-  Agisoft PhotoScan
-  ContextCapture

**Notes**

-  G6 ECSs support the following OS:

   -  Windows Server 2016 Standard 64bit

-  G6 ECSs created using a public image have had the GRID driver of a specific version installed by default. However, you need to purchase and configure the GRID license by yourself. Ensure that the GRID driver version meets service requirements.

-  If a G6 ECS is created using a private image, make sure that the GRID driver was installed during the private image creation. If not, install the driver for graphics acceleration after the ECS is created.



.. _en-us_topic_0097289624__section1454714546567:

Computing-accelerated P2s
-------------------------

**Overview**

P2s ECSs use NVIDIA Tesla V100 GPUs to provide flexibility, high-performance computing, and cost-effectiveness. P2s ECSs provide outstanding general computing capabilities and have strengths in AI-based deep learning, scientific computing, Computational Fluid Dynamics (CFD), computing finance, seismic analysis, molecular modeling, and genomics.

**Specifications**



.. _en-us_topic_0097289624__table85474544565:

.. table:: **Table 2** P2s ECS specifications

   +----------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+----------------+------------------+---------------------+----------------------------------------------------------+
   | Flavor         | vCPUs | Memory (GiB) | Maximum/Assured Bandwidth (Gbit/s) | Max. PPS (10,000) | NIC Multi-Queue | Maximum NICs | GPUs     | GPU Connection | GPU Memory (GiB) | Virtualization Type | Hardware                                                 |
   +================+=======+==============+====================================+===================+=================+==============+==========+================+==================+=====================+==========================================================+
   | p2s.2xlarge.8  | 8     | 64           | 10/4                               | 50                | 4               | 4            | 1 x V100 | PCIe Gen3      | 1 x 32 GiB       | KVM                 | CPU: 2nd Generation Intel® Xeon® Scalable Processor 6278 |
   +----------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+----------------+------------------+---------------------+----------------------------------------------------------+
   | p2s.4xlarge.8  | 16    | 128          | 15/8                               | 100               | 8               | 8            | 2 x V100 | PCIe Gen3      | 2 x 32 GiB       | KVM                 |                                                          |
   +----------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+----------------+------------------+---------------------+----------------------------------------------------------+
   | p2s.8xlarge.8  | 32    | 256          | 25/15                              | 200               | 16              | 8            | 4 x V100 | PCIe Gen3      | 4 x 32 GiB       | KVM                 |                                                          |
   +----------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+----------------+------------------+---------------------+----------------------------------------------------------+
   | p2s.16xlarge.8 | 64    | 512          | 30/30                              | 400               | 32              | 8            | 8 x V100 | PCIe Gen3      | 8 x 32 GiB       | KVM                 |                                                          |
   +----------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+----------------+------------------+---------------------+----------------------------------------------------------+

**P2s ECS Features**

-  CPU: 2nd Generation Intel® Xeon® Scalable 6278 processors (2.6 GHz of base frequency and 3.5 GHz of turbo frequency), or Intel® Xeon® Scalable 6151 processors (3.0 GHz of base frequency and 3.4 GHz of turbo frequency)

-  Up to eight NVIDIA Tesla V100 GPUs on an ECS

-  NVIDIA CUDA parallel computing and common deep learning frameworks, such as TensorFlow, Caffe, PyTorch, and MXNet

-  14 TFLOPS of single-precision computing and 7 TFLOPS of double-precision computing

-  NVIDIA Tensor cores with 112 TFLOPS of single- and double-precision computing for deep learning

-  Up to 30 Gbit/s of network bandwidth on a single ECS

-  32 GiB of HBM2 GPU memory with a bandwidth of 900 Gbit/s

-  Comprehensive basic capabilities

   Networks are user-defined, subnets can be divided, and network access policies can be configured as needed. Mass storage is used, elastic capacity expansion as well as backup and restoration are supported to make data more secure. Auto Scaling allows you to add or reduce the number of ECSs quickly.

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

-  P2s ECSs support the following OSs:

   -  Windows Server 2019 Standard 64bit
   -  Windows Server 2016 Standard 64bit
   -  Windows Server 2012 R2 Standard 64bit
   -  Ubuntu Server 20.04 64bit
   -  Ubuntu Server 18.04 64bit
   -  Ubuntu Server 16.04 64bit
   -  CentOS 7.7 64bit
   -  CentOS 7.4 64bit
   -  EulerOS 2.5 64bit
   -  Oracle Linux 7.6 64bit

-  By default, P2s ECSs created using a Windows public image have the Tesla driver installed.
-  If a P2s ECS is created using a private image, make sure that the Tesla driver was installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.



.. _en-us_topic_0097289624__section208472383415:

Computing-accelerated P2v
-------------------------

**Overview**

Compared with P2 ECSs, P2v ECSs use NVIDIA Tesla V100 GPUs to provide flexibility, high-performance computing, and cost-effectiveness. These ECSs use GPU NVLink for direct communication between GPUs, improving data transmission efficiency. P2v ECSs provide outstanding general computing capabilities and have strengths in AI-based deep learning, scientific computing, Computational Fluid Dynamics (CFD), computing finance, seismic analysis, molecular modeling, and genomics.

**Specifications**



.. _en-us_topic_0097289624__table87321433202814:

.. table:: **Table 3** P2v ECS specifications

   +----------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+----------------+------------------+---------------------+-------------------------------------------+
   | Flavor         | vCPUs | Memory (GiB) | Maximum/Assured Bandwidth (Gbit/s) | Max. PPS (10,000) | NIC Multi-Queue | Maximum NICs | GPUs     | GPU Connection | GPU Memory (GiB) | Virtualization Type | Hardware                                  |
   +================+=======+==============+====================================+===================+=================+==============+==========+================+==================+=====================+===========================================+
   | p2v.2xlarge.8  | 8     | 64           | 10/4                               | 50                | 4               | 4            | 1 x V100 | N/A            | 1 × 16 GiB       | KVM                 | CPU: Intel® Xeon® Skylake-SP Gold 6151 v5 |
   +----------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+----------------+------------------+---------------------+-------------------------------------------+
   | p2v.4xlarge.8  | 16    | 128          | 15/8                               | 100               | 8               | 8            | 2 x V100 | NVLink         | 2 × 16 GiB       | KVM                 |                                           |
   +----------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+----------------+------------------+---------------------+-------------------------------------------+
   | p2v.8xlarge.8  | 32    | 256          | 25/15                              | 200               | 16              | 8            | 4 x V100 | NVLink         | 4 × 16 GiB       | KVM                 |                                           |
   +----------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+----------------+------------------+---------------------+-------------------------------------------+
   | p2v.16xlarge.8 | 64    | 512          | 30/30                              | 400               | 32              | 8            | 8 x V100 | NVLink         | 8 × 16 GiB       | KVM                 |                                           |
   +----------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+----------------+------------------+---------------------+-------------------------------------------+

**P2v ECS Features**

-  CPU: Intel® Xeon® Scalable 6151 processors (3.0 GHz of base frequency and 3.4 GHz of turbo frequency)

-  Up to eight NVIDIA Tesla V100 GPUs on an ECS

-  NVIDIA CUDA parallel computing and common deep learning frameworks, such as TensorFlow, Caffe, PyTorch, and MXNet

-  15.7 TFLOPS of single-precision computing and 7.8 TFLOPS of double-precision computing

-  NVIDIA Tensor cores with 125 TFLOPS of single- and double-precision computing for deep learning

-  Up to 30 Gbit/s of network bandwidth on a single ECS

-  16 GiB of HBM2 GPU memory with a bandwidth of 900 Gbit/s

-  Comprehensive basic capabilities

   Networks are user-defined, subnets can be divided, and network access policies can be configured as needed. Mass storage is used, elastic capacity expansion as well as backup and restoration are supported to make data more secure. Auto Scaling allows you to add or reduce the number of ECSs quickly.

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

-  P2v ECSs support the following OSs:

   -  Windows Server 2019 Standard 64bit
   -  Windows Server 2016 Standard 64bit
   -  Windows Server 2012 R2 Standard 64bit
   -  Ubuntu Server 16.04 64bit
   -  CentOS 7.7 64bit
   -  EulerOS 2.5 64bit
   -  Oracle Linux 7.6 64bit

-  By default, P2v ECSs created using a Windows public image have the Tesla driver installed.
-  By default, P2v ECSs created using a Linux public image do not have a Tesla driver installed. After the ECS is created, install a driver on it for computing acceleration. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.
-  If a P2v ECS is created using a private image, make sure that the Tesla driver was installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.



.. _en-us_topic_0097289624__section5477185118234:

Computing-accelerated P2
------------------------

**Overview**

Compared with P1 ECSs, P2 ECSs use NVIDIA Tesla V100 GPUs, which have improved both single- and double-precision computing capabilities by 50% and offer 112 TFLOPS of deep learning.

**Specifications**



.. _en-us_topic_0097289624__table179717351266:

.. table:: **Table 4** P2 ECS specifications

   +--------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+------------------+------------------+---------------------+----------------------------------------+
   | Flavor       | vCPUs | Memory (GiB) | Maximum/Assured Bandwidth (Gbit/s) | Max. PPS (10,000) | NIC Multi-Queue | Maximum NICs | GPUs     | GPU Memory (GiB) | Local Disks      | Virtualization Type | Hardware                               |
   +==============+=======+==============+====================================+===================+=================+==============+==========+==================+==================+=====================+========================================+
   | p2.2xlarge.8 | 8     | 64           | 5/1.6                              | 35                | 2               | 12           | 1 x V100 | 1 x 16           | 1 × 800 GiB NVMe | KVM                 | CPU: Intel® Xeon® Processor E5-2690 v4 |
   +--------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+------------------+------------------+---------------------+----------------------------------------+
   | p2.4xlarge.8 | 16    | 128          | 8/3.2                              | 70                | 4               | 12           | 2 x V100 | 2 x 16           | 2 × 800 GiB NVMe | KVM                 |                                        |
   +--------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+------------------+------------------+---------------------+----------------------------------------+
   | p2.8xlarge.8 | 32    | 256          | 10/6.5                             | 140               | 8               | 12           | 4 x V100 | 4 x 16           | 4 × 800 GiB NVMe | KVM                 |                                        |
   +--------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+------------------+------------------+---------------------+----------------------------------------+

**P2 ECS Features**

-  CPU: Intel® Xeon® Processor E5-2690 v4 (2.6 GHz)

-  NVIDIA Tesla V100 GPUs

-  GPU hardware passthrough

-  14 TFLOPS of single-precision computing, 7 TFLOPS of double-precision computing, and 112 TFLOPS of deep learning

-  Maximum network bandwidth of 12 Gbit/s

-  16 GiB of HBM2 GPU memory with a bandwidth of 900 Gbit/s

-  800 GiB NVMe SSDs for temporary local storage

-  Comprehensive basic capabilities

   Networks are user-defined, subnets can be divided, and network access policies can be configured as needed. Mass storage is used, elastic capacity expansion as well as backup and restoration are supported to make data more secure. Auto Scaling allows you to add or reduce the number of ECSs quickly.

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

      Data may be lost on the local NVMe SSDs attached to P2 ECSs due to, for example, a disk or host fault. Therefore, you are suggested to store only temporary data in local NVMe SSDs. If you store important data in such a disk, securely back up the data.

-  P2 ECSs do not support specifications modification.

-  P2 ECSs support the following OSs:

   Ubuntu Server 16.04 64bit

-  After you delete a P2 ECS, the data stored in local NVMe SSDs is automatically cleared.

-  By default, P2 ECSs created using a Linux public image do not have a Tesla driver installed. After the ECS is created, install a driver on it for computing acceleration. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.

-  If a P2 ECS is created using a private image, make sure that the Tesla driver was installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.



.. _en-us_topic_0097289624__section1124594913391:

Computing-accelerated P1
------------------------

**Overview**

P1 ECSs use NVIDIA Tesla P100 GPUs and provide flexibility, high performance, and cost-effectiveness. These ECSs support GPU Direct for direct communication between GPUs, improving data transmission efficiency. P1 ECSs provide outstanding general computing capabilities and have strengths in deep learning, graphic databases, high-performance databases, Computational Fluid Dynamics (CFD), computing finance, seismic analysis, molecular modeling, and genomics. They are designed for scientific computing.

**Specifications**



.. _en-us_topic_0097289624__table1888295812406:

.. table:: **Table 5** P1 ECS specifications

   +--------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+------------------+-------------------+---------------------+----------------------------------------+
   | Flavor       | vCPUs | Memory (GiB) | Maximum/Assured Bandwidth (Gbit/s) | Max. PPS (10,000) | NIC Multi-Queue | Maximum NICs | GPUs     | GPU Memory (GiB) | Local Disks (GiB) | Virtualization Type | Hardware                               |
   +==============+=======+==============+====================================+===================+=================+==============+==========+==================+===================+=====================+========================================+
   | p1.2xlarge.8 | 8     | 64           | 5/1.6                              | 35                | 2               | 12           | 1 x P100 | 1 x 16           | 1×800             | KVM                 | CPU: Intel® Xeon® Processor E5-2690 v4 |
   +--------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+------------------+-------------------+---------------------+----------------------------------------+
   | p1.4xlarge.8 | 16    | 128          | 8/3.2                              | 70                | 4               | 12           | 2 x P100 | 2 x 16           | 2×800             | KVM                 |                                        |
   +--------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+------------------+-------------------+---------------------+----------------------------------------+
   | p1.8xlarge.8 | 32    | 256          | 10/6.5                             | 140               | 8               | 12           | 4 x P100 | 4 x 16           | 4×800             | KVM                 |                                        |
   +--------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+----------+------------------+-------------------+---------------------+----------------------------------------+

**P1 ECS Features**

-  CPU: Intel® Xeon® Processor E5-2690 v4 (2.6 GHz)

-  Up to four NVIDIA Tesla P100 GPUs on a P1 ECS (If eight P100 GPUs are required on an instance, use BMS.)

-  GPU hardware passthrough

-  9.3 TFLOPS of single-precision computing and 4.7 TFLOPS of double-precision computing

-  Maximum network bandwidth of 10 Gbit/s

-  16 GiB of HBM2 GPU memory with a bandwidth of 732 Gbit/s

-  800 GiB NVMe SSDs for temporary local storage

-  Comprehensive basic capabilities

   Networks are user-defined, subnets can be divided, and network access policies can be configured as needed. Mass storage is used, elastic capacity expansion as well as backup and restoration are supported to make data more secure. Auto Scaling allows you to add or reduce the number of ECSs quickly.

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
-  P1 ECSs do not support specifications modification.
-  P1 ECSs support the following OSs:

   -  Windows Server 2012 R2 Standard 64bit
   -  Ubuntu Server 16.04 64bit
   -  CentOS 7.4 64bit
   -  Debian 9.0 64bit

-  After you delete a P1 ECS, the data stored in local NVMe SSDs is automatically cleared.
-  By default, P1 ECSs created using a Windows public image have the Tesla driver installed.
-  By default, P1 ECSs created using a Linux public image do not have a Tesla driver installed. After the ECS is created, install a driver on it for computing acceleration. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.
-  If a P1 ECS is created using a private image, make sure that the Tesla driver was installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.



.. _en-us_topic_0097289624__section1846114713182:

Inference-accelerated PI2
-------------------------

**Overview**

PI2 ECSs use NVIDIA Tesla T4 GPUs dedicated for real-time AI inference. These ECSs use the T4 INT8 calculator for up to 130 TOPS of INT8 computing. The PI2 ECSs can also be used for light-load training.

**Specifications**



.. _en-us_topic_0097289624__table029414915519:

.. table:: **Table 6** PI2 ECS specifications

   +---------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+--------+------------------+-------------+---------------------+----------------------------------------------------------------------------------+
   | Flavor        | vCPUs | Memory (GiB) | Maximum/Assured Bandwidth (Gbit/s) | Max. PPS (10,000) | NIC Multi-Queue | Maximum NICs | GPUs   | GPU Memory (GiB) | Local Disks | Virtualization Type | Hardware                                                                         |
   +===============+=======+==============+====================================+===================+=================+==============+========+==================+=============+=====================+==================================================================================+
   | pi2.2xlarge.4 | 8     | 32           | 10/4                               | 50                | 4               | 4            | 1 x T4 | 1 × 16 GiB       | N/A         | KVM                 | CPU: Intel® Xeon® Skylake 6151 3.0 GHz or Intel® Xeon® Cascade Lake 6278 2.6 GHz |
   +---------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+--------+------------------+-------------+---------------------+----------------------------------------------------------------------------------+
   | pi2.4xlarge.4 | 16    | 64           | 15/8                               | 100               | 8               | 8            | 2 x T4 | 2 × 16 GiB       | N/A         | KVM                 |                                                                                  |
   +---------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+--------+------------------+-------------+---------------------+----------------------------------------------------------------------------------+
   | pi2.8xlarge.4 | 32    | 128          | 25/15                              | 200               | 16              | 8            | 4 x T4 | 4 × 16 GiB       | N/A         | KVM                 |                                                                                  |
   +---------------+-------+--------------+------------------------------------+-------------------+-----------------+--------------+--------+------------------+-------------+---------------------+----------------------------------------------------------------------------------+

**PI2 ECS Features**

-  CPU: 2nd Generation Intel® Xeon® Scalable 6278 processors (2.6 GHz of base frequency and 3.5 GHz of turbo frequency), or Intel® Xeon® Scalable 6151 processors (3.0 GHz of base frequency and 3.4 GHz of turbo frequency)
-  Up to four NVIDIA Tesla T4 GPUs on an ECS
-  GPU hardware passthrough
-  Up to 8.1 TFLOPS of single-precision computing on a single GPU
-  Up to 130 TOPS of INT8 computing on a single GPU
-  16 GiB of GDDR6 GPU memory with a bandwidth of 320 GiB/s on a single GPU
-  One built-in NVENC and two NVDEC GPUs

**Supported Common Software**

PI2 ECSs are used in GPU-based inference computing scenarios, such as image recognition, speech recognition, and natural language processing. The PI2 ECSs can also be used for light-load training.

PI2 ECSs support the following commonly used software:

-  Deep learning frameworks, such as TensorFlow, Caffe, PyTorch, and MXNet

**Notes**

-  After a PI2 ECS is stopped, basic resources including vCPUs, memory, and images are not billed, but its system disk is billed based on the disk capacity. If other products, such as EVS disks, EIP, and bandwidth are associated with the ECS, these products are billed separately.

   .. note::

      Resources are released after a PI2 ECS is stopped. If desired resources are insufficient when the PI2 ECS is started after being stopped, starting the ECS might fail. Therefore, if you need to use a PI2 ECS for a long time, keep the ECS running.

-  PI2 ECSs support the following OSs:

   -  Windows Server 2019 Standard 64bit
   -  Windows Server 2016 Standard 64bit
   -  Windows Server 2012 R2 Standard 64bit
   -  Ubuntu Server 16.04 64bit
   -  CentOS 7.8 64bit

-  PI2 ECSs support automatic recovery when the hosts accommodating such ECSs become faulty.
-  By default, PI2 ECSs created using a Windows public image have the Tesla driver installed.
-  By default, PI2 ECSs created using a Linux public image do not have a Tesla driver installed. After the ECS is created, install a driver on it for computing acceleration. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.
-  If a PI2 ECS is created using a private image, make sure that the Tesla driver was installed during the private image creation. If not, install the driver for computing acceleration after the ECS is created. For details, see :ref:`Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <en-us_topic_0149470468>`.
