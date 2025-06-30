:original_name: gaussdb_02_0011.html

.. _gaussdb_02_0011:

Introducing Read/Write Splitting
================================

Read/write splitting enables read and write requests to be automatically routed through a proxy address. You can create a proxy instance by referring to :ref:`Creating a Proxy Instance <gaussdb_11_0017>` after read replicas are created. Thanks to the IP address of the proxy instance, write requests are automatically routed to the primary node and read requests are routed to read replicas and the primary node by user-defined weights.

Constraints
-----------

-  Read/write splitting can be enabled only when at least one read replica is created.
-  After read/write splitting is enabled, the database port, private IP address, and security group cannot be changed.
-  Proxy instances cannot be created if transaction isolation is READ-UNCOMMITTED.
-  A maximum of four proxy instances can be created for a TaurusDB instance.
-  Proxy instances do not support reads from and writes to any column containing more than 16 MB of data in a table.

-  After read/write splitting is enabled, both the database port and the security group of the primary node and read replicas are changed.
-  Read/write splitting does not support SSL encryption.
-  Read/write splitting does not support the compression protocol.
-  If multi-statements are executed, all subsequent requests will be routed to the primary node. To restore the read/write splitting function, you need to disconnect the connection between applications and the read/write splitting address and establish a connection again.
-  The port number of a proxy instance is independent of that of a DB instance. Changing the port number of the DB instance does not change that of the proxy instance. The default port number of a proxy instance is 3306.

Scenarios
---------

When enabling read/write splitting for an instance, you need to select the nodes (including the primary node and read replicas) to be associated to the proxy instances.

-  Different applications can connect to the instance through the IP addresses of different proxy instances. Read requests are routed to the proxy instances that applications connect to. You can also add nodes to or remove nodes from proxy instances.

-  A primary node or read replica can be added to multiple proxy instances at the same time, and then is assigned different read weights. For details about how to assign weights, :ref:`Assigning Read Weights <gaussdb_11_0018>`.

-  In the read/write mode, all write requests are routed to the primary node, and read requests are routed to each node based on the read weights.
-  In the read-only mode, only read requests can be routed to read replicas based on the read weights. Even if the primary node is assigned with a read weight, the weight does not take effect.
