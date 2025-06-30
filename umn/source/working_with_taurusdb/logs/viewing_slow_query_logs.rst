:original_name: gaussdb_03_0019.html

.. _gaussdb_03_0019:

Viewing Slow Query Logs
=======================

Scenarios
---------

Slow query logs record statements that exceed **long_query_time** (1 second by default). You can view log details and statistics to identify the statements that are executing slowly and optimize the statements.

TaurusDB supports the following statements:

-  SELECT
-  INSERT
-  UPDATE
-  DELETE
-  CREATE
-  ALTER
-  DROP

Viewing Log Details
-------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, click the target DB instance. The **Basic Information** page is displayed.

#. In the navigation pane on the left, choose **Logs**.

#. On the **Slow Query Logs** page, view the slow query log details.

   You can view the slow query log records of a specified execution statement type or a specific time period.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
