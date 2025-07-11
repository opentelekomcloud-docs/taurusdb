:original_name: gaussdb_03_0069.html

.. _gaussdb_03_0069:

Backup Space and Billing
========================

Category
--------

-  Full backup: All data is backed up even if no data is updated since the last backup.
-  Incremental backup: The system automatically backs up data that has changed since the last automated backup or incremental backup in logs every 5 minutes. The logs can be used to restore data to a point in time.
-  Differential backup: The system backs up data that has changed since the most recent full backup or differential backup in to physical files. Physical files cannot be used for log replay.
-  Billed space: backup space that you are billed for.
-  Logical space: space occupied by full backups.
-  Physical space: the amount of data backed up to OBS.

   .. note::

      After you create a DB instance, the logical space is the same as the physical space. When a backup starts in a backup chain, the physical space stores the data of the first full backup and subsequent differential backups.

Backup Space Calculation Methods
--------------------------------

There is a default backup chain (where there are seven backups). The first automated backup is a full backup, and subsequent automated backups are differential backups.

In a backup chain, the backup space is released only after all full backups and differential backups are deleted.

The hourly billed space is calculated as follows:

-  Logical space: Total size of the logical space - Logical size of the expired backup file
-  Physical space: Size of the first full backup file + Total size of subsequent differential backup files

Billed space = Min (Logical space, Physical space)

Example
-------

A backup chain contains seven backups by default. There are 11 backups shown in the following figure. The 1st backup to the 7th belong to one backup chain and the 8th to the 11th belong to the other backup chain.


.. figure:: /_static/images/en-us_image_0000001896928157.png
   :alt: **Figure 1** Backup example

   **Figure 1** Backup example

If the logical space is 1,000 MB each time, the physical space for the 1st backup is 1,000 MB. If the incremental data size is 100 MB each time, the physical space for the 2nd backup to 7th is 100 MB.

A backup chain contains seven backups by default. The physical space for the 8th backup is 1,000 MB because it represents a new backup chain.

Billed space includes the space of the two chains in the example.

Suppose that after the 11th backup was created, and the 1st, 2nd and 3rd backups expired and were automatically deleted. The size of each space is calculated as follows:

-  Total size of the logical space for the 11th backup = 1,000 MB x 11 - 3,000 MB = 8,000 MB

-  Physical space: the amount of data backed up to OBS, that is, the sum of the physical space on the two chains.

   Physical space = 1,000 MB + 100 MB x 6 + 1,000 MB + 100 MB x 3 = 2,900 MB

-  Total billed space = Min (8,000 MB, 2,900 MB) = 2,900 MB
