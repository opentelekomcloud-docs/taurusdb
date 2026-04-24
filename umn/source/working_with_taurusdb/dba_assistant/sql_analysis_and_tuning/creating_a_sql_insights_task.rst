:original_name: taurusdb_03_0162.html

.. _taurusdb_03_0162:

Creating a SQL Insights Task
============================

Scenarios
---------

SQL Insights allows you to not only query all executed SQL statements, but also analyze and search for the tables that are accessed and updated most frequently, and the SQL statements that have the longest lock wait, helping you quickly identify exceptions.

Constraints
-----------

-  You need to enable **Collect All Query Logs** before using SQL Insights. Collecting all query logs will reduce instance performance by up to 5%.

-  After **Collect All Query Logs** is disabled, new SQL statements will not be collected anymore and the collected SQL data will be deleted.

-  Some data cannot be recorded if a buffer overrun occurs.

-  Any SQL statement that exceeds the value of **rds_sql_tracer_max_record_size** will not be recorded by default.

   To configure the parameter value, see :ref:`Modifying a Parameter Template <gaussdb_08_0112>`.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and project.

#. Click |image2| in the upper left corner of the page and choose **Databases** > **TaurusDB**.

#. On the **Instances** page, click the instance name.

#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.

#. Click **SQL Explorer** and then **SQL Insights**.

   Click |image3| next to **Collect All Query Logs**.

   To disable this function, click **Log Settings** in the upper right corner, toggle off the **Collect All Query Logs** switch, and click **OK**.

#. Click **Create Task**.

#. On the displayed page, set **Time Range**, **Synchronization to Other Instances**, **Username**, **Keyword**, **Database**, **Thread ID**, **Transaction ID**, **Dimension**, **SQL Type**, and **Execution Status**.

   You can set **Dimension** to **Instance** or **Node**. When **Node** is selected, you can view the SQL logs of deleted nodes.

#. Click **OK**.

#. In the task list, view the SQL Insights task.

   -  You can click **Details** in the **Operation** column to view the SQL Insights task details.
   -  You can click **View Sync Tasks** in the **Operation** column to view synchronization task details.
   -  You can select a keyword such as **Time Range**, **Username**, **Keyword**, or **Database** to search for the SQL statements executed on the current instance or node.

.. |image1| image:: /_static/images/en-us_image_0000002518409421.png
.. |image2| image:: /_static/images/en-us_image_0000002486209558.png
.. |image3| image:: /_static/images/en-us_image_0000002527290701.png
