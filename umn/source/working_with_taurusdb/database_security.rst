:original_name: gaussdb_03_0082.html

.. _gaussdb_03_0082:

Database Security
=================

Password Strength Requirements
------------------------------

TaurusDB has a password security policy for newly created database users. Passwords must:

-  Consist of at least eight characters.
-  Contain at least three types of the following: uppercase letters, lowercase letters, digits, and special characters.

When you create DB instances, your password strength is checked. You can modify the password strength as user **root**. For security reasons, you are advised to use a password that is at least as strong as the default one.

Account Description
-------------------

To provide O&M services, the system automatically creates system accounts when you create DB instances. These system accounts are unavailable to you.

.. important::

   Deleting, renaming, and changing passwords or permissions for these accounts will cause the DB instance to run abnormally. Exercise caution when performing these operations.

-  rdsAdmin: indicates the management account, which has the highest superuser permission and is used to query and modify DB instance information, rectify faults, migrate data, and restore data.
-  rdsRepl: indicates the replication account, which is used to synchronize data from the primary node to read replicas.
-  rdsBackup: indicates the backup account, which is used for background backup.
-  rdsMetric: indicates the metric monitoring account, which is used by watchdog to collect database status data.
