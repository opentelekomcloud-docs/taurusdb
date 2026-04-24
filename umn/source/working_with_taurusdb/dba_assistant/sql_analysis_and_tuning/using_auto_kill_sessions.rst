:original_name: en-us_topic_0000002489182682.html

.. _en-us_topic_0000002489182682:

Using Auto Kill Sessions
========================

You can kill all sessions, kill specific sessions by criteria, and view history.

To kill the current session or manually kill a session, see :ref:`Managing Real-Time Sessions <en-us_topic_0000002521502463>`.

Functions
---------

+---------------------------------------+------------------------------------------------------------------------------------------------------------------+
| Function                              | Description                                                                                                      |
+=======================================+==================================================================================================================+
| Killing specific sessions by criteria | You can add a task for killing sessions. Sessions that meet the criteria will be killed.                         |
+---------------------------------------+------------------------------------------------------------------------------------------------------------------+
| Killing all sessions                  | After you enable **Auto Kill Sessions** and click **Kill All Sessions**, all sessions are automatically deleted. |
+---------------------------------------+------------------------------------------------------------------------------------------------------------------+
| Viewing history                       | You can view killed sessions.                                                                                    |
+---------------------------------------+------------------------------------------------------------------------------------------------------------------+

Killing Specific Sessions by Criteria
-------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and project.

#. Click |image2| in the upper left corner of the page and choose **Databases** > **TaurusDB**.

#. On the **Instances** page, click the instance name.

#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.

#. Choose **SQL Explorer** > **Auto Kill Sessions**.

#. Click |image3| on the right of **Auto Kill Sessions**. In the displayed dialog box, click **OK**.

#. Click **Add Kill Task**.

#. In the displayed dialog box, set the criteria for killing sessions. The parameters listed in :ref:`Table 1 <en-us_topic_0000002489182682__en-us_topic_0000002014649624_table15329431173510>` are in a logical AND relationship.

   If you only specify **Session Duration (s)** and **Task Duration (s)**, all sessions that meet the criteria will be killed.

   A maximum of five conditional kill tasks can be executed at the same time.

   .. _en-us_topic_0000002489182682__en-us_topic_0000002014649624_table15329431173510:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                |
      +===================================+============================================================================================================================+
      | User                              | Enter a single value, for example, **root**.                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Host IP Address                   | Enter a single value, for example, **168.192.0.0**.                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Database Name                     | Enter a database name.                                                                                                     |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Command                           | Enter a command.                                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | SQL Statement                     | Enter a SQL statement.                                                                                                     |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Session Duration (s)              | The value ranges from 1 to 2147483647.                                                                                     |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Task Closure Method               | If you select **Scheduled**, you need to set **Task Duration**. After the duration ends, the task is automatically closed. |
      |                                   |                                                                                                                            |
      |                                   | If you select **Manual**, you can click **Stop** in the **Operation** column of the task list to manually close a task.    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Task Duration (s)                 | The value ranges from 10 to 31535999.                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   When the criteria for killing sessions are met, the system automatically kills the sessions.

Killing All Sessions
--------------------

#. Log in to the management console.
#. Click |image4| in the upper left corner and select a region and project.
#. Click |image5| in the upper left corner of the page and choose **Databases** > **TaurusDB**.
#. On the **Instances** page, click the instance name.
#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.
#. Choose **SQL Explorer** > **Auto Kill Sessions**.
#. Click |image6| on the right of **Auto Kill Sessions**. In the displayed dialog box, click **OK**.
#. Click **Kill All Sessions**.
#. In the displayed dialog box, click **OK**.

Viewing History
---------------

#. Log in to the management console.

#. Click |image7| in the upper left corner and select a region and project.

#. Click |image8| in the upper left corner of the page and choose **Databases** > **TaurusDB**.

#. On the **Instances** page, click the instance name.

#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.

#. Choose **SQL Explorer** > **Auto Kill Sessions**.

#. Click |image9| on the right of **Auto Kill Sessions**. In the displayed dialog box, click **OK**.

#. Click **View History**.

#. In the displayed dialog box, select a time range to view killed sessions within that period.

   A maximum of 500 session records can be displayed.

.. |image1| image:: /_static/images/en-us_image_0000002518409421.png
.. |image2| image:: /_static/images/en-us_image_0000002486209558.png
.. |image3| image:: /_static/images/en-us_image_0000002527170759.png
.. |image4| image:: /_static/images/en-us_image_0000002518409421.png
.. |image5| image:: /_static/images/en-us_image_0000002486209558.png
.. |image6| image:: /_static/images/en-us_image_0000002494971108.png
.. |image7| image:: /_static/images/en-us_image_0000002518409421.png
.. |image8| image:: /_static/images/en-us_image_0000002486209558.png
.. |image9| image:: /_static/images/en-us_image_0000002495131002.png
