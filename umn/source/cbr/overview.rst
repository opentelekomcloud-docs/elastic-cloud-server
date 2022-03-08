Overview
========

What Is CBR?
------------

Cloud Backup and Recovery (CBR) enables you to back up cloud servers and disks with ease. In case of a virus attack, accidental deletion, or software or hardware fault, you can restore data to any point in the past when the data was backed up.

CBR protects your services by ensuring the security and consistency of your data.

What Are the Differences Between Backup, Snapshot, and Image?
-------------------------------------------------------------

You can use the cloud server backup function to create ECSs and the cloud disk backup function to create EVS disks.

An image can be a system disk image, data disk image, or full-ECS image.



.. _EN-US_TOPIC_0000001128445638__table178211453578:

+-----------------------------+-----------------------------+-----------------------------+-----------------------------+
| Backup Type                 | Backup Object               | Application Scenario        | Differences and Advantages  |
+=============================+=============================+=============================+=============================+
| Cloud server backup         | All disks (system and data  | -  **Hacker attacks and     | All disks on an ECS are     |
|                             | disks) on an ECS            |    viruses**                | backed up at the same time, |
|                             |                             |                             | ensuring data consistency.  |
|                             |                             |    You can use cloud server |                             |
|                             |                             |    backup to restore data   | In addition, you can        |
|                             |                             |    to the latest backup     | configure backup policies   |
|                             |                             |    point at which the ECS   | for automatic backup.       |
|                             |                             |    has not been affected by |                             |
|                             |                             |    hacker attacks and       |                             |
|                             |                             |    viruses.                 |                             |
|                             |                             |                             |                             |
|                             |                             | -  **Accidental data        |                             |
|                             |                             |    deletion**               |                             |
|                             |                             |                             |                             |
|                             |                             |    You can use cloud server |                             |
|                             |                             |    backup to restore data   |                             |
|                             |                             |    to the backup point      |                             |
|                             |                             |    prior to the accidental  |                             |
|                             |                             |    deletion.                |                             |
|                             |                             |                             |                             |
|                             |                             | -  **Application update     |                             |
|                             |                             |    errors**                 |                             |
|                             |                             |                             |                             |
|                             |                             |    You can use cloud server |                             |
|                             |                             |    backup to restore data   |                             |
|                             |                             |    to the backup point      |                             |
|                             |                             |    prior to the application |                             |
|                             |                             |    update.                  |                             |
|                             |                             |                             |                             |
|                             |                             | -  **System breakdown**     |                             |
|                             |                             |                             |                             |
|                             |                             |    You can use cloud server |                             |
|                             |                             |    backup to restore an ECS |                             |
|                             |                             |    to the backup point in   |                             |
|                             |                             |    time prior to system     |                             |
|                             |                             |    breakdown.               |                             |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+
| Cloud disk backup           | One or more specified disks | -  **Only data disks need   | Backup data is stored in    |
|                             | (system or data disks)      |    to be backed up, because | OBS, instead of disks. This |
|                             |                             |    the system disk does not | ensures data restoration    |
|                             |                             |    contain users'           | upon disk data loss or      |
|                             |                             |    application data.**      | corruption.                 |
|                             |                             |                             |                             |
|                             |                             |    You can use cloud disk   | Backup cost is reduced      |
|                             |                             |    backup to back up and    | without compromising data   |
|                             |                             |    restore data if an EVS   | security.                   |
|                             |                             |    disk is faulty or        |                             |
|                             |                             |    encounters a logical     |                             |
|                             |                             |    error, for example,      |                             |
|                             |                             |    accidental deletion,     |                             |
|                             |                             |    hacker attacks, and      |                             |
|                             |                             |    virus infection.         |                             |
|                             |                             |                             |                             |
|                             |                             | -  **Use backups as         |                             |
|                             |                             |    baseline data.**         |                             |
|                             |                             |                             |                             |
|                             |                             |    After a backup policy    |                             |
|                             |                             |    has been set, the EVS    |                             |
|                             |                             |    disk data can be         |                             |
|                             |                             |    automatically backed up  |                             |
|                             |                             |    based on the policy. You |                             |
|                             |                             |    can use the backups      |                             |
|                             |                             |    created on a timely      |                             |
|                             |                             |    basis as the baseline    |                             |
|                             |                             |    data to create new EVS   |                             |
|                             |                             |    disks or to restore the  |                             |
|                             |                             |    backup data to EVS       |                             |
|                             |                             |    disks.                   |                             |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+
| Snapshot                    | One or more specified disks | -  **Routine data backup**  | -  The snapshot data is     |
|                             | (system or data disks)      |                             |    stored with the disk     |
|                             |                             |    You can create snapshots |    data to facilitate rapid |
|                             |                             |    for disks on a timely    |    data back up and         |
|                             |                             |    basis and use snapshots  |    restoration.             |
|                             |                             |    to recover your data in  | -  You can create snapshots |
|                             |                             |    case that data loss or   |    to rapidly save disk     |
|                             |                             |    data inconsistency       |    data as it was at        |
|                             |                             |    occurred due to          |    specified points in      |
|                             |                             |    misoperations, viruses,  |    time. You can also use   |
|                             |                             |    or attacks.              |    snapshots to create new  |
|                             |                             |                             |    disks so that the        |
|                             |                             | -  **Rapid data             |    created disks will       |
|                             |                             |    restoration**            |    contain the snapshot     |
|                             |                             |                             |    data in the beginning.   |
|                             |                             |    You can create a         |                             |
|                             |                             |    snapshot or multiple     |                             |
|                             |                             |    snapshots before an      |                             |
|                             |                             |    application software     |                             |
|                             |                             |    upgrade or a service     |                             |
|                             |                             |    data migration. If an    |                             |
|                             |                             |    exception occurs during  |                             |
|                             |                             |    the upgrade or           |                             |
|                             |                             |    migration, service data  |                             |
|                             |                             |    can be rapidly restored  |                             |
|                             |                             |    to the time point when   |                             |
|                             |                             |    the snapshot was         |                             |
|                             |                             |    created.                 |                             |
|                             |                             |                             |                             |
|                             |                             |    For example, if ECS A    |                             |
|                             |                             |    cannot be started due to |                             |
|                             |                             |    a fault occurred in      |                             |
|                             |                             |    system disk A, you can   |                             |
|                             |                             |    create disk B using an   |                             |
|                             |                             |    existing snapshot of     |                             |
|                             |                             |    system disk A and attach |                             |
|                             |                             |    disk B to a properly     |                             |
|                             |                             |    running ECS, for example |                             |
|                             |                             |    ECS B. In this case, ECS |                             |
|                             |                             |    B can read the data of   |                             |
|                             |                             |    system disk A from the   |                             |
|                             |                             |    disk B.                  |                             |
|                             |                             |                             |                             |
|                             |                             | -  **Rapid deployment of    |                             |
|                             |                             |    multiple services**      |                             |
|                             |                             |                             |                             |
|                             |                             |    You can use a snapshot   |                             |
|                             |                             |    to create multiple EVS   |                             |
|                             |                             |    disks containing the     |                             |
|                             |                             |    same initial data, and   |                             |
|                             |                             |    these disks can be used  |                             |
|                             |                             |    as data resources for    |                             |
|                             |                             |    various services,        |                             |
|                             |                             |                             |                             |
|                             |                             |    for example data mining, |                             |
|                             |                             |    report query, and        |                             |
|                             |                             |    development and testing. |                             |
|                             |                             |    This method protects the |                             |
|                             |                             |    initial data and creates |                             |
|                             |                             |    disks rapidly, meeting   |                             |
|                             |                             |    the diversified service  |                             |
|                             |                             |    data requirements.       |                             |
|                             |                             |                             |                             |
|                             |                             | NOTE:                       |                             |
|                             |                             |                             |                             |
|                             |                             | -  A snapshot can be rolled |                             |
|                             |                             |    back only to its source  |                             |
|                             |                             |    disk. Rollback to        |                             |
|                             |                             |    another disk is not      |                             |
|                             |                             |    possible.                |                             |
|                             |                             | -  If you have reinstalled  |                             |
|                             |                             |    or changed the ECS OS,   |                             |
|                             |                             |    snapshots of the system  |                             |
|                             |                             |    disk are automatically   |                             |
|                             |                             |    deleted. Snapshots of    |                             |
|                             |                             |    the data disks can be    |                             |
|                             |                             |    used as usual.           |                             |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+
| System disk image           | System disk                 | -  **Rapid system           | A system disk image can     |
|                             |                             |    recovery**               | help an ECS with OS damaged |
|                             |                             |                             | to quickly change its OS.   |
|                             |                             |    You can create a system  |                             |
|                             |                             |    disk image for the       |                             |
|                             |                             |    system disk of an ECS    |                             |
|                             |                             |    before OS change,        |                             |
|                             |                             |    application software     |                             |
|                             |                             |    upgrade, or service data |                             |
|                             |                             |    migration. If an         |                             |
|                             |                             |    exception occurs during  |                             |
|                             |                             |    the migration, you can   |                             |
|                             |                             |    use the system disk      |                             |
|                             |                             |    image to change ECS OS   |                             |
|                             |                             |    or create a new ECS.     |                             |
|                             |                             |                             |                             |
|                             |                             | -  **Rapid deployment of    |                             |
|                             |                             |    multiple services**      |                             |
|                             |                             |                             |                             |
|                             |                             |    You can use a system     |                             |
|                             |                             |    disk image to quickly    |                             |
|                             |                             |    create multiple ECSs     |                             |
|                             |                             |    with the same OS,        |                             |
|                             |                             |    thereby quickly          |                             |
|                             |                             |    deploying services these |                             |
|                             |                             |    ECSs.                    |                             |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+
| Data disk image             | Specific data disk          | **Rapid data replication**  | A data disk image can       |
|                             |                             |                             | replicate all data on a     |
|                             |                             | You can use a data disk     | disk and create new EVS     |
|                             |                             | image to create multiple    | disks. The EVS disks can be |
|                             |                             | EVS disks containing the    | attached to other ECSs for  |
|                             |                             | same initial data, and then | data replication and        |
|                             |                             | attach these disks to ECSs  | sharing.                    |
|                             |                             | to provide data resources   |                             |
|                             |                             | for multiple services.      |                             |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+
| Full-ECS image              | All disks (system and data  | -  **Rapid system           | A full-ECS image            |
|                             | disks) on an ECS            |    recovery**               | facilitates service         |
|                             |                             |                             | migration.                  |
|                             |                             |    You can create a         |                             |
|                             |                             |    full-ECS image for the   |                             |
|                             |                             |    system disk and data     |                             |
|                             |                             |    disks of an ECS before   |                             |
|                             |                             |    OS change, application   |                             |
|                             |                             |    software upgrade, or     |                             |
|                             |                             |    service data migration.  |                             |
|                             |                             |    If an exception occurs   |                             |
|                             |                             |    during the migration,    |                             |
|                             |                             |    you can use the full-ECS |                             |
|                             |                             |    image to change ECS OS   |                             |
|                             |                             |    or create a new ECS.     |                             |
|                             |                             |                             |                             |
|                             |                             | -  **Rapid deployment of    |                             |
|                             |                             |    multiple services**      |                             |
|                             |                             |                             |                             |
|                             |                             |    You can use a full-ECS   |                             |
|                             |                             |    image to quickly create  |                             |
|                             |                             |    multiple ECSs with the   |                             |
|                             |                             |    same OS and data,        |                             |
|                             |                             |    thereby quickly          |                             |
|                             |                             |    deploying services these |                             |
|                             |                             |    ECSs.                    |                             |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+

