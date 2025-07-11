:original_name: gaussdb_03_0063.html

.. _gaussdb_03_0063:

Restoring Data from a Backup
============================

Scenarios
---------

You can use an automated or manual backup to restore data to the status when the backup was created. The restoration is at the DB instance level.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Backups** page, select the backup to be restored and click **Restore** in the **Operation** column.

#. Click **OK**. Currently, you can only restore data to a new DB instance.

   The **Create New Instance** page is displayed.

   -  The region, DB engine and version of the new DB instance are the same as those of the original DB instance and cannot be changed.
   -  The database port is **3306** by default.
   -  Other settings are the same as those of the original DB instance by default and can be modified. For details, see :ref:`Step 1: Create a DB Instance <gaussdb_02_0004>`.

#. View the restoration results.

   A new DB instance is created using the backup data. The instance status changes from **Creating** to **Available**.

   The new DB instance is independent from the original one. If you want to offload read pressure on the primary node, create one or more read replicas for the new DB instance.

   A full backup is triggered after the new DB instance is created.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
