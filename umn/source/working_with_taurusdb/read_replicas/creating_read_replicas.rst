:original_name: gaussdb_03_0111.html

.. _gaussdb_03_0111:

Creating Read Replicas
======================

Scenarios
---------

Read replicas are used to enhance the read capabilities and reduce read pressure on DB instances.

After a DB instance is created, you can create read replicas for it.

-  If you select the single AZ type, read replicas are deployed in the same AZ as the primary node.
-  If you select the multi-AZ type, read replicas are deployed in different AZs from the primary node to ensure high reliability.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, locate the instance that you want to create read replicas for and choose **More** > **Create Read Replica** in the **Operation** column.

   Alternatively, click the instance name to go to the **Basic Information** page. In the **DB Instance Topology** area, click |image2| to create read replicas.

#. On the displayed page, specify **Failover Priority** and **Quantity** and then click **Create Now**.

#. After read replicas are created, you can manage them following the instructions provided in :ref:`Managing a Read Replica <gaussdb_03_0112>`.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
.. |image2| image:: /_static/images/en-us_image_0000001403218753.png
