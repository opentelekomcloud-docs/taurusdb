:original_name: gaussdb_11_0017.html

.. _gaussdb_11_0017:

Creating a Proxy Instance
=========================

A proxy instance enables read and write requests to be automatically routed through its IP address. This section describes how to create a proxy instance.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **TaurusDB**.
#. On the **Instances** page, click the instance name.
#. In the navigation pane on the left, choose **Database Proxy**.
#. Click **Create Proxy Instance**.
#. In the displayed dialog box, configure required parameters and click **OK**. After a proxy instance has been created, you can click **Create Proxy Instance** in the **Database Proxy** page to add a new proxy instance.

   -  **Proxy Instance Name**: Enter 4 to 64 characters starting with a letter. Only letters (case-sensitive), digits, hyphens (-), and underscores (_) are allowed.
   -  **Proxy Mode**: Select **Read/Write** or **Read-only**.

      .. note::

         -  **Read/Write**: All write requests are forwarded only to the primary node, and all read requests are forwarded to the selected nodes based on the read weights. The default read weight of the primary node is **0**.
         -  **Read-only**: All read requests are forwarded to the selected read replicas based on read weights. Even if the primary node is assigned with a read weight, the weight does not take effect.

            -  It supports only read requests. If write requests are forwarded to the selected nodes, an error message is displayed.
            -  This mode offloads the pressure of the primary node by routing all read requests to read replicas.
            -  DDL, DML, and temporary table operations are not supported in the read-only mode.

   -  Proxy instance specifications: 2 vCPUs \| 4 GB (general-enhanced), 4 vCPUs \| 8 GB (general-enhanced), and 8 vCPUs \| 16 GB (general-enhanced).
   -  **Proxy Instance Nodes**: The default value is **2**. Enter an integer from 2 to 32. Number of recommended proxy instance nodes = (Number of vCPUs of the primary node + Total number of vCPUs of all read replicas)/(4 x Number of vCPUs of the proxy instance), rounded up.

   -  **Read Weight**: For instances with read/write splitting enabled, you can add or delete nodes and assign weights for the primary node and read replicas. Requests are assigned to the nodes based on the read weights you specify. For example, read weights assigned to one primary node and two read replicas are 100, 200, and 200, respectively. In the read/write mode, the primary node and two read replicas process read requests in the ratio of 1:2:2. The primary node processes 20% of read requests, and each read replica processes 40% of read requests. Write requests are automatically routed to the primary node. In the read-only mode, the read weight of the primary node does not take effect, and the two read replicas process 50% of read requests, respectively. For details, see :ref:`Assigning Read Weights <gaussdb_11_0018>`.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
