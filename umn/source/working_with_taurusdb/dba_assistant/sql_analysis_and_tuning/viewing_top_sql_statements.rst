:original_name: taurusdb_03_0164.html

.. _taurusdb_03_0164:

Viewing Top SQL Statements
==========================

Scenarios
---------

After **Collect All Query Logs** is enabled, you can filter, search for, and analyze SQL statements in multiple dimensions and gain a comprehensive insight into all SQL statements. **Top SQL** helps you locate exceptions.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and project.
#. Click |image2| in the upper left corner of the page and choose **Databases** > **TaurusDB**.
#. On the **Instances** page, click the instance name.
#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.
#. Choose **SQL Explorer** > **Top SQL**.
#. Click **Subscribe**. In the displayed dialog box, you can learn about Intelligent O&M functions and pricing.
#. View the top SQL statements of the DB instance.

   -  View execution durations of the top SQL statements in the last 1 hour, last 3 hours, last 6 hours, last 12 hours, or a custom time period (no longer than one day).
   -  Click a point in time or drag to select a time period to view the SQL statistics of a SQL template.
   -  Click |image3| to export information about all top SQL templates in the list. To use this export function, subscribe to Intelligent O&M.
   -  Locate a SQL template and click **Details** to view the total execution times, average rows scanned, average execution duration, and the like.
   -  Locate a SQL template and click **SQL Throttling** in the **Operation** column to add a SQL throttling rule. For details, see :ref:`Configuring SQL Throttling <taurusdb_03_0163>`.
   -  Select **Comparison by Date** and select dates and a time range to view the top SQL statements in the time range on different days.

.. |image1| image:: /_static/images/en-us_image_0000002518409421.png
.. |image2| image:: /_static/images/en-us_image_0000002486209558.png
.. |image3| image:: /_static/images/en-us_image_0000002495130974.png
