:original_name: taurusdb_03_0161.html

.. _taurusdb_03_0161:

Viewing Slow Query Logs
=======================

Scenarios
---------

**Slow Query Logs** displays a chart of SQL statements that are taking too long to execute and allows you to sort slow SQL statements by multiple dimensions, such as by user, host, or SQL template. It helps you quickly identify bottlenecks and improve instance performance.

Constraints
-----------

-  If you did not subscribe to Intelligent O&M, you can only view the data of the last hour. The data will be automatically deleted when it expires. You are advised to subscribe to Intelligent O&M. This will allow data to be stored for up to 30 days. For details, see :ref:`Subscribing to Intelligent O&M <taurusdb_03_0161__en-us_topic_0000001882727596_section978713131721>`.
-  After **Collect Slow Query Logs** is enabled, SQL text will be stored in OBS.
-  Incorrectly optimizing slow queries may cause service exceptions. Exercise caution when performing this operation.

.. _taurusdb_03_0161__en-us_topic_0000001882727596_section978713131721:

Subscribing to Intelligent O&M
------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and project.
#. Click |image2| in the upper left corner of the page and choose **Databases** > **TaurusDB**.
#. On the **Instances** page, click the instance name.
#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.
#. Click the **Slow Query Logs** tab.
#. Click **Subscribe**. In the displayed dialog box, you can learn about Intelligent O&M functions and pricing.
#. Select "I have read and understand the billing rules." and click **Subscribe**.

Collecting Slow Query Logs
--------------------------

Click **Log Settings** in the upper right corner. In the displayed dialog box, enable **Collect Slow Query Logs** and click **OK**. SQL statement logs can then be stored for analysis.

If you do not need to collect slow query logs later, you can disable **Collect Slow Query Logs**. If **Collect Slow Query Logs** is disabled, new SQL statements will not be collected anymore and the collected SQL data will be deleted.

Slow Query Log Storage
----------------------

-  Intelligent O&M subscribed:

   Click **Log Settings** in the upper right corner. In the displayed dialog box, set **Slow Query Log Retention** in the **Log Storage and Archiving** area.

   -  **Slow Query Log Retention**: The default value is **7**. The value ranges from 1 to 30 days. After the period expires, the logs are automatically deleted.
   -  **All Query Log Retention**: The default value is **7**. The value ranges from 1 to 180 days.

-  Intelligent O&M not subscribed:

   -  **Slow Query Log Retention**: 1 hour. After the period expires, the logs are automatically deleted.
   -  **All Query Log Retention**: 1 hour

Viewing Slow Queries over Time
------------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select a region and project.

#. Click |image4| in the upper left corner of the page and choose **Databases** > **TaurusDB**.

#. On the **Instances** page, click the instance name.

#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.

#. Click the **Slow Query Logs** tab.

#. Select a time range, and view slow queries over time by instance or node.

   You can view slow query logs in the last 1 hour, last 3 hours, last 6 hours, last 12 hours, or a custom time period.

#. Above the chart, switch to another instance or node to view its slow queries over time.

   Move the cursor to a point in time of the chart to view the number of slow query logs and CPU usage at the point in time.

Viewing Slow Query Log Details
------------------------------

#. Log in to the management console.

#. Click |image5| in the upper left corner and select a region and project.

#. Click |image6| in the upper left corner of the page and choose **Databases** > **TaurusDB**.

#. On the **Instances** page, click the instance name.

#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.

#. Click the **Slow Query Logs** tab.

#. Select an instance, node, and time range, and view slow query log details. The details include the SQL statement, execution start time, database, client, user, execution duration, lock wait duration, and scanned and returned rows.

   You can view slow query logs in the last 1 hour, last 3 hours, last 6 hours, last 12 hours, or a custom time period.

   -  Export slow query log details.

      a. Click **Export**.
      b. In the displayed dialog box, select **Quick export** or **Export all** for **Export Mode**.

         -  **Quick export**: Log details are exported to your local PC. Only the first 1,000 records can be exported.

         -  **Export all**: Select an OBS bucket and a directory to export log details to the OBS bucket. Up to 100,000 records can be exported.

            If no OBS bucket is available, create one on the OBS console. For details, see the OBS documentation.

      c. Click **OK**.
      d. After the slow query log details are exported, click **View All Export Records**. In the displayed dialog box, click **Download** in the **Operation** column. After the download is complete, view the slow query log details in the ZIP package.

   -  To add a SQL throttling rule, locate a record and click **SQL Throttling** in the **Operation** column. In the displayed dialog box, specify **SQL Type**, **Keyword**, and **Max. Concurrent Requests**, and click **OK**. For details, see :ref:`Configuring SQL Throttling <taurusdb_03_0163>`.
   -  To view SQL diagnosis results, locate a record and click **Diagnose** in the **Operation** column. In the displayed dialog box, confirm the slow SQL statement to be diagnosed and click **OK**. In the **Diagnosis Details** area, you can see the SQL diagnosis results.

Viewing Top 5 Slow Query Logs
-----------------------------

#. Log in to the management console.

#. Click |image7| in the upper left corner and select a region and project.

#. Click |image8| in the upper left corner of the page and choose **Databases** > **TaurusDB**.

#. On the **Instances** page, click the instance name.

#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.

#. Click the **Slow Query Logs** tab.

#. Select an instance, node, and time range. In the **Top 5 Slow Query Logs** area, view the top 5 slow SQL statements by user or client IP address.

   You can view slow query logs in the last 1 hour, last 3 hours, last 6 hours, last 12 hours, or a custom time period.

Viewing Template Statistics
---------------------------

#. Log in to the management console.
#. Click |image9| in the upper left corner and select a region and project.
#. Click |image10| in the upper left corner of the page and choose **Databases** > **TaurusDB**.
#. On the **Instances** page, click the instance name.
#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.
#. Click the **Slow Query Logs** tab.
#. Select an instance, node, and time range, and view the template statistics.

   -  Click **View Sample** in the **Operation** to view the sample of a SQL template.

   -  Export template statistics.

      a. Click **Export**.
      b. In the displayed dialog box, select **Quick export** or **Export all** for **Export Mode**.

         -  **Quick export**: Log details are exported to your local PC. Only the first 1,000 records can be exported.

         -  **Export all**: Select an OBS bucket and a directory to export log details to the OBS bucket. Up to 100,000 records can be exported.

            If no OBS bucket is available, create one on the OBS console. For details, see the OBS documentation.

      c. Click **OK**.
      d. After the slow query log details are exported, click **View All Export Records**. In the displayed dialog box, click **Download** in the **Operation** column. After the download is complete, view the slow query log details in the ZIP package.

.. |image1| image:: /_static/images/en-us_image_0000002518409421.png
.. |image2| image:: /_static/images/en-us_image_0000002486209558.png
.. |image3| image:: /_static/images/en-us_image_0000002518409421.png
.. |image4| image:: /_static/images/en-us_image_0000002486209558.png
.. |image5| image:: /_static/images/en-us_image_0000002518409421.png
.. |image6| image:: /_static/images/en-us_image_0000002486209558.png
.. |image7| image:: /_static/images/en-us_image_0000002518409421.png
.. |image8| image:: /_static/images/en-us_image_0000002486209558.png
.. |image9| image:: /_static/images/en-us_image_0000002518409421.png
.. |image10| image:: /_static/images/en-us_image_0000002486209558.png
