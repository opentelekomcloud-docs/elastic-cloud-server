Overview
========

This document describes how to call the APIs of Elastic Cloud Server (ECS) to use ECS functions. The concepts related to ECS help you quickly learn this service.

ECS
---

An ECS is a cloud server that allows on-demand allocation and elastic scaling to create an efficient, reliable, and secure computing environment. This ensures stable and uninterrupted operation of services.

Basic Concepts
--------------

-  Region

   A region is a geographic area where resources used by ECSs are located.

-  Availability zone (AZ)

   An AZ is a physical location where power and networks are physically isolated within a region. Each AZ provides cost-effective and low-latency network connections that are unaffected by faults that may occur in other AZs. Each region contains one or more AZs. AZs are physically isolated but interconnected through an internal network.

-  Project

   A project groups and isolates OpenStack resources, such as computing, storage, and network resources. A project can be either a department or a project team.

   A tenant can create multiple projects.

-  Flavor

   Specifies hardware resources required for running an ECS, including the vCPUs, memory, and storage capacities.

-  Elastic Volume Service (EVS)

   Provides persistent block storage for computing services, such as ECS and Bare Metal Server (BMS). With advanced data redundancy and cache acceleration capabilities, EVS offers high availability and durability with a low latency. Users can format an EVS disk, create a file system on it, and store data persistently.

-  Image

   An image is an ECS template that contains an OS and may also contain application software (such as database software) and software configuration.

   Images can be public or private. Public images are provided by the system by default, and private images are manually created by users. Users can use any type of image to create an ECS. They can also create a private image using an existing ECS or external image. This provides users with a simple way to create ECSs that comply with their service requirements.

-  Virtual Private Cloud (VPC)

   VPC allows users to create private, isolated virtual networks. Users can define IP address segments, subnets, and security groups, assign EIPs, and allocate bandwidth in a VPC.
