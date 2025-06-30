:original_name: gaussdb_11_0018.html

.. _gaussdb_11_0018:

Assigning Read Weights
======================

After read/write splitting is enabled, you can assign read weights as required.

Description
-----------

-  After read/write splitting is enabled, you can assign read weights for the primary node and read replicas.
-  The default read weight of the primary node is 0. The higher read weight the primary node is assigned, the more read requests it can process.
-  When the read weights of all nodes are 0, services are not affected. In this case, the primary node processes all read and write requests by default.
-  The weight of a read replica ranges from 0 to 1000.
-  For details about how to assign read weights, see :ref:`Weight Assignment Rules <gaussdb_11_0018__en-us_topic_0200110324_section18253121664211>`.

.. _gaussdb_11_0018__en-us_topic_0200110324_section18253121664211:

Weight Assignment Rules
-----------------------

When the system automatically assigns read weights to read replicas, the weight values are fixed.

.. note::

   The default weight equals to the number of vCPUs multiplied by 50. The weight ranges from 100 to 1000.

   For example:

   -  If the number of CPUs is 8, the weight is 400 (8 x 50 = 400).
   -  If the number of CPUs is 16, the weight is 800 (16 x 50 = 800).
   -  If the number of vCPUs is 32, the weight is 1000 (32 x 50 = 1600, rounded down to the maximum value within the range).

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, click the target instance.

#. In the navigation pane on the left, choose **Database Proxy**. On the displayed page, click the **Read/Write Splitting** tab.

#. In the displayed dialog box, select read replicas for which you want to assign weights on the left and assign the weights on the right.

   -  Different applications can connect to the instance through the IP addresses of different proxy instances. Read requests are routed to the proxy instances that applications connect to. You can also add nodes to or remove nodes from proxy instances.

   -  In the read/write mode, all write requests are routed to the primary node, and read requests are routed to each node based on the read weights.
   -  In the read-only mode, only read requests can be routed to read replicas based on the read weights. Even if the primary node is assigned with a read weight, the weight does not take effect.

   For example, a DB instance contains one primary node and two read replicas, and two proxy instances have been enabled. Proxy instance 1 is in the read/write mode. The primary node and read replica 1 are connected to proxy instance 1 and assigned with a read weight of 100 and 200, respectively. They process read requests in the ratio of 1:2, that is, the primary node processes 1/3 read requests and read replica 1 processes 2/3 read requests. Write requests are automatically routed to the primary node. Proxy instance 2 is in read-only mode. The primary node and read replica 2 are associated with proxy instance 2 and assigned with a read weight of 100 and 200, respectively. In this case, the weight of the primary node does not take effect, and read replica 2 processes all read requests.


   .. figure:: /_static/images/en-us_image_0000001423775818.png
      :alt: **Figure 1** Ratio of read requests processed by each node in multiple proxy instances

      **Figure 1** Ratio of read requests processed by each node in multiple proxy instances

   .. note::

      -  When there are multiple proxy instances, newly created read replicas are automatically associated with proxy instances and their read weights are 0 by default.
      -  If you want to associate a read replica with a proxy instance, go to the **Basic Information** page, locate the read replica in the **Node List** area, and click **Associate with proxy instance**. On the displayed page, select a proxy instance and click **Assign Weight**.
      -  After a read replica is deleted, its weight is automatically removed while the weights of other read replicas remain unchanged.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
