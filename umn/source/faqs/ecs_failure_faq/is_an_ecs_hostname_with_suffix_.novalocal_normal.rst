:original_name: en-us_topic_0094874138.html

.. _en-us_topic_0094874138:

Is an ECS Hostname with Suffix .novalocal Normal?
=================================================

Symptom
-------

Hostnames of ECSs created based on some types of images have the suffix **.novalocal**, whereas others do not.

For example, the hostname is set to **abc** during ECS creation. :ref:`Table 1 <en-us_topic_0094874138__table168595206502>` lists the hostnames (obtained by running the **hostname** command) of ECSs created using different images and those displayed after the ECSs are restarted.

.. _en-us_topic_0094874138__table168595206502:

.. table:: **Table 1** Hostnames of ECSs created from different images

   ========== =========================== ==========================
   Image      Hostname Before ECS Restart Hostname After ECS Restart
   ========== =========================== ==========================
   CentOS 6.8 abc                         abc.novalocal
   CentOS 7.3 abc.novalocal               abc.novalocal
   Ubuntu 16  abc                         abc
   ========== =========================== ==========================

Troubleshooting
---------------

This is a normal phenomenon.

The static hostname of a Linux ECS is user defined and injected using Cloud-Init during the ECS creation. According to the test results, Cloud-Init adapts to OSs differently. As a result, hostnames of some ECSs have suffix **.novalocal**, whereas others do not.

If you do not want to have the obtained hostnames contain suffix **.novalocal**, change the hostnames by referring to :ref:`How Can a Changed Static Hostname Take Effect Permanently? <en-us_topic_0050735736>`
