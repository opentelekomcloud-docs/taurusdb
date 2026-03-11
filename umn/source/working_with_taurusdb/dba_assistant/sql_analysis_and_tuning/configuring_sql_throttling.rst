:original_name: taurusdb_03_0163.html

.. _taurusdb_03_0163:

Configuring SQL Throttling
==========================

Scenarios
---------

SQL throttling allows you to create rules to control concurrent execution of SQL statements by specifying SQL type, keywords, and maximum concurrency. To maintain better performance at high concurrency, SQL statements that meet the specified SQL type and keyword and exceed the maximum concurrency will not be executed. You can check how many times SQL statements are intercepted by throttling rules.

You can also identify SQL statements that consume the most resources based on the execution duration or number of executions and then create throttling rules for these SQL statements.

Supported Versions
------------------

SQL throttling is only available to TaurusDB instances that meet any of the following requirements:

-  2.0.28.40 > kernel version >= 2.0.28.15 (Throttling rules for SELECT, UPDATE, and DELETE statements are supported.)
-  Kernel version >= 2.0.29.1 (Throttling rules for SELECT, UPDATE, and DELETE statements are supported.)
-  Kernel version >= 2.0.54.240600 (Throttling rules for SELECT, UPDATE, DELETE, and INSERT statements are supported.)

Constraints
-----------

.. table:: **Table 1** Constraints on throttling rules

   +-----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scenario                                | Constraint                                                                                                                                                                                                                                                            |
   +=========================================+=======================================================================================================================================================================================================================================================================+
   | Adding a SQL throttling rule            | -  A single throttling rule can contain a maximum of 128 keywords. Backslashes (\\) or null characters cannot be used as keywords. Spaces at the beginning and end of a keyword and special null characters (such as \\'t', \\'r', and \\'n') will be ignored.        |
   |                                         | -  A throttling rule cannot end with a tilde (~).                                                                                                                                                                                                                     |
   |                                         | -  For TaurusDB kernel 2.0.69.250900 or later, a maximum of 100 rules are allowed, each with no more than 1,000 bytes.                                                                                                                                                |
   |                                         | -  If the kernel version of your TaurusDB instance is 2.0.54.240600 or later, the total length of all rules and concurrent requests of SELECT, UPDATE, DELETE, or INSERT statements cannot exceed 4,000 bytes. The length of a single rule cannot exceed 1,000 bytes. |
   |                                         | -  If the kernel version of your TaurusDB instance is earlier than 2.0.54.240600, the total length of all rules and concurrent requests of SELECT, UPDATE, or DELETE statements cannot exceed 1,024 bytes.                                                            |
   +-----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Matching a SQL throttling rule          | -  Keywords in a throttling rule will be matched in sequence. If a rule contains **a~and~b**, **xxx a>1 and b>2** will be throttled but **xxx b>2 and a>1** will not.                                                                                                 |
   |                                         | -  Each SQL throttling rule is applied to only the SQL statements that your database received after the rule is created.                                                                                                                                              |
   |                                         | -  If different rules are created for the primary node and read replicas of an instance, the rules still apply to the primary node and read replicas after their roles are switched over.                                                                             |
   |                                         | -  If a SQL statement matches multiple throttling rules, only the most recently added rule is applied.                                                                                                                                                                |
   |                                         | -  SQL statements that have been executed before a SQL throttling rule is added are not counted.                                                                                                                                                                      |
   |                                         | -  Throttling rules are applied based on SQL statement prefixes. For example, if a throttling rule is **SELECT~COUNT~t1**, **SELECT COUNT(*) FROM t1** and **SELECT COUNT(*) FROM t1 LIMIT 1** will both be intercepted.                                              |
   |                                         | -  SQL throttling rules of the following operations will be regenerated, and the number of concurrent and intercepted requests of the regenerated throttling rules will be cleared and recalculated.                                                                  |
   |                                         |                                                                                                                                                                                                                                                                       |
   |                                         |    -  Throttling rules will be regenerated for all SELECT, UPDATE, DELETE, and INSERT statements when you reboot a node or enable SQL Throttling.                                                                                                                     |
   |                                         |    -  For TaurusDB kernel earlier than 2.0.69.250900, if you add or delete a throttling rule, all of them will be regenerated for SELECT, UPDATE, DELETE, and INSERT statements.                                                                                      |
   +-----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Recommended rule                        | -  SQL statements executed by user **root** are not included in the recommended rule.                                                                                                                                                                                 |
   |                                         | -  If the length of a SQL statement exceeds 1,000 bytes, the SQL statement will be automatically truncated. You need to modify its length when using the recommended rule.                                                                                            |
   |                                         | -  The recommended rule is based on the 1,000 longest sessions.                                                                                                                                                                                                       |
   +-----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Historical SQL throttling rules         | -  The creation time of existing throttling rules in the SQL throttling rule list are displayed as the time when the feature for setting validity periods for throttling rules was released. The creation time of new throttling rules will be displayed accurately.  |
   |                                         | -  You can only view the deleted and expired SQL throttling rules of the last 30 days.                                                                                                                                                                                |
   +-----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scenarios not subject to SQL throttling | -  System tables                                                                                                                                                                                                                                                      |
   |                                         | -  SQL statements not used to query data, such as SELECT SLEEP(*xxx*);                                                                                                                                                                                                |
   |                                         | -  If the TaurusDB kernel version is earlier than 2.0.45.230900, the **root** account is not restricted by SQL throttling.                                                                                                                                            |
   |                                         | -  SQL statements in stored procedures, triggers, and functions                                                                                                                                                                                                       |
   +-----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Impact of throttling rules              | -  As the number of throttling rules increases, the performance may deteriorate. Delete unnecessary throttling rules.                                                                                                                                                 |
   |                                         | -  If SQL throttling is triggered, error "ERROR 1317 (70100): Query execution was interrupted" is reported.                                                                                                                                                           |
   +-----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Adding a Throttling Rule
