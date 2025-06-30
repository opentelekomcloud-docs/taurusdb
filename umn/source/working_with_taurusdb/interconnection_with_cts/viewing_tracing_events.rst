:original_name: gaussdb_03_0015.html

.. _gaussdb_03_0015:

Viewing Tracing Events
======================

Scenarios
---------

After CTS is enabled, operations on cloud resources are recorded. You can view the operation records of the last 7 days on the CTS console.

This section describes how to query the operation records of last 7 days on the CTS console.

Procedure
---------

#. Log in to the management console.

#. Choose **Management & Deployment** > **Cloud Trace Service**.

#. Choose **Trace List** in the navigation pane on the left.

#. Filter conditions to query traces. The details are described as follows:

   -  **Trace Source**, **Resource Type**, and **Search By**: Select a filter from the drop-down list.

      When you select **Resource ID** for **Search By**, you also need to select or enter a resource ID.

   -  **Operator**: Select a specific operator from the drop-down list.

   -  **Trace Status**: Available options include **All trace statuses**, **Normal**, **Warning**, and **Incident**. You can only select one of them.

   -  In the upper right corner of the page, you can specify a time range for querying traces.

#. Select the search criteria, and click **Query**.

#. Click |image1| on the left of the required trace to expand its details.

#. Click **View Trace** in the **Operation** column. On the displayed dialog box, the trace structure details are displayed.

#. Click **Export** on the right. CTS exports traces collected in the past seven days to a CSV file. The CSV file contains all information related to traces on the management console.

   For details about key fields in the trace structure, see sections "Trace Structure" and "Trace Examples" in the *Cloud Trace Service User Guide*.

.. |image1| image:: /_static/images/en-us_image_0000001472729081.png
