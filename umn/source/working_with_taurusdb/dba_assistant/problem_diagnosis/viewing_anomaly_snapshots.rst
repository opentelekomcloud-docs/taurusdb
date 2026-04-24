:original_name: en-us_topic_0000002521462469.html

.. _en-us_topic_0000002521462469:

Viewing Anomaly Snapshots
=========================

After anomaly diagnosis is enabled, the system checks your instance health status and diagnoses faults. If there is an anomaly, its snapshots will be collected, helping you monitor instance performance in real time.

Diagnosis Item
--------------

.. _en-us_topic_0000002521462469__en-us_topic_0000002009238626_table9521791237:

.. table:: **Table 1** Diagnosis item

   ======================= ===================================
   Item                    Description
   ======================= ===================================
   Transaction uncommitted There are uncommitted transactions.
   ======================= ===================================

Constraints
-----------

Collecting abnormal snapshots will cause about 5% of instance performance loss.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and project.

#. Click |image2| in the upper left corner of the page and choose **Databases** > **TaurusDB**.

#. On the **Instances** page, click the instance name.

#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.

#. Click **Anomaly Snapshots**.

#. Click |image3| on the right of **Collect Abnormal Snapshots** to enable anomaly diagnosis.

   After anomaly diagnosis is enabled, if any anomaly listed in :ref:`Table 1 <en-us_topic_0000002521462469__en-us_topic_0000002009238626_table9521791237>` occurs, you can view its snapshots. Anomaly snapshot records are retained for seven days and will be deleted after this time expires. A maximum of 100 records can be retained for a single node.

   Click **Diagnosis Details** in the **Operation** column to view diagnosis result details and optimization suggestions.

   Click the **Anomaly Snapshots** tab to view session snapshots, metadata lock snapshots, InnoDB lock snapshots, and transaction snapshots.

.. |image1| image:: /_static/images/en-us_image_0000002518409421.png
.. |image2| image:: /_static/images/en-us_image_0000002486209558.png
.. |image3| image:: /_static/images/en-us_image_0000002527170671.png