------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and project.
#. Click |image2| in the upper left corner of the page and choose **Databases** > **TaurusDB**.
#. On the **Instances** page, click the instance name.
#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.
#. Click **SQL Explorer** and then **SQL Throttling**.
#. On the displayed page, toggle on **Enable SQL Throttling**.
#. Click **Add Rule**. In the displayed dialog box, specify **SQL Type**, **Keyword**, and **Max. Concurrent Requests**.

   .. table:: **Table 2** Parameter description

      +---------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                                         | Description                                                                                                                                                                                                                                                                                   |
      +===================================================+===============================================================================================================================================================================================================================================================================================+
      | SQL Type                                          | There are four options: **SELECT**, **UPDATE**, **DELETE**, and **INSERT**.                                                                                                                                                                                                                   |
      +---------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Keyword                                           | A maximum of 128 keywords (case-insensitive) are supported. You can specify keywords in either of the following ways:                                                                                                                                                                         |
      |                                                   |                                                                                                                                                                                                                                                                                               |
      |                                                   | -  **Manually**: Take **select~a** as an example. **select** and **a** are two keywords contained in a SQL throttling rule. The keywords are separated by a tilde (~). In this example, the rule restricts the execution of only the SQL statements containing keywords **select** and **a**. |
      |                                                   | -  **Using SQL statements**: You can enter a SQL statement and then click **Generate Keyword**. The generated keywords are for reference only. Exercise caution when using them.                                                                                                              |
      |                                                   |                                                                                                                                                                                                                                                                                               |
      |                                                   | SQL statements match the keywords from first to last. For example, if one rule contains the keyword **a~and~b**, the statement **\**\* a>1 and b>2** can match the keyword, but **\**\* b>2 and a>1** cannot.                                                                                 |
      |                                                   |                                                                                                                                                                                                                                                                                               |
      |                                                   | Empty characters before and after each keyword will be ignored, for example, spaces, '\\n', '\\r', and '\\t'.                                                                                                                                                                                 |
      +---------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. Concurrent Requests                          | If the number of concurrent SQL statements matching the keyword exceeds this limit, the SQL statements will not be executed. The value ranges from 0 to 1000000000.                                                                                                                           |
      +---------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Kill existing sessions that match this rule       | If this option is selected, all sessions generated by users subject to this SQL throttling rule will be killed.                                                                                                                                                                               |
      +---------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Synchronize rules to other nodes                  | If this option is selected, new throttling rules will be synchronized to other nodes of a given instance.                                                                                                                                                                                     |
      +---------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Setting the validity period for a throttling rule | The validity period of a rule is the specific timeframe during which the rule is in effect.                                                                                                                                                                                                   |
      |                                                   |                                                                                                                                                                                                                                                                                               |
      |                                                   | -  **Permanent**: The new SQL throttling rule takes effect permanently.                                                                                                                                                                                                                       |
      |                                                   |                                                                                                                                                                                                                                                                                               |
      |                                                   | -  **Limited**: You need to specify the expiration time for the SQL throttling rule. The validity period starts when the request to add the rule is submitted. The expiration time may be delayed for a maximum of 1 minute.                                                                  |
      |                                                   |                                                                                                                                                                                                                                                                                               |
      |                                                   |    The expiration time can be a maximum of two weeks later than the current time.                                                                                                                                                                                                             |
      |                                                   |                                                                                                                                                                                                                                                                                               |
      |                                                   |    You can click **Historical SQL Throttling Rules** on the right to view the expired SQL throttling rules.                                                                                                                                                                                   |
      +---------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Confirm the settings and click **OK**.
#. In the displayed dialog box, click **OK**.

Deleting a Throttling Rule
--------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select a region and project.

#. Click |image4| in the upper left corner of the page and choose **Databases** > **TaurusDB**.

#. On the **Instances** page, click the instance name.

#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.

#. Click **SQL Explorer** and then **SQL Throttling**.

#. Locate a SQL throttling rule and click **Delete** in the **Operation** column.

   Alternatively, select one or more throttling rules and click **Delete** above the list.

#. In the displayed dialog box, confirm the throttling rules to be deleted. If you select **Synchronize rules to other nodes**, the throttling rules of other nodes of a given instance will also be deleted. Click **OK**.

#. (Optional) Click **Historical SQL Throttling Rules** to view the deleted and expired throttling rules.

.. |image1| image:: /_static/images/en-us_image_0000002518409421.png
.. |image2| image:: /_static/images/en-us_image_0000002486209558.png
.. |image3| image:: /_static/images/en-us_image_0000002518409421.png
.. |image4| image:: /_static/images/en-us_image_0000002486209558.png