CBR Architecture
----------------

CBR consists of backups, vaults, and policies.

-  **Backup**

   A backup is a copy of a particular chunk of data and is usually stored elsewhere so that it may be used to restore the original data in the event of data loss. CBR supports the following backup types:

   -  Cloud server backup: This type of backup uses the consistency snapshot technology for disks to protect data of ECSs and BMSs. The backups of servers without deployed databases are common server backups, and those of servers with deployed databases are application-consistent backups.
   -  Cloud disk backup: This type of backup provides snapshot-based data protection for EVS disks.

-  **Vault**

   CBR uses vaults to store backups. Before creating a backup, you need to create at least one vault and associate the resource you want to back up with the vault. Then the backup of the resource is stored in the associated vault.

   Vaults can be classified into two types: backup vaults and replication vaults. Backup vaults store backups, whereas replication vaults store replicas of backups.

   The backups of different types of resources must be stored in different types of vaults.

-  **Policy**

   Policies are divided into backup policies and replication policies.

   -  Backup policies: To perform automatic backups, configure a backup policy by setting the execution times of backup tasks, the backup cycle, and retention rules, and then apply the policy to a vault.
   -  Replication policies: To automatically replicate backups or vaults, configure a replication policy by setting the execution times of replication tasks, the replication cycle, and retention rules, and then apply the policy to a vault. Replicas of backups must be stored in replication vaults.

