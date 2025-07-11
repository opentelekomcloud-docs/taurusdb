:original_name: gaussdb_03_0088.html

.. _gaussdb_03_0088:

Viewing Monitoring Metrics
==========================

Scenarios
---------

The Cloud Eye service monitors operating statuses of DB instances. You can view the metrics of DB instances on the management console. By monitoring system resource usage during database running, you can identify periods of high resource usage. You can also check error logs or slow query logs to optimize database performance.

.. note::

   You can configure resource alarm rules on the Cloud Eye console. For details, see "Creating an Alarm Rule" in the *Cloud Eye User Guide*.

Prerequisites
-------------

-  A DB instance is running properly.

   Metrics of the DB instances that are faulty or have been deleted cannot be displayed on the Cloud Eye console. You can view their metrics after they are rebooted or restored to normal.

.. note::

   If a DB instance has been faulty for 24 hours, Cloud Eye considers it to no longer exist and deletes it from the monitoring object list. You need to manually clear the alarm rules created for the DB instance.

-  A DB instance keeps running properly for about 10 minutes.

   For a newly created DB instance, you need to wait a bit before you can view the metrics.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, locate the target DB instance and click **View Metrics** in the **Operation** column to go to the Cloud Eye console.

   You can use either of the following methods to view metrics:

   -  Click the target DB instance. On the displayed **Basic Information** page, click **View Metrics** in the upper right corner of the page to go to the Cloud Eye console.
   -  At the bottom part of the **Basic Information** page, locate the target read replica and click **View Metrics** in the **Operation** column to go to the Cloud Eye console.

#. On the Cloud Eye console, view DB instance metrics.

   Cloud Eye can monitor performance metrics from the last 1 hour, last 3 hours, last 12 hours, last 24 hours or last 7 days.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
