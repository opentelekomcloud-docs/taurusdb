:original_name: gaussdb_03_0092.html

.. _gaussdb_03_0092:

Changing vCPUs and Memory of an Instance
========================================

Scenarios
---------

You can change the vCPUs or memory of a DB instance as required. If the status of a DB instance changes from **Changing instance specifications** to **Available**, the change is successful.

-  An instance cannot be deleted when its specifications are being changed.
-  The vCPUs and memory can be changed only at the instance level. The specifications of the primary node or read replicas cannot be changed separately for a given instance.

.. important::

   -  Changing the vCPUs and memory will cause the instance to reboot. To prevent service interruptions, change the instance specifications during off-peak hours.
   -  To prevent traffic congestion during peak hours, you are advised to reboot the instance during off-peak hours.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. You can change the instance specifications in either of the following ways:

   -  On the **Instances** page, locate the target DB instance and choose **More** > **Change Instance Specifications** in the **Operation** column.
   -  Click the target DB instance to go to the **Basic Information** page. In the **DB Instance Information** area, click **Change** in the **Instance Specifications** field.

#. On the displayed page, specify the new instance specifications, and click **Next**.

#. On the displayed page, confirm the instance specifications.

   -  If you need to modify your settings, click **Previous** to go back to the page where you specify details.
   -  If you do not need to modify your settings, click **Submit**.

#. View the DB instance specification change result.

   Changing the instance specifications takes 5-15 minutes. During this period, the status of the instance on the **Instances** page is **Changing instance specifications**. After a few minutes, you can click the instance name to view the new instance specifications on the displayed **Basic Information** page.

   .. important::

      After the specifications of DB instances 8.0 are changed, the system will change the values of the following parameters accordingly: **innodb_buffer_pool_size**, **innodb_log_buffer_size**, **max_connections**, **innodb_buffer_pool_instances**, **innodb_page_cleaners**, **innodb_parallel_read_threads**, **innodb_read_io_threads**, **innodb_write_io_threads**, **threadpool_size** and **query_cache_size**.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
