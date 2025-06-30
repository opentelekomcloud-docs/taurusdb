:original_name: gaussdb_05_2265.html

.. _gaussdb_05_2265:

Upgrading the Minor Version of a DB Instance
============================================

Scenarios
---------

You can manually upgrade minor versions of your instances to improve performance, add new functions, and fix bugs.

Precautions
-----------

-  The upgrade will cause the instance to reboot and interrupt services intermittently. To limit the impact of the upgrade, perform the upgrade during off-peak hours, or ensure that your applications support automatic reconnection.
-  If an instance contains a large number of table partitions (more than 1 million), it may take more than 2 hours to reboot the instance.
-  If the primary node and read replicas of an instance are deployed in the same AZ, a minor version upgrade will trigger a failover. If they are in different AZs, a minor version upgrade will trigger two failovers. A failover means that the system fails over to a read replica in case the primary node is unavailable.
-  When you upgrade a minor version of an instance, minor versions of read replicas (if any) will also be upgraded automatically. Minor versions of read replicas cannot be upgraded separately. A minor version upgrade cannot be rolled back after the upgrade is complete.
-  DDL operations, such as CREATE EVENT, DROP EVENT, and ALTER EVENT, are not allowed during a minor version upgrade.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, click the target instance to go to the **Basic Information** page.

#. In the **DB Instance Information** area, click **Upgrade** in the **DB Engine Version** field.

#. In the displayed dialog box, select a scheduled time and click **OK**.

   Upon submission: The system upgrades the minor version immediately after your submission of the upgrade request. After the operation is complete, in the **Task Center** page, click **Instant Tasks** and view the information about the upgrade task.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