Backup Mechanism
----------------

A full backup is performed only for the first backup and backs up all used data blocks.

For example, if the size of a disk is 100 GB and the used space is 40 GB, the 40 GB of data is backed up.

An incremental backup backs up only the data changed since the last backup, which is storage- and time-efficient.

When a backup is deleted, only the data blocks that are not depended on by other backups are deleted, so that other backups can still be used for restoration. Both a full backup and an incremental backup can restore data to the state at a given backup point in time.

When creating a backup of a disk, CBR also creates a snapshot for it. Every time a new disk backup is created, CBR deletes the old snapshot and keeps only the latest snapshot.

CBR stores backup data in OBS, enhancing backup data security.

Backup Options
--------------

CBR supports one-off backup and periodic backup. A one-off backup task is manually created by users and is executed only once. Periodic backup tasks are automatically executed based on a user-defined backup policy.



.. _EN-US_TOPIC_0000001128445638__table427813140219:

.. table:: **Table 1** One-off backup and periodic backup

   +------------------------+---------------------------------------------+---------------------------------------------+
   | Item                   | One-Off Backup                              | Periodic Backup                             |
   +========================+=============================================+=============================================+
   | Backup policy          | Not required                                | Required                                    |
   +------------------------+---------------------------------------------+---------------------------------------------+
   | Number of backup tasks | One manual backup task                      | Periodic tasks driven by a backup policy    |
   +------------------------+---------------------------------------------+---------------------------------------------+
   | Backup name            | User-defined backup name, which is          | System-assigned backup name, which is       |
   |                        | **manualbk\_**\ *xxxx* by default           | **autobk\_**\ *xxxx* by default             |
   +------------------------+---------------------------------------------+---------------------------------------------+
   | Backup mode            | Full backup for the first time and          | Full backup for the first time and          |
   |                        | incremental backup subsequently, by default | incremental backup subsequently, by default |
   +------------------------+---------------------------------------------+---------------------------------------------+
   | Application scenario   | Executed before patching or upgrading the   | Executed for routine maintenance of a       |
   |                        | OS or upgrading an application on a         | resource. The latest backup can be used for |
   |                        | resource. A one-off backup can be used to   | restoration if an unexpected failure or     |
   |                        | restore the resource to the original state  | data loss occurs.                           |
   |                        | if the patching or upgrading fails.         |                                             |
   +------------------------+---------------------------------------------+---------------------------------------------+

