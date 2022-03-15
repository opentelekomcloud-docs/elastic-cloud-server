Is an ECS Hostname with Suffix .novalocal Normal?
=================================================

Symptom
-------

Hostnames of ECSs created based on some types of images have the suffix **.novalocal**, whereas others do not.

For example, the hostname is set to **abc** during ECS creation. `Table 1 <#enustopic0094874138table168595206502>`__ lists the hostnames (obtained by running the **hostname** command) of ECSs created using different images and those displayed after the ECSs are restarted.



.. _ENUSTOPIC0094874138table168595206502:

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

If you do not need suffix **.novalocal** in obtained hostnames, change the hostnames. For details, see `How Can a Changed Static Hostname Take Effect Permanently? <../../faqs/ecs_management/how_can_a_changed_static_hostname_take_effect_permanently.html>`__


