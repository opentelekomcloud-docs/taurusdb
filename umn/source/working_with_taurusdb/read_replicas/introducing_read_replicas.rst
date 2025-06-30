:original_name: gaussdb_03_0110.html

.. _gaussdb_03_0110:

Introducing Read Replicas
=========================

Introduction
------------

TaurusDB instances support read replicas.

In read-intensive scenarios, a primary node may be unable to handle the read pressure and service performance may be affected. To offload read pressure on the primary node, you can create one or more read replicas in the same region as the primary node. These read replicas can process a large number of read requests and increase application throughput. You need to separately configure connection addresses for the primary node and each read replica on your applications so that all read requests can be sent to read replicas and write requests to the primary node.

Functions
---------

-  Specifications of read replicas are the same as those of the primary node.

-  You do not need to maintain accounts and databases for read replicas. They are synchronized from the primary node.

-  Read replicas support system performance monitoring.

   TaurusDB provides nearly 20 metrics, including the CPU usage, memory usage, storage space usage, and database connections. You can view these metrics to understand the load of DB instances.

Constraints
-----------

-  A DB instance contains up to 15 read replicas.
-  Read replicas do not support backup settings or temporary backups.
-  Read replicas do not support instance creation at any point of time or restoration from backup files to the original instance to overwrite data.
-  Data cannot be migrated to read replicas.
-  Read replicas do not support database creation and deletion.
-  Read replicas do not support account creation. You can create accounts only on the primary node.
