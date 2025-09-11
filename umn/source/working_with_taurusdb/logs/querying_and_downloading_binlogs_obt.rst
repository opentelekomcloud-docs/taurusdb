:original_name: en-us_topic_0000002347520144.html

.. _en-us_topic_0000002347520144:

Querying and Downloading Binlogs (OBT)
======================================

Binlogs record all DDL and DML statements (except data query statements). You can download binlogs to a local PC for further analysis.

This section describes how to enable binlog, and then query and download binlogs on the TaurusDB console.

Billing
-------

Binlogs are stored in OBS buckets.

Prerequisites
-------------

-  Binlog can only be enabled when the following conditions are met:

   -  If the kernel version of your DB instance is earlier than 2.0.45.230900, the value of **log-bin** must be **ON**. To view and modify the parameter value, see :ref:`Modifying a Parameter Template <gaussdb_08_0112>`.
   -  If the kernel version of your DB instance is 2.0.45.230900 or later, the value of **rds_global_sql_log_bin** must be **ON**.

-  Before viewing and downloading binlogs, you need to enable binlog by referring to :ref:`Enabling Binlog <en-us_topic_0000002347520144__section20209121620219>`.

Constraints
-----------

To use binlogs, set the **log-bin** or **rds_global_sql_log_bin** parameter to **ON**.

.. _en-us_topic_0000002347520144__section20209121620219:

Enabling Binlog
---------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **TaurusDB**.
#. On the **Instances** page, click the instance name.
#. In the navigation pane, choose **Logs**.
#. Click the **Binlog** tab.
#. Click **Configure Binlog**. In the displayed dialog box, enable **Binlog** and set **Retention Period**.

   -  The retention period ranges from 1 to 180 days.
   -  After binlog is disabled, the generated logs will be automatically deleted after the retention period expires. Deleted logs cannot be restored. Exercise caution when disabling binlog.

Querying and Downloading Binlogs
--------------------------------

#. Log in to the management console.
#. Click |image2| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **TaurusDB**.
#. On the **Instances** page, click the instance name.
#. In the navigation pane, choose **Logs**.
#. Click the **Binlog** tab.

   -  View binlogs generated in the last 15 minutes, last 30 minutes, last 1 hour, last 24 hours, last 7 days, last 30 days, or a custom time range.

   -  Click **Download** in the **Operation** column to download a binlog to a local PC.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
.. |image2| image:: /_static/images/en-us_image_0000001352219100.png
