:original_name: en-us_topic_0000002489182676.html

.. _en-us_topic_0000002489182676:

Viewing the Overall Status of a DB Instance
===========================================

The **Dashboard** page allows you to view the overall status of the current DB instance, including alarms, health check results, compute resource usage, storage resource usage, and key performance metrics.

Alarms
------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and project.

#. Click |image2| in the upper left corner of the page and choose **Databases** > **TaurusDB**.

#. On the **Instances** page, click the instance name.

#. In the navigation pane, choose **DBA Assistant** > **Real-Time Diagnosis**.

#. On the **Dashboard** page, view instance alarms provided by Cloud Eye.

   You can customize alarm rules by adjusting alarm policies and severities for key metrics, such as CPU usage and disk usage. To view alarm details, click the number next to an alarm severity.

Health
------

In the **Health** area, you can view real-time health check results. By default, the data for high vCPU utilization, memory bottlenecks, high-frequency slow SQL statements, and lock waits are displayed.

For abnormal metrics, click **Diagnose** to view diagnosis details and suggestions. For details, see :ref:`Table 1 <en-us_topic_0000002489182676__en-us_topic_0000002002572404_en-us_topic_0000001498704924_table10196185183110>`.

For details about metrics, see :ref:`Viewing Monitoring Metrics <gaussdb_03_0088>`. For details about how to configure alarm rules on Cloud Eye, see :ref:`Setting Alarm Rules <gaussdb_03_0087>`.

.. _en-us_topic_0000002489182676__en-us_topic_0000002002572404_en-us_topic_0000001498704924_table10196185183110:

.. table:: **Table 1** Health diagnosis and suggestions

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------+
   | Item                              | Exception Trigger Condition                                                                                     |
   +===================================+=================================================================================================================+
   | High vCPU utilization             | Either of the following conditions is met:                                                                      |
   |                                   |                                                                                                                 |
   |                                   | -  After you configure alarm rules on Cloud Eye, an alarm is reported, indicating the CPU usage is high.        |
   |                                   | -  The CPU usage exceeds 95% for more than 2.5 minutes of a 5-minute measurement period.                        |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------+
   | Memory bottleneck                 | Either of the following conditions is met:                                                                      |
   |                                   |                                                                                                                 |
   |                                   | -  After you configure alarm rules on Cloud Eye, an alarm is reported, indicating the memory usage is high.     |
   |                                   | -  The memory usage exceeds 95% within a 5-minute measurement period.                                           |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------+
   | High-frequency slow SQL           | Either of the following conditions is met:                                                                      |
   |                                   |                                                                                                                 |
   |                                   | -  After you configure alarm rules on Cloud Eye, an alarm is reported, indicating there are too many slow logs. |
   |                                   | -  There are more than 100 slow logs within five minutes.                                                       |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------+
   | Lock wait                         | After you configure alarm rules on Cloud Eye, any of the following alarms is reported:                          |
   |                                   |                                                                                                                 |
   |                                   | -  Row Lock Time                                                                                                |
   |                                   | -  InnoDB Row Locks                                                                                             |
   |                                   | -  Row Lock Waits                                                                                               |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------+

Compute Resource Usage
----------------------

In the **Compute Resource Usage** area, the vCPU usage and memory usage are displayed by default. The displayed values are the average values for 5-minute measurement periods.

Storage Resource Usage
----------------------

In the **Storage Resource Usage** area, the storage usage, disk read IOPS, and disk write IOPS are displayed by default. The displayed values are the average values for 5-minute measurement periods.

Key Performance Metrics
-----------------------

In the **Key Performance Metrics** area, the CPU usage & slow query logs, connections, memory utilization, and disk reads/writes from the last hour are displayed by default. The displayed values are real-time values.

.. |image1| image:: /_static/images/en-us_image_0000002518409421.png
.. |image2| image:: /_static/images/en-us_image_0000002486209558.png
