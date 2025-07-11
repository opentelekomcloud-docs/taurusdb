:original_name: gaussdb_03_0040.html

.. _gaussdb_03_0040:

Rebooting a DB Instance
=======================

Scenarios
---------

You may need to reboot a DB instance during maintenance. For example, after modifying some parameters, you must reboot the DB instance for the modifications to take effect. Instances cannot be rebooted when backups or read replicas are being created for them.

The time required for rebooting a DB instance depends on the crash recovery process of the DB engine. To shorten the reboot time, you are advised to reduce database activities during the reboot to reduce rollback activities of transit transactions.

.. important::

   -  Your database may be unavailable if, for example, data is being backed up or there are modifications being made.
   -  Rebooting a DB instance will cause service interruption. During this period, the DB instance status is **Rebooting**.
   -  DB instances are not available when being rebooted. After the reboot completes, the cached memory will be automatically cleared. The DB instance needs to be warmed up to prevent congestion during peak hours.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, locate the target DB instance and choose **More** > **Reboot** in the **Operation** column.

   Alternatively, click the target DB instance. On the displayed page, click **Reboot** in the upper right corner of the page.

   The read replicas are also rebooted.

#. In the displayed **Reboot DB Instance** dialog box, click **Yes**.

#. Refresh the DB instance list and view the status of the DB instance. If its status is **Available**, it has rebooted successfully.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
