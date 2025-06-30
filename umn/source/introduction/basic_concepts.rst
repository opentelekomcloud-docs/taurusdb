:original_name: gaussdb_01_0001.html

.. _gaussdb_01_0001:

Basic Concepts
==============

Understanding the following concepts helps you better use TaurusDB:

-  Cluster: TaurusDB uses the cluster architecture, with one primary node and multiple read replicas.

-  Region: A region is a physical data center. Generally, TaurusDB instances and ECSs must be located in the same region for high access performance.

-  Availability zone (AZ): An AZ contains one or multiple physical data centers. Each AZ has independent cooling, fire extinguishing, moisture-proof, and electricity facilities. Within an AZ, computing, network, storage, and other resources are logically divided into multiple instances. An AZ is a geographic location with independent power supply and network facilities in a region.

   AZs are physically isolated but interconnected over an intranet. Each AZ provides cost-effective and low-latency network connections that are unaffected by faults that may occur in other AZs. As a result, provisioning TaurusDB instances in separate AZs protects your applications against local faults that occur in a single location. AZs within the same region have no functional differences.

-  Instance class: resource configuration of each node, for example, 16 vCPUs and 64 GB.
